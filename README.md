## Hi there 👋 I´m Samira Fanjul

Aspiring Data Analyst | 17+ Years in Technology Consulting & Business Solutions

Transforming data into actionable insights through SQL, Python, Excel, and Power BI.
<!--
**samyfs-DA/samyfs-DA** is a ✨ _special_ ✨ repository because its `README.md` (this file) appears on your GitHub profile.-->

<img width="1683" height="653" alt="ChatGPT Image 28 abr 2026, 12_50_09 p m" src="https://github.com/user-attachments/assets/eac6b18a-c4ca-407a-93b8-25c0cb3b0373" />

  </p>

<br>

# About me

My engineering background fuels my passion for data . I translate my clients' requirements into insights and visualize them to inspire action.

I have experience working with datasets, extracting, cleaning, and shaping them. In this space, I want to share part of my journey into the fascinating world of data analytics and explain why I am passionate about it.

## Technical skills

I have experience working with  **Excel, Google Sheets, SQL,** and **Python** for data analysis and management.
I work with **Power BI** and **Tableau** to visualize and tell stories with data.

## Soft skills
- Data analytics
- Working under process
- Result-oriented
- Client-oriented
- Problem-solving
- Teamwork
- Client attention 

Please feel free to contact me. I'm sharing my LinkedIn profile and email address. 

<a href="https://linkedin.com/in/samira-fanjul" target="blank"><img align="center" src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="unsimpledev"/></a>
<a href = "mailto:samyfs@gmail.com" target="blank"><img align="center" src="https://img.shields.io/badge/Gmail-D14836?style=for-the-badge&logo=gmail&logoColor=white" alt="@unsimpledev"  /></a>

# Projects

## Sales Data Analysis in "VentaExpress".


[<img width="1280" height="720" alt="Venta Express" src="https://github.com/user-attachments/assets/f68d9127-5d92-446e-a9ee-acdfa04291b2" />
](https://github.com/samyfs-DA/ventaexpress.git)

## Financial Performance Analysis
<img width="48" height="48" src="https://img.icons8.com/fluency/48/sql.png" alt="sql"/></br>
AdventureWorks is a financial enterprise. This project involved analyzing revenue, campaigns, ROI, and ROMI.

To resolve this project, we need the following tables:
- ventas_2017: Transaction table from 2017.
- productos: Catalog with attributes, cost, and price with ClaveProducto.
- productos_categorias: Product category and subcategory.
- clientes: Location and segment.
- territorios: Continent and country.
- campanas: Marketing spend for territory/campaign.

**Key Questions**
- How much are we earning per country?
- How profitable is each market considering the marketing expenses?

**Methology**
- **Data processing**: FFirst, explore the database and check the join keys. Then, familiarize yourself with the database diagram. 
 
Some screenshots:

Code on ventas 2017:
```
SELECT
    *
FROM
    ventas_2017
LIMIT 10;
```
<img width="873" height="263" alt="image" src="https://github.com/user-attachments/assets/a7b8d75b-0f1b-4916-bdc3-bc32aa643c55" />

 
  - Second cleaning of data: this means removing null values and duplicates, then building a database for the join.
 
  Code:
```
  SELECT 
    v.numero_pedido AS numero_pedido, 
    v.clave_producto AS clave_producto, 
    p.nombre_producto AS producto, 
    pc.clave_categoria AS categoria, 
    v.cantidad_pedido AS cantidad,
    t.pais AS pais, 
    t.continente AS continente, 
    v.clave_territorio AS clave_territorio,
    COALESCE(p.precio_producto, 0) AS precio_venta,
    COALESCE(p.costo_producto, 0) AS costo
    FROM 
    ventas_2017 AS v
    LEFT JOIN productos AS p
      ON p.clave_producto = v.clave_producto
    LEFT JOIN productos_categorias AS pc
      ON p.clave_subcategoria = pc.clave_subcategoria
    LEFT JOIN territorios AS t 
      ON t.clave_territorio = v.clave_territorio;
 ```
   <img width="1070" height="397" alt="image" src="https://github.com/user-attachments/assets/174e22ae-bdf5-4964-a792-bd3790b15af5" />

  - Added two new columns to keep track of incoming and outgoing funds.
```
SELECT
    v.numero_pedido AS numero_pedido,
    v.clave_producto AS clave_producto,
    p.nombre_producto AS producto,
    pc.clave_categoria AS categoria,
    COALESCE(p.precio_producto, 0)  AS precio_producto,
    COALESCE(v.cantidad_pedido, 0)  AS cantidad_pedido,
    COALESCE(p.costo_producto, 0)   AS costo_producto,
    t.pais AS pais,
    t.continente AS continente,
    v.clave_territorio AS territorio,
    COALESCE(p.precio_producto, 0) * COALESCE(v.cantidad_pedido, 0) AS ingreso_total,
    COALESCE(p.costo_producto, 0) * COALESCE(v.cantidad_pedido, 0) AS costo_total
    FROM 
      ventas_2017 AS v
    JOIN productos AS p
      ON v.clave_producto = p.clave_producto
    LEFT JOIN productos_categorias AS pc
      ON p.clave_subcategoria = pc.clave_subcategoria
    LEFT JOIN territorios AS t
      ON v.clave_territorio = t.clave_territorio;
```
  <img width="1242" height="364" alt="image" src="https://github.com/user-attachments/assets/fcd1519a-b69e-4b12-a480-f47ae07790f6" />

  - Calculate revenue and cost per country.
    ```
    SELECT
    p.pais,
    p.clave_territorio,
    SUM(p.ingresos)::integer AS ingresos,
    SUM(p.costos)::integer AS costos,
    COALESCE(SUM(c.costo_campana), 0)::integer AS costo_campana,
    SUM(p.ingresos)::integer - SUM(p.costos)::integer AS beneficio_bruto,
        ((SUM(p.ingresos) - SUM(p.costos)) * 100.0)
        / NULLIF(SUM(p.ingresos), 0) AS margen_pct,
    ((SUM(p.ingresos) - SUM(p.costos)) * 100.0)
    / NULLIF(SUM(c.costo_campana), 0) AS roi_pct
    FROM pais_ingreso_costo AS p
    LEFT JOIN pais_campanas AS c
      ON p.clave_territorio = c.clave_territorio
    GROUP BY
      p.pais,
      p.clave_territorio
    ORDER BY
      p.clave_territorio, ingresos, costos;
    ```
  <img width="1159" height="250" alt="image" src="https://github.com/user-attachments/assets/eb21036f-ce90-49a0-aa9b-ff3c7abca72c" />

  - It is important to realize a QA. This is true for every analysis.
    ```
    SELECT 
    COUNT (*) AS productos_precio_no_valido
    FROM 
    productos
    WHERE costo_producto <= 0;
    ```
  
  <img width="348" height="93" alt="image" src="https://github.com/user-attachments/assets/eb5e5571-31bd-4130-a782-bacc66e081a4" />
  
  *This demonstrates that everything is fine, so you can proceed.*

  - The analysis is concluded with the export of results to Excel or Google Sheets for stakeholders' review. The format is comprehensive.

<img width="1872" height="680" alt="image" src="https://github.com/user-attachments/assets/89420c2a-f89a-4b52-b546-329d0ff5dd3e" />

[Proyecto 2_ Análisis financiero  SQL - Resumen ejecutivo.xlsx](https://github.com/user-attachments/files/28677833/Proyecto.2_.Analisis.financiero.SQL.-.Resumen.ejecutivo.xlsx)

## Urban Mobility Analysis and Economic Productivity
<img width="48" height="48" src="https://img.icons8.com/clouds/100/python.png" alt="python"/> <img width="42" height="42" src="https://img.icons8.com/color/48/pandas.png" alt="pandas"/> <img width="42" height="42" src="https://img.icons8.com/color/48/numpy.png" alt="numpy"/> <img width="42" height="42" src="https://img.icons8.com/color/48/matplotlib.png" alt="matplotlib"/> <img width="42" height="42" src="https://raw.githubusercontent.com/gilbarbara/logos/refs/heads/main/logos/seaborn-icon.svg"/>

