---
title: Obter os bancos de dados de exemplo para exemplos de código do ADO.NET
description: Baixe os bancos de dados de exemplo usados nos exemplos de código na documentação do ADO.NET, bem como ferramentas de gerenciamento e do SQL Server
ms.date: 10/18/2018
ms.assetid: ef9d69a1-9461-43fe-94bb-7c836754bcb5
ms.openlocfilehash: 9779300288135cb9332a028d547ce55a07e89471
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50188385"
---
# <a name="get-the-sample-databases-for-adonet-code-samples"></a>Obter os bancos de dados de exemplo para exemplos de código do ADO.NET

Um número de exemplos e explicações passo a passo no [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] documentação usar bancos de dados de exemplo e o SQL Server Express. Você pode baixar esses produtos gratuitos da Microsoft.

## <a name="get-the-northwind-sample-database"></a>Obter dados de exemplo Northwind

Baixe o banco de dados de exemplo Northwind na seguinte página no Microsoft Download Center:

[Northwind e Pubs Sample Databases](https://go.microsoft.com/fwlink?linkid=64296)

Depois que o arquivo é baixado, clique duas vezes no arquivo para extrair os bancos de dados e scripts. Por padrão, os arquivos são instalados na pasta `<drive>:\SQL Server 2000 Sample Databases`.

Antes de usar o banco de dados Northwind, você tem de recriar o banco de dados em uma instância do SQL Server por meio [SQL Server Management Studio](#get_ssms) ou uma ferramenta semelhante para executar o `instnwnd.sql` arquivo de script na pasta de instalação.

## <a name="get-the-adventureworks-sample-database"></a>Obter dados de exemplo AdventureWorks

Baixe o banco de dados de exemplo AdventureWorks do repositório do GitHub a seguir:

[Bancos de dados de exemplo AdventureWorks](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks)

Depois de baixar um backup de banco de dados de (\*. bak) arquivos, restaure o backup para uma instância do SQL Server usando o SQL Server Management Studio (SSMS). Ver [obter o SQL Server Management Studio](#get_ssms).

## <a name="get_sql"></a> Obtenha o SQL Server Express

SQL Server Express é uma edição gratuita do SQL Server que pode ser redistribuído com aplicativos de nível básica. Baixe o SQL Server Express da seguinte página:
  
[Edições Express do SQL Server](https://www.microsoft.com/sql-server/sql-server-editions-express)

Se você estiver usando [Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017), SQL Server Express LocalDB está incluído na Community edition gratuita, bem como as edições Professional e superior.  

## <a name="get_ssms"></a> Obtenha o SQL Server Management Studio
Se você quiser exibir ou modificar um banco de dados que você baixou, você pode usar o SQL Server Management Studio (SSMS). Baixe o SSMS na seguinte página:

[Baixar o SQL Server Management Studio (SSMS)](/sql/ssms/download-sql-server-management-studio-ssms) 

Você também pode exibir e gerenciar bancos de dados no ambiente de desenvolvimento integrado (IDE) do Visual Studio. Na [Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017), conecte-se ao banco de dados do **Pesquisador de objetos do SQL Server**, ou criar uma Conexão de dados ao banco de dados **Gerenciador de servidores**. Abrir esses painéis explorer do **exibição** menu.
  
## <a name="see-also"></a>Consulte também

- [Introdução](../../../../../../docs/framework/data/adonet/sql/linq/getting-started.md)
