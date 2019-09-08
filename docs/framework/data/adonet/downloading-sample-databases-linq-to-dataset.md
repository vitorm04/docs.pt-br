---
title: Bases de dados de exemplo de transferência (LINQ to DataSet)
ms.date: 03/30/2017
ms.assetid: eb42a7af-d410-4b7f-b4a8-13c72ce6fd09
ms.openlocfilehash: c67ee699cf594f476a728c7345b47b0c32dea7ff
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795169"
---
# <a name="downloading-sample-databases-linq-to-dataset"></a>Bases de dados de exemplo de transferência (LINQ to DataSet)
Os exemplos e orientações na documentação do LINQ to DataSet usam o banco de dados de exemplo AdventureWorks. Você pode baixar este produto gratuitamente do site de download da Microsoft. Os exemplos e orientações na documentação do LINQ to DataSet usam SQL Server como o armazenamento de dados. O SQL Server Express edition, que está disponível sem carregamento, também pode ser usada como o armazenamento de dados em vez do SQL Server.  
  
## <a name="downloading-and-installing-the-adventureworks-database"></a>Download e instalar o base de dados AdventureWorks  
  
#### <a name="to-download-and-install-the-adventureworks-sample-database-for-sql-server"></a>Para baixar e instalar o base de dados de exemplo AdventureWorks do SQL Server  
  
1. Abra o Internet Explorer.  
  
2. Vá para o site de [exemplos do SQL Server 2005 e bancos de dados de exemplo](https://go.microsoft.com/fwlink/?linkid=31046) .  
  
3. Siga as instruções para baixar o base de dados de exemplo AdventureWorks para o tipo do processador (como AdventureWorksDB.msi), e salve o arquivo .msi para seu computador local.  
  
4. Se você tiver uma versão anterior AdventureWorks instalado de download ou durante a configuração do SQL Server, você deve remova-o antes de executar AdventureWorks.msi.  
  
#### <a name="to-remove-a-previous-download-of-an-adventureworks-sample-database"></a>Para remover um download anterior de um base de dados de exemplo AdventureWorks  
  
1. Solte o base de dados AdventureWorks ou de AdventureWorksDW.  
  
2. Em **Adicionar ou remover programas**, selecione **AdventureWorksDB** ou **AdventureWorksBI** e clique em **remover**.  
  
#### <a name="to-remove-an-adventureworks-sample-database-previously-installed-using-setup"></a>Para remover um base de dados de exemplo AdventureWorks instalado anteriormente usando a configuração  
  
1. Solte o base de dados AdventureWorks ou de AdventureWorksDW.  
  
2. Em **Adicionar ou remover programas**, selecione **Microsoft SQL Server 2005** e clique em **alterar**.  
  
3. Em **seleção de componentes**, selecione **componentes da estação de trabalho** e clique em **Avançar**.  
  
4. Em **Bem-vindo ao assistente de instalação do SQL Server**, clique em **Avançar**.  
  
5. Em **verificação de configuração do sistema**, clique em **Avançar**.  
  
6. Em **alterar ou remover instância**, clique em **alterar componentes instalados**.  
  
7. Na **seleção de recursos**, expanda o nó **documentação, exemplos e bancos de dados de exemplo** .  
  
8. Selecione **código e aplicativos de exemplo**. Expanda bancos de dados de **exemplo**, selecione o banco de dados de exemplo a ser removido e selecione o **recurso inteiro estará indisponível**. Clique em **Avançar**.  
  
9. Clique em **instalar** e conclua o assistente de instalação.  
  
#### <a name="to-attach-the-adventureworks-sample-database-files-to-an-instance-of-sql-server"></a>Para anexar arquivos de base de dados de exemplo AdventureWorks a uma instância de SQL Server  
  
1. Depois que o arquivo do instalador do banco de dados de exemplo de arquivo for baixado, clique duas vezes no arquivo **AdventureWorksDB. msi** (ou no arquivo que você baixou) para instalar o banco de dados. Por padrão, o base de dados é instalado em c:\Program Files\Microsoft SQL Server \ MSSQL.1 \ MSSQL \ dados.  
  
2. Anexar arquivos de base de dados AdventureWorks a uma instância do SQL Server executando o seguinte script SQLCMD ou o SQL Server Management Studio:  
  
    ```sql
    exec sp_attach_db @dbname=N'AdventureWorks', @filename1=N'C:\Program Files\Microsoft SQL Server\MSSQL.1\MSSQL\Data\AdventureWorks_Data.mdf', @filename2=N'C:\Program Files\Microsoft SQL Server\MSSQL.1\MSSQL\Data\AdventureWorks_log.ldf'  
    ```  
  
     Se você instalar esses arquivos a uma unidade ou para um diretório diferente, você deve revisar os caminhos corretamente antes de executar o procedimento armazenado `sp_attach_db` .  
  
## <a name="downloading-sql-server-express-edition"></a>Baixando o SQL Server Express Edition  
 Os exemplos e orientações na seção LINQ to DataSet usam SQL Server 2005 como o armazenamento de dados, mas podem ser modificados para usar a edição do SQL Server Express, em vez disso. O SQL Server Express Edition está disponível gratuitamente, e você pode redistribuí-lo com os aplicativos. Se você estiver usando o Visual Studio, o SQL Server Express Edition estará incluído nas edições Pro e superior.  
  
#### <a name="to-download-and-install-sql-server-express-edition"></a>Para baixar e instalar o SQL Server Express Edition  
  
1. Inicie o Internet Explorer.  
  
2. Vá para a página de download do [Microsoft SQL Server 2005 Express Edition](https://go.microsoft.com/fwlink/?LinkID=31070) .  
  
3. Siga as instruções de instalação no site.  
  
## <a name="see-also"></a>Consulte também

- [Introdução](getting-started-linq-to-dataset.md)
