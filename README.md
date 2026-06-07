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
<img width="48" height="48" src="https://img.icons8.com/fluency/48/google-sheets--v1.png" alt="google-sheets--v1"/> <img width="48" height="48" src="https://img.icons8.com/fluency/48/ms-excel.png" alt="ms-excel"/><br>
"VentaExpress" is a growing e-commerce company. The first step in any data analysis is to clean and organize the data so that stakeholders can make informed decisions, such as identifying which city had the best sales and determining the best month in the last quarter of 2024.

**Key Questions**
- What were the total sales for the quarter?
- What was the average transaction amount?
- What was the total number of transactions?
- Which month had better sales?
- Which city had higher sales?

**Methology**
- **Data processing** involves cleaning data. This means removing null values, duplicates, and columns with incorrect forms or types. It also involves combining or splitting information.
- **Document** the challenges and changes needed.
- **To organize data**, we need to follow best practices.
- **Calculate** important metrics to inform action.
- **Visualize** the insights so they are clear when communicating with stakeholders.

**Visualizations and Results**

<img width="1187" height="734" alt="image" src="https://github.com/user-attachments/assets/cf4f3a5a-6c09-4a06-87d9-d74dfc55e1ae" />

<img width="1174" height="726" alt="image" src="https://github.com/user-attachments/assets/f92d4880-eb2c-4b5f-808b-185f319328c9" />

<img width="1305" height="1323" alt="image" src="https://github.com/user-attachments/assets/e00288a0-8839-4377-b184-ebc5867c7930" />

[Proyecto 1_ VentaExpress.xlsx](https://github.com/user-attachments/files/28676840/Proyecto.1_.VentaExpress.xlsx)

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


  - .
