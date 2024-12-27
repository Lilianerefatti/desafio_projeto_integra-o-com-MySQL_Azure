# desafio_projeto_integra-o-com-MySQL_Azure
Desafio de Projeto_ Criando um Dashboard corporativo com integração com MySQL e Azure
Relatório de Análise de Dados – azure_company (Desafio de projeto DIO)

Criação de uma Instância na Azure para MySQL
•	Criei uma instância de banco de dados MySQL na plataforma Azure. Para isso, acessei o portal da Azure, criei um novo recurso e selecione "Banco de Dados MySQL". Configurei as opções básicas como nome do servidor, região, e credenciais de administrador, e depois provisionar a instância.
Criar o Banco de Dados com Base Disponível no GitHub
•	Após configurar a instância do MySQL, criei o banco de dados usando as tabelas e dados fornecidos no GitHub. Para isso, clonei ou baixe os scripts SQL do repositório GitHub e executei-os na instância do MySQL para criar as tabelas e popular o banco de dados com os dados.
Integração do Power BI com MySQL no Azure
•	Para conectar o Power BI ao banco de dados MySQL hospedado no Azure, abri o Power BI Desktop e selecione a opção "Obter Dados" > "MySQL". Inseri as credenciais de acesso e o nome do servidor, além de garantir que a instância do MySQL esteja acessível remotamente (permitir IPs ou configurar as regras de firewall no Azure). Em seguida, conectei-me e importei as tabelas desejadas.
Verificar Problemas na Base a Fim de Realizar a Transformação dos Dados
•	Analisi a base de dados para verificar inconsistências ou problemas, como valores nulos, dados errados ou mal formatados. Utilize o Power BI ou ferramentas SQL para identificar esses problemas. Após identificar as falhas, planejei e executei as transformações de dados necessárias, como alteração de tipos de dados, limpeza de dados nulos e correção de formatos.


Este relatório visa analisar os dados da empresa, com foco nas tabelas de funcionários, departamentos, projetos e trabalhos realizados. A análise inclui transformações de dados no Power BI usando o Power Query Editor, com o objetivo de responder a uma série de questões sobre os dados.
Estrutura do Relatório
1.	Verificação de Cabeçalhos e Tipos de Dados
2.	Modificação de Valores Monetários para Tipo Double Preciso
3.	Verificação de Nulos e Análise de Remoção
4.	Verificação de Funcionários sem Gerente
5.	Verificação de Departamentos sem Gerente
6.	Preenchimento de Lacunas de Departamentos sem Gerente
7.	Verificação das Horas Trabalhadas nos Projetos
8.	Separação de Colunas Complexas
9.	Mesclagem de Tabelas: Employee e Department
10.	Eliminação de Colunas Desnecessárias
11.	Junção de Colaboradores com Nomes de Gerentes
12.	Mesclagem de Colunas de Nome e Sobrenome
13.	Mesclagem de Nomes de Departamentos e Localizações
14.	Explicação sobre Mesclagem e Atribuição
15.	Agrupamento de Dados por Gerente
16.	Eliminação de Colunas Desnecessárias
________________________________________
1. Verifique os Cabeçalhos e Tipos de Dados
•	Ação: Verificamos que os cabeçalhos estavam corretos e fizemos a alteração dos tipos de dados onde necessário. As colunas de valores monetários foram convertidas para double para garantir precisão.
________________________________________
2. Modifique os Valores Monetários para Tipo Double Preciso
•	Ação: As colunas Salary na tabela employee e Hours na tabela works_on foram convertidas para o tipo double para garantir precisão nas análises financeiras e de tempo.
________________________________________
3. Verifique a Existência dos Nulos e Analise a Remoção
•	Ação: Identificamos e removemos valores nulos nas colunas essenciais. Nos casos de valores nulos em Super_ssn (gerente) e Mgr_ssn (gerente de departamento), analisamos a possibilidade de preencher esses campos com dados de gerentes válidos.
________________________________________
4. Os Employees com Nulos em Super_ssn Podem Ser os Gerentes
•	Ação: Encontramos colaboradores com valores nulos em Super_ssn e consideramos esses colaboradores como possíveis gerentes. Validamos e registramos os dados conforme necessário.
________________________________________
5. Verifique se Há Algum Departamento Sem Gerente
•	Ação: Analisamos se algum departamento não possui um gerente, ou seja, se Mgr_ssn está nulo. Preenchemos essas lacunas com o SSN de gerentes existentes.
________________________________________
6. Se Houver Departamento Sem Gerente, Preencha as Lacunas
•	Ação: Preenchemos os departamentos que estavam sem gerente com os dados de gerentes existentes, conforme a necessidade.
________________________________________
7. Verifique o Número de Horas dos Projetos
•	Ação: Calculamos o total de horas de trabalho de cada projeto agrupando os dados pela coluna Pno e somando as Hours correspondentes.
________________________________________
8. Separação de Colunas Complexas
•	Ação: Separamos a coluna Address da tabela employee em partes distintas (Rua, Cidade, Estado) para melhor análise e visualização.
________________________________________
9. Mesclagem de Consultas: Employee e Department
•	Ação: Realizamos uma junção das tabelas employee e departament para associar os colaboradores aos departamentos. Utilizamos a chave Dno para mesclar essas tabelas, garantindo que todos os colaboradores tivessem seus departamentos associados.
________________________________________
10. Eliminação de Colunas Desnecessárias
•	Ação: Após a junção e transformação dos dados, eliminamos colunas que não eram necessárias para o relatório final, mantendo apenas os dados relevantes.
________________________________________
11. Realize a Junção dos Colaboradores e Respectivos Nomes dos Gerentes
•	Ação: Realizamos uma junção interna entre a tabela employee e ela mesma para associar os colaboradores aos seus gerentes. Utilizamos a coluna Super_ssn como chave de junção.
________________________________________
12. Mescle as Colunas de Nome e Sobrenome
•	Ação: Criamos uma nova coluna Full_Name que mescla as colunas Fname e Lname, facilitando a visualização dos nomes completos dos colaboradores.
________________________________________
13. Mescle os Nomes de Departamentos e Localizações
•	Ação: Criamos uma coluna Department_Location que combina os nomes de Dname e Location, para representar a localização de cada departamento de forma única.
________________________________________
14. Explicação sobre Mesclagem e Atribuição
•	Mesclar é usado porque você está combinando dados de duas tabelas diferentes de forma lógica e eficiente, criando uma nova coluna ou tabela. Isso permite manter a integridade dos dados e possibilitar a atualização automática conforme os dados das tabelas originais mudam.
•	Atribuir seria útil se você estivesse simplesmente substituindo ou alterando valores dentro de uma coluna de dados existente, mas não permite combinar dados de fontes diferentes de maneira eficiente e escalável.
________________________________________
15. Agrupe os Dados para Saber Quantos Colaboradores Existem por Gerente
•	Ação: Agrupamos os colaboradores pela coluna Super_ssn (gerente) e calculamos o número de colaboradores por gerente. Isso nos permite entender a carga de trabalho de cada gerente.
________________________________________
16. Elimine as Colunas Desnecessárias
•	Ação: Removemos colunas desnecessárias de cada tabela que não eram necessárias para o relatório final, deixando apenas as informações pertinentes.
________________________________________
Conclusão
O processo de transformação de dados foi realizado com sucesso, atendendo a todos os requisitos mencionados. As junções, modificações de tipos de dados, e a remoção de nulos garantiram que os dados fossem preparados adequadamente para análise. O relatório final pode ser utilizado para uma visão geral da empresa, incluindo informações sobre colaboradores, departamentos, gerentes e horas trabalhadas em projetos.
