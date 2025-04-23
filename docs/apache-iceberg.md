# Apache Iceberg

# Inicia a sessão spark com configurações do Iceberg
```
spark = SparkSession.builder \
  .appName("IcebergLocalDevelopment") \
  .config('spark.jars.packages', 'org.apache.iceberg:iceberg-spark-runtime-3.5_2.12:1.6.1') \
  .config("spark.sql.extensions", "org.apache.iceberg.spark.extensions.IcebergSparkSessionExtensions") \
  .config("spark.sql.catalog.local", "org.apache.iceberg.spark.SparkCatalog") \
  .config("spark.sql.catalog.local.type", "hadoop") \
  .config("spark.sql.catalog.local.warehouse", "spark-warehouse/iceberg") \
  .getOrCreate()
```
# Criação da tabela cliente_iceberg
```
spark.sql(
     """
     CREATE TABLE IF NOT EXISTS local.cliente_iceberg (
         id INT NOT NULL,
         nome_cliente STRING,
         uf CHAR(2),
         status BOOLEAN,
         limite_credito FLOAT
     ) USING iceberg
     """
)
```
# Insert
```
spark.sql("""
    INSERT INTO local.cliente_iceberg VALUES
    (1, 'Jean', 'SP', true, 5000.0),
    (2, 'Lucas', 'RJ', false, 3000.0),
    (3, 'Matheus', 'MG', true, 7000.0)
""")
```
# Update
```
spark.sql("""
    UPDATE local.cliente_iceberg
    SET limite_credito = 8000.0
    WHERE nome_cliente = 'Jean'
""")
```
# Delete
```
spark.sql("""
    DELETE FROM local.cliente_iceberg
    WHERE id = 2
""")
```
