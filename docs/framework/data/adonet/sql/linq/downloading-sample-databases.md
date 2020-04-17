---
title: Obtenha os bancos de dados sql server de amostra para amostras de código ADO.NET
description: Baixe os bancos de dados sql server de amostra usados nas amostras de código na documentação ADO.NET, bem como sql server e ferramentas de gerenciamento
ms.date: 01/11/2019
ms.assetid: ef9d69a1-9461-43fe-94bb-7c836754bcb5
ms.openlocfilehash: 3449f502834f449f5023bd52457d45ffaf9b0fa1
ms.sourcegitcommit: d9470d8b2278b33108332c05224d86049cb9484b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/17/2020
ms.locfileid: "81607978"
---
# <a name="get-the-sample-databases-for-adonet-code-samples"></a>Obtenha os bancos de dados de amostras para amostras de código ADO.NET

Uma série de exemplos e passo [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] a passo na documentação usam bancos de dados SQL Server de amostra e SQL Server Express. Você pode baixar esses produtos gratuitamente da Microsoft.

## <a name="get-the-northwind-sample-database-for-sql-server"></a>Obtenha o banco de dados de amostra do Northwind para SQL Server

Baixe o `instnwnd.sql` script do seguinte repositório do GitHub para criar e carregar o banco de dados de amostra do Northwind para o SQL Server:

[Northwind e pubs mostram bancos de dados para Microsoft SQL Server](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/northwind-pubs)

Antes de usar o banco de dados Northwind, você tem que executar o arquivo de script baixado `instnwnd.sql` para recriar o banco de dados em uma instância do SQL Server usando o [SQL Server Management Studio](#get_ssms) ou uma ferramenta semelhante. Siga as instruções no arquivo Readme no repositório.

> [!TIP]
> Se você estiver procurando o banco de dados Northwind para o Microsoft Access, consulte [Instalar o banco de dados de amostras do Northwind para o Microsoft Access](#northwind_access).

## <a name="get-the-northwind-sample-database-for-microsoft-access"></a><a name="northwind_access"></a>Obtenha o banco de dados de exemplo do Northwind para o Microsoft Access

O banco de dados de exemplo northwind para O Microsoft Access não está disponível no Microsoft Download Center. Para instalar o Northwind diretamente do Access, faça as seguintes coisas:

1. Acesso Aberto.

1. Digite **Northwind** na caixa **Pesquisar modelos online** e, em seguida, selecione **Enter**.

1. Na tela de resultados, selecione **Northwind**. Uma nova janela se abre com uma descrição do banco de dados Northwind.

1. Na nova janela, na caixa de texto **Nome do arquivo,** forneça um nome de arquivo para sua cópia do banco de dados Northwind.

1. Selecione **Criar**. O Access baixa o banco de dados northwind e prepara o arquivo.

1. Quando esse processo estiver concluído, o banco de dados será aberto com uma tela de boas-vindas.

## <a name="get-the-adventureworks-sample-database-for-sql-server"></a>Obtenha o banco de dados de exemplo AdventureWorks para SQL Server

Baixe o banco de dados de exemplo AdventureWorks para SQL Server no seguinte repositório do GitHub:

[Bancos de dados de exemplo do AdventureWorks](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks)

Depois de baixar um dos\*arquivos de backup do banco de dados (.bak), restaure o backup em uma instância do SQL Server usando o SQL Server Management Studio (SSMS). Consulte [get SQL Server Management Studio](#get_ssms).

## <a name="get-sql-server-management-studio"></a><a name="get_ssms"></a>Obtenha o SQL Server Management Studio
Se você quiser visualizar ou modificar um banco de dados que você baixou, você pode usar o SQL Server Management Studio (SSMS). Baixe SSMS na seguinte página:

[Baixar o SQL Server Management Studio (SSMS)](/sql/ssms/download-sql-server-management-studio-ssms)

Você também pode visualizar e gerenciar bancos de dados no ambiente de desenvolvimento integrado (IDE) do Visual Studio. No [Visual Studio,](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019)conecte-se ao banco de dados do **SQL Server Object Explorer**ou crie uma conexão de dados com o banco de dados no Server **Explorer**. Abra esses painéis de explorador no menu **Ver.**

## <a name="get-sql-server-express"></a><a name="get_sql"></a>Obter SQL Server Express

SQL Server Express é uma edição gratuita e de nível básico do SQL Server que você pode redistribuir com aplicativos. Baixe SQL Server Express na seguinte página:
  
[SQL Server Express Edition](https://www.microsoft.com/sql-server/sql-server-editions-express)

Se você estiver usando [o Visual Studio,](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019)o SQL Server Express LocalDB está incluído na edição gratuita da Comunidade do Visual Studio, bem como nas edições Profissional e superior.  

## <a name="see-also"></a>Confira também

- [Introdução](getting-started.md)
