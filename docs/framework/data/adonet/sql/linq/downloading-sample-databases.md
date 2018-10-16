---
title: Obter os bancos de dados de exemplo para exemplos de código do ADO.NET
description: Baixe os bancos de dados de exemplo usados nos exemplos de código na documentação do ADO.NET, bem como ferramentas de gerenciamento e do SQL Server
ms.date: 10/12/2018
ms.assetid: ef9d69a1-9461-43fe-94bb-7c836754bcb5
ms.openlocfilehash: 75ae1895d683b669f51b33130fc2f47010e39814
ms.sourcegitcommit: fd8d4587cc26e53f0e27e230d6e27d828ef4306b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/16/2018
ms.locfileid: "49347488"
---
# <a name="get-the-sample-databases-for-adonet-code-samples"></a>Obter os bancos de dados de exemplo para exemplos de código do ADO.NET

Um número de exemplos e explicações passo a passo no [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] documentação usar bancos de dados de exemplo e o SQL Server Express. Você pode baixar esses produtos gratuitos da Microsoft.

## <a name="get-the-adventureworks-sample-database"></a>Obter dados de exemplo AdventureWorks

Baixe o banco de dados de exemplo AdventureWorks do repositório do GitHub a seguir:

[Bancos de dados de exemplo AdventureWorks](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks)

Depois de baixar um backup de banco de dados de (\*. bak) arquivos, restaure o backup para uma instância do SQL Server usando o SQL Server Management Studio (SSMS). Ver [obter o SQL Server Management Studio](#get_ssms).

## <a name="get-the-northwind-sample-database"></a>Obter dados de exemplo Northwind

Baixe o banco de dados de exemplo Northwind na seguinte página no Microsoft Download Center:

[Northwind e Pubs Sample Databases](https://go.microsoft.com/fwlink?linkid=64296)

Depois que o arquivo é baixado, clique duas vezes no arquivo para extrair os bancos de dados e scripts. Por padrão, os arquivos são instalados na pasta `<drive>:\SQL Server 2000 Sample Databases`.

Antes de usar o banco de dados Northwind, você deve fazer uma das seguintes ações:

- Recriar o banco de dados em uma instância do SQL Server executando o `instnwnd.sql` arquivo de script na pasta de instalação.

- Anexar a `northwnd.mdf` arquivo com correspondente `*.ldf` arquivo de log para uma instância do SQL Server.

## <a name="get_sql"></a> Obtenha o SQL Server Express

SQL Server Express é uma edição gratuita do SQL Server que pode ser redistribuído com aplicativos de nível básica. Baixe o SQL Server Express da seguinte página:
  
[Edições Express do SQL Server](https://www.microsoft.com/sql-server/sql-server-editions-express)

Se você estiver usando [Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017), SQL Server Express LocalDB está incluído na Community edition, bem como as edições Professional e superior.  

## <a name="get_ssms"></a> Obtenha o SQL Server Management Studio
Se você quiser exibir ou modificar um banco de dados que você baixou, você pode usar o SQL Server Management Studio (SSMS). Baixe o SSMS na seguinte página:

[Baixar o SQL Server Management Studio (SSMS)](/sql/ssms/download-sql-server-management-studio-ssms) 

Você também pode exibir e gerenciar bancos de dados no ambiente de desenvolvimento integrado (IDE) do Visual Studio. Na [Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017), conecte-se ao banco de dados do **Pesquisador de objetos do SQL Server**, ou criar uma Conexão de dados ao banco de dados **Gerenciador de servidores**. Abrir esses painéis explorer do **exibição** menu.
  
## <a name="see-also"></a>Consulte também

- [Introdução](../../../../../../docs/framework/data/adonet/sql/linq/getting-started.md)
