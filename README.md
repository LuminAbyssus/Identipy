# Identipy
Paquete y script para el análisis de ensamblados genómicos que permite:
  - Obtencion de proteínas de ensamblados genómicos que son homólogas a una o varias proteinas query
  - Alineamiento y obtención del árbol filogenético de dichas proteinas
  - Obtención de la lista de dominios presentes en cada proteina a partir de la base de datos de Prosite

El paquete identipy puede ser usado de forma independiente pero lo más aconsejable es su uso conjunto con el script main.py 

------------------------------------------------------------------------------------------------------------------------

## Instrucciones de uso
    1. Colocar en una carpeta el paquete identipy, el script main.py y el archivo prosite.dat 
    (ftp://ftp.expasy.org/databases/prosite/prosite.dat)
    
![alt text](Imagenes_instrucciones_de_uso/im1.png)
    
    2. Introducir todos los archivos querys (1 archivo fasta por query) en un directorio (query_path)
    
    3. Introducir todos los archivos genbank de ensamblados genómicos en un directorio (database_path)
    
![alt text](Imagenes_instrucciones_de_uso/im2.png)

En este ejemplo los directorios query y database se han puesto en el mismo directorio que el paquete y el resto de archivos pero se pueden colocar en cualquier directorio.
    
    4. Ejecutar el script 

>> ¡¡IMPORTANTE!!: fundamental reemplazar el archivo 'prositedat_placeholder' del repositorio por prosite.dat (demasiado grande para cargarlo).

Ejecución del script: 
`main.py query_path database_path [evalue=num] [cov=num] [iden=num]`

    - query_path: ruta del directorio donde están contenidas todas las proteinas query 
      (una query por archivo en formato fasta)
    
    - database_path: ruta del directorio donde están contenidos todos los genbank 
      referentes a los ensamblados genómicos
    
    
    - evalue=num (opcional): num se sustituye por el numero usado como 
      umbral de evalue en blastp (e.g. evalue=0.01)

    - cov=num (opcional): num se sustituye por el % minimo de cobertura 
      de los hits (e.g. cov=70)

    - iden=num (opcional): num se sustituye por el % minimo de identidad
      de los hits (e.g. id=70)
    
 --------------------------------------------------------------------------------------------------------------------------
 ## Resultados
 La ejecución del script genera una serie de archivos de resultados en la carpeta donde se ejecuta:
 - MultifaDB.fasta: multifasta con todas las secuencias del ensamblado
  - ID_Organism_table.csv: tabla con las equivalencias entre @id y organismo
  - Result_$query$: directorio que contiene el resto de archivos para la query $query$
      - Blast_result: resultado del blastp
      - MultifaFiltered: secuencias filtradas por el blastp
      - MuscleAlign: alineamiento de muscle de las secuencias filtradas
      - MuscleTree: árbol filogenético con las secuencias filtradas
      - Domains: tablas que contienen los datos de dominios encontrados

Asimismo durante la ejecución se ofrece cierta información sobre el estado del análisis y la posibilidad de observar varios gráficos: 
    - Gráfico scatter que resume de los resultados del blast
    - Gráfico de los árboles filogenéticos obtenidos
    - Gráfico de dominios encontrados y su posición en las proteínas
  
