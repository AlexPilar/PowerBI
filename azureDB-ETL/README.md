
# ☁️ Transformação de dados numa DB da Azure
**Objetivo:**
O objetivo do projeto é realizar o processo de ETL em uma base de dados que está situada num banco de dados Azure (MySQL).

Os passos adotados foram: Criar o servidor e o banco de dados na Azure, inserir os dados e realizar a transformação de dados no power BI.

##  📂 Criação e inserção na Azure
  
No site da [Azure](https://azure.microsoft.com/en-us) foi criado um "Banco de Dados do Azure para MySQL" que é um servidor, cujo nome dado foi "desafio-projeto-dio-alex". A parte de inserção de dados foi feita através do MySQL Workbench sincronizado diretamente com a Azure. Esta alternativa foi escolhida pela facilidade, visto que também é possível inserir pelo próprio Cloud Shell.

Os arquivos "company-schema.sql" e "company-data.sql" permitem criar o Banco de dados fictício "azure_company" com todas as informações e restrições necessárias.

## 💱 Transformação no Power BI

Para realizar a transformação dos dados, primeiro foi necessário sincronizá-los com o servidor Azure. O próprio recurso da Microsoft permite fazer o download de um arquivo de extensão ".pbids" para abrir no powerBI e fazer a conexão.

Para a transformação foram feitos os seguintes passos:

    1. Inserção de consulta inicial para a tabela employees. Esta consulta junta
     o nome e sobrenome dos colaboradores em uma única coluna "FullName" e associou 
     com  o nome dos seus gerentes "MgnName".
        A consulta utilizada foi:
            SELECT e1.*, CONCAT(e1.Fname, " ",  e1.Minit, " ", e1.Lname) as FullName,
            CONCAT(e2.Fname, " ",  e2.Minit, " ", e2.Lname) as Mng_Name,
            d.Dname FROM employee e1
            LEFT JOIN employee e2 ON e1.Super_ssn = e2.Ssn;
    
    
    2.Verificação dos tipos de dados de cada coluna
        O valor de salário foi modificado para "Número decimal fixo"
        Os "SSN's" foram mantidos como tipo texto
        O número de horas dos projetos foi mantido como decimal para facilitar nas contas

    3. Verificação de células "nulas"
        A única célula nula é na tabela "employee". Esta informação é nula,
        pois ele é o gerente da empresa.

    4. Verificação da gerência dos departamentos
        Não há departamento nem colaborador sem gerente.

    5. Divisão da coluna "Address" em 4 novas colunas pelo separador "-":
        StNumber, StName, City, State

    6. Mescla das tabelas "employee" e "departament" para associar o nome do 
     departamento a cada colaborador. Adicionada a seguinte linha na consulta:
     LEFT JOIN departament d ON e1.Dno = d.Dnumber;


### Conecte-se comigo


LinkedIn             |  Discord | GitHub
:-------------------------:|:-------------------------:|:-------------------------:
[![LinkedIn](https://img.shields.io/badge/LinkedIn-0E76A8?style=for-the-badge&logo=linkedin&logoColor=FFFFFF)](https://www.linkedin.com/in/alex-pilar/)  |  [![Discord](https://img.shields.io/badge/Discord-9E1EA8?style=for-the-badge&logo=discord&logoColor=FFFFFF)](discordapp.com/users/alekaolindo) | [![Twitter](https://img.shields.io/badge/GitHub-000?style=for-the-badge&logo=github)](https://github.com/AlexPilar)