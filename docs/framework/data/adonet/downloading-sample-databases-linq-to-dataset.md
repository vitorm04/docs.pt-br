---
title: Bases de dados de exemplo de transferência (LINQ to DataSet)
ms.date: 03/30/2017
ms.assetid: eb42a7af-d410-4b7f-b4a8-13c72ce6fd09
ms.openlocfilehash: 1ef5a5ceac6a7f819551f6221b63197786ab4f09
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59339704"
---
# <a name="downloading-sample-databases-linq-to-dataset"></a>Bases de dados de exemplo de transferência (LINQ to DataSet)
Os exemplos e explicações passo a passo no [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] documentação usam o banco de dados de exemplo AdventureWorks. Você pode baixar o produto gratuitamente do site de download da Microsoft. Os exemplos e explicações passo a passo no [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] documentação use SQL Server como o armazenamento de dados. O SQL Server Express edition, que está disponível sem carregamento, também pode ser usada como o armazenamento de dados em vez do SQL Server.  
  
## <a name="downloading-and-installing-the-adventureworks-database"></a>Download e instalar o base de dados AdventureWorks  
  
#### <a name="to-download-and-install-the-adventureworks-sample-database-for-sql-server"></a>Para baixar e instalar o base de dados de exemplo AdventureWorks do SQL Server  
  
1. Abra o Internet Explorer.  
  
2. Vá para o [SQL Server 2005 exemplos e bancos de dados de exemplo](https://go.microsoft.com/fwlink/?linkid=31046) site da Web.  
  
3. Siga as instruções para baixar o base de dados de exemplo AdventureWorks para o tipo do processador (como AdventureWorksDB.msi), e salve o arquivo .msi para seu computador local.  
  
4. Se você tiver uma versão anterior AdventureWorks instalado de download ou durante a configuração do SQL Server, você deve remova-o antes de executar AdventureWorks.msi.  
  
#### <a name="to-remove-a-previous-download-of-an-adventureworks-sample-database"></a>Para remover um download anterior de um base de dados de exemplo AdventureWorks  
  
1. Solte o base de dados AdventureWorks ou de AdventureWorksDW.  
  
2. Partir **adicionar ou remover programas**, selecione **AdventureWorksDB** ou **AdventureWorksBI** e clique em **remover**.  
  
#### <a name="to-remove-an-adventureworks-sample-database-previously-installed-using-setup"></a>Para remover um base de dados de exemplo AdventureWorks instalado anteriormente usando a configuração  
  
1. Solte o base de dados AdventureWorks ou de AdventureWorksDW.  
  
2. Partir **adicionar ou remover programas**, selecione **Microsoft SQL Server 2005** e clique em **alteração**.  
  
3. Partir **seleção de componentes**, selecione **componentes de estação de trabalho** e, em seguida, clique em **próxima**.  
  
4. Partir **bem-vindo ao Assistente de instalação do SQL Server**, clique em **próxima**.  
  
5. Partir **verificação da configuração do sistema**, clique em **próxima**.  
  
6. Partir **alterar ou remover instância**, clique em **alterar componentes instalados**.  
  
7. Partir **seleção de recursos**, expanda o **documentação, exemplos e bancos de dados de exemplo** nó.  
  
8. Selecione **código de exemplo e aplicativos**. Expandir **bancos de dados de exemplo**, selecione o banco de dados de exemplo a ser removido e selecione **recurso inteiro não estará disponível**. Clique em **Avançar**.  
  
9. Clique em **instalar** e conclua o Assistente de instalação.  
  
#### <a name="to-attach-the-adventureworks-sample-database-files-to-an-instance-of-sql-server"></a>Para anexar arquivos de base de dados de exemplo AdventureWorks a uma instância de SQL Server  
  
1. Depois que tiver baixado o arquivo de instalador de banco de dados de exemplo de arquivo, clique duas vezes o **Adventureworksdb** arquivo (ou o arquivo que você baixou) para instalar o banco de dados. Por padrão, o base de dados é instalado em c:\Program Files\Microsoft SQL Server \ MSSQL.1 \ MSSQL \ dados.  
  
2. Anexar arquivos de base de dados AdventureWorks a uma instância do SQL Server executando o seguinte script SQLCMD ou o SQL Server Management Studio:  
  
    ```sql
    exec sp_attach_db @dbname=N'AdventureWorks', @filename1=N'C:\Program Files\Microsoft SQL Server\MSSQL.1\MSSQL\Data\AdventureWorks_Data.mdf', @filename2=N'C:\Program Files\Microsoft SQL Server\MSSQL.1\MSSQL\Data\AdventureWorks_log.ldf'  
    ```  
  
     Se você instalar esses arquivos a uma unidade ou para um diretório diferente, você deve revisar os caminhos corretamente antes de executar o procedimento armazenado `sp_attach_db` .  
  
## <a name="downloading-sql-server-express-edition"></a>Baixando o SQL Server Express Edition  
 Os exemplos e explicações passo a passo no [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] seção usar o SQL Server 2005 como o armazenamento de dados, mas pode ser modificado para usar o SQL Server Express Edition, em vez disso. O SQL Server Express Edition está disponível gratuitamente, e você pode redistribuí-lo com os aplicativos. Se você estiver usando o Visual Studio, SQL Server Express Edition está incluído nas edições Pro e superior.  
  
#### <a name="to-download-and-install-sql-server-express-edition"></a>Para baixar e instalar o SQL Server Express Edition  
  
1. Inicie o Internet Explorer.  
  
2. Vá para o [Microsoft SQL Server 2005 Express Edition](https://go.microsoft.com/fwlink/?LinkID=31070) página de download.  
  
3. Siga as instruções de instalação no site.  
  
## <a name="see-also"></a>Consulte também

- [Guia de Introdução](../../../../docs/framework/data/adonet/getting-started-linq-to-dataset.md)
