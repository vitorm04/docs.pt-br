---
title: "Bases de dados de exemplo de transferência (LINQ to DataSet)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: eb42a7af-d410-4b7f-b4a8-13c72ce6fd09
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: b984fdef7f7f43e266ec4ba42b04990aced159c6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="downloading-sample-databases-linq-to-dataset"></a>Bases de dados de exemplo de transferência (LINQ to DataSet)
Os exemplos e explicações passo a passo no [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] documentação usam o banco de dados de exemplo AdventureWorks. Você pode baixar este produto gratuitamente no site de download da Microsoft. Os exemplos e explicações passo a passo no [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] documentação use SQL Server como repositório de dados. O SQL Server Express edition, que está disponível sem carregamento, também pode ser usada como o armazenamento de dados em vez do SQL Server.  
  
## <a name="downloading-and-installing-the-adventureworks-database"></a>Download e instalar o base de dados AdventureWorks  
  
#### <a name="to-download-and-install-the-adventureworks-sample-database-for-sql-server"></a>Para baixar e instalar o base de dados de exemplo AdventureWorks do SQL Server  
  
1.  Abra o Internet Explorer.  
  
2.  Vá para o [exemplos do SQL Server 2005 e bancos de dados de exemplo](http://go.microsoft.com/fwlink/?linkid=31046) site da Web.  
  
3.  Siga as instruções para baixar o base de dados de exemplo AdventureWorks para o tipo do processador (como AdventureWorksDB.msi), e salve o arquivo .msi para seu computador local.  
  
4.  Se você tiver uma versão anterior AdventureWorks instalado de download ou durante a configuração do SQL Server, você deve remova-o antes de executar AdventureWorks.msi.  
  
#### <a name="to-remove-a-previous-download-of-an-adventureworks-sample-database"></a>Para remover um download anterior de um base de dados de exemplo AdventureWorks  
  
1.  Solte o base de dados AdventureWorks ou de AdventureWorksDW.  
  
2.  De **adicionar ou remover programas**, selecione **AdventureWorksDB** ou **AdventureWorksBI** e clique em **remover**.  
  
#### <a name="to-remove-an-adventureworks-sample-database-previously-installed-using-setup"></a>Para remover um base de dados de exemplo AdventureWorks instalado anteriormente usando a configuração  
  
1.  Solte o base de dados AdventureWorks ou de AdventureWorksDW.  
  
2.  De **adicionar ou remover programas**, selecione **Microsoft SQL Server 2005** e clique em **alteração**.  
  
3.  De **seleção de componente**, selecione **componentes de estação de trabalho** e, em seguida, clique em **próximo**.  
  
4.  De **bem-vindo ao Assistente de instalação do SQL Server**, clique em **próximo**.  
  
5.  De **verificação da configuração do sistema**, clique em **próximo**.  
  
6.  De **alterar ou remover instância**, clique em **alterar componentes instalados**.  
  
7.  De **seleção de recursos**, expanda o **documentação, exemplos e bancos de dados de exemplo** nó.  
  
8.  Selecione **código de exemplo e aplicativos**. Expanda **bancos de dados de exemplo**, selecione o banco de dados de exemplo a ser removido e selecione **recurso inteiro estará indisponível**. Clique em **Avançar**.  
  
9. Clique em **instalar** e conclua o Assistente de instalação.  
  
#### <a name="to-attach-the-adventureworks-sample-database-files-to-an-instance-of-sql-server"></a>Para anexar arquivos de base de dados de exemplo AdventureWorks a uma instância de SQL Server  
  
1.  Depois que tiver baixado o arquivo de instalador de banco de dados de exemplo de arquivo, clique duas vezes o **AdventureWorksDB.msi** arquivo (ou o arquivo baixado) para instalar o banco de dados. Por padrão, o base de dados é instalado em c:\Program Files\Microsoft SQL Server \ MSSQL.1 \ MSSQL \ dados.  
  
2.  Anexar arquivos de base de dados AdventureWorks a uma instância do SQL Server executando o seguinte script SQLCMD ou o SQL Server Management Studio:  
  
    ```  
    exec sp_attach_db @dbname=N'AdventureWorks', @filename1=N'C:\Program Files\Microsoft SQL Server\MSSQL.1\MSSQL\Data\AdventureWorks_Data.mdf', @filename2=N'C:\Program Files\Microsoft SQL Server\MSSQL.1\MSSQL\Data\AdventureWorks_log.ldf'  
    ```  
  
     Se você instalar esses arquivos a uma unidade ou para um diretório diferente, você deve revisar os caminhos corretamente antes de executar o procedimento armazenado `sp_attach_db` .  
  
## <a name="downloading-sql-server-express-edition"></a>Baixando o SQL Server Express Edition  
 Os exemplos e explicações passo a passo no [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] seção usar o SQL Server 2005 como o repositório de dados, mas pode ser modificado para usar o SQL Server Express Edition. O SQL Server Express Edition está disponível gratuitamente, e você pode redistribuí-lo com os aplicativos. Se você estiver usando [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)], o SQL Server Express edition está incluída nas edições e para acima.  
  
#### <a name="to-download-and-install-sql-server-express-edition"></a>Para baixar e instalar o SQL Server Express Edition  
  
1.  Inicie o Internet Explorer.  
  
2.  Vá para o [Microsoft SQL Server 2005 Express Edition](http://go.microsoft.com/fwlink/?LinkID=31070) página de download.  
  
3.  Siga as instruções de instalação no site.  
  
## <a name="see-also"></a>Consulte também  
 [Introdução](../../../../docs/framework/data/adonet/getting-started-linq-to-dataset.md)
