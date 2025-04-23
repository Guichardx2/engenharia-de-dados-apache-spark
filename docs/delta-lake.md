# Delta Lake

```
from pyspark.sql import SparkSession #Import para sessão spark
from pyspark.sql.functions import col
from pyspark.sql.types import StructType, StructField, StringType, FloatType #Imports para estrutura e tipos

from delta import *

import logging

logging.getLogger("py4j").setLevel(logging.DEBUG)
```
#Configuração da Sessão spark
```
spark = (
    SparkSession
    .builder
    .master("local[*]")
    .config("spark.jars.packages", "io.delta:delta-spark_2.12:3.0.0")
    .config("spark.sql.extensions", "io.delta.sql.DeltaSparkSessionExtension")
    .config("spark.sql.catalog.spark_catalog", "org.apache.spark.sql.delta.catalog.DeltaCatalog")
    .getOrCreate()
)
```
# Criação da tabela cliente_delta
```
spark.sql(
     """
     CREATE TABLE IF NOT EXISTS default.clientes_delta (
         id INT NOT NULL,
         nome_cliente STRING NOT NULL,
         uf CHAR(2) NOT NULL,
         status BOOLEAN NOT NULL,
         limite_credito FLOAT NOT NULL
     ) USING delta
     """
)
```
# Realiza um select na tabela criada e faz o output

```
spark.sql(
    """
    SELECT * from default.clientes_delta
    """
).show()
```
# Criação da delta table para cliente delta
```
cliente = DeltaTable.forPath(spark, "./spark-warehouse/clientes_delta") 
```
# INSERT
```
spark.sql(
    """
        INSERT INTO default.clientes_delta VALUES 
        (1, 'Jean Guichard²', 'RS', false, 10000000.0), 
        (2, 'Lucas da Rosa', 'SC', true, 1000000.0), 
        (3, 'Matheus Daminelli', 'SC', true, 4000000.0)   
    """
)
```
# Adicionando coluna
```
spark.sql(
    """
    alter table default.clientes_delta add column cidade STRING
    """
)
```
# Update
```
spark.sql("""
    UPDATE default.clientes_delta
    SET cidade = CASE
        WHEN id = 1 THEN 'Torres'
        WHEN id = 2 THEN 'Tubarão'
        WHEN id = 3 THEN 'Criciúma'
        ELSE cidade
    END
""")
```
# Verifica se é uma delta table
```
DeltaTable.isDeltaTable(spark, "spark-warehouse/clientes_delta")
```
# Delete
```
spark.sql(
    """
        DELETE FROM default.clientes_delta
        WHERE uf = 'RS' AND status = false
    """
)
```
# Visualização dos dados
```
spark.sql(
    """
    SELECT * from default.clientes_delta
    """
).show()
cliente.toDF().show()
```