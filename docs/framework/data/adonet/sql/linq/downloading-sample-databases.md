---
title: Obter os bancos de dados do SQL Server de exemplo para exemplos de código do ADO.NET
description: Baixe os bancos de dados do exemplo do SQL Server usados nos exemplos de código na documentação do ADO.NET, bem como ferramentas de gerenciamento e do SQL Server
ms.date: 10/18/2018
ms.assetid: ef9d69a1-9461-43fe-94bb-7c836754bcb5
ms.openlocfilehash: 8ab65f992c9cf2b65271a237fa06eb96e358ae6a
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53153482"
---
# <a name="get-the-sample-databases-for-adonet-code-samples"></a>Obter os bancos de dados de exemplo para exemplos de código do ADO.NET

Um número de exemplos e explicações passo a passo no [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] documentação usar bancos de dados do SQL Server e SQL Server Express. Você pode baixar esses produtos gratuitos da Microsoft.

## <a name="get-the-northwind-sample-database-for-sql-server"></a>Obter dados de exemplo Northwind para SQL Server

Baixe o script `instnwnd.sql` do repositório do GitHub para criar e carregar dados de exemplo Northwind do SQL Server:

[Bancos de dados de exemplo do Northwind e pubs para o Microsoft SQL Server](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/northwind-pubs)

Antes de usar o banco de dados Northwind, você precisa executar o baixado `instnwnd.sql` arquivo de script para recriar o banco de dados em uma instância do SQL Server usando [SQL Server Management Studio](#get_ssms) ou uma ferramenta semelhante. Siga as instruções no arquivo Leiame no repositório.

> [!TIP]
> Se você estiver procurando por banco de dados Northwind do Microsoft Access, consulte [instalar o banco de dados de exemplo Northwind para o Microsoft Access](#northwind_access).

## <a name="get-the-adventureworks-sample-database-for-sql-server"></a>Obter dados de exemplo AdventureWorks para SQL Server

Baixe o banco de dados de exemplo AdventureWorks para SQL Server do repositório do GitHub a seguir:

[Bancos de dados de exemplo AdventureWorks](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks)

Depois de baixar um backup de banco de dados de (\*. bak) arquivos, restaure o backup para uma instância do SQL Server usando o SQL Server Management Studio (SSMS). Ver [obter o SQL Server Management Studio](#get_ssms).

## <a name="get_sql"></a> Obtenha o SQL Server Express

SQL Server Express é uma edição gratuita do SQL Server que pode ser redistribuído com aplicativos de nível básica. Baixe o SQL Server Express da seguinte página:
  
[SQL Server Express Edition](https://www.microsoft.com/sql-server/sql-server-editions-express)

Se você estiver usando [Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017), SQL Server Express LocalDB está incluído na Community edition gratuita do Visual Studio, bem como as edições Professional e superior.  

## <a name="get_ssms"></a> Obtenha o SQL Server Management Studio
Se você quiser exibir ou modificar um banco de dados que você baixou, você pode usar o SQL Server Management Studio (SSMS). Baixe o SSMS na seguinte página:

[Baixar o SQL Server Management Studio (SSMS)](/sql/ssms/download-sql-server-management-studio-ssms) 

Você também pode exibir e gerenciar bancos de dados no ambiente de desenvolvimento integrado (IDE) do Visual Studio. Na [Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017), conecte-se ao banco de dados do **Pesquisador de objetos do SQL Server**, ou criar uma Conexão de dados ao banco de dados **Gerenciador de servidores**. Abrir esses painéis explorer do **exibição** menu.

## <a name="northwind_access"></a> Instalar o banco de dados de exemplo Northwind do Microsoft Access

O banco de dados de exemplo Northwind para o Microsoft Access não está disponível no Microsoft Download Center. Para instalar o Northwind diretamente de dentro do Access, faça o seguinte:

1. Abra o Access.

1. ENTER **Northwind** na **pesquisar modelos Online** caixa e, em seguida, selecione **Enter**.

1. Na tela de resultados, selecione **Northwind**. Uma nova janela é aberta com uma descrição do banco de dados Northwind.

1. Na nova janela, na **nome do arquivo** texto caixa, forneça um nome de arquivo de sua cópia do banco de dados Northwind.

1. Selecione **Criar**. Acesso downloads para o banco de dados Northwind e prepara o arquivo.

1. Quando esse processo for concluído, o banco de dados é aberta com uma tela de boas-vindas.

## <a name="see-also"></a>Consulte também

- [Introdução](../../../../../../docs/framework/data/adonet/sql/linq/getting-started.md)
