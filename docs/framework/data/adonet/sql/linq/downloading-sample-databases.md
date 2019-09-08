---
title: Obter os bancos de dados de exemplo SQL Server para exemplos de código ADO.NET
description: Baixe os bancos de dados de SQL Server de exemplo usados nos exemplos de código na documentação do ADO.NET, bem como SQL Server e ferramentas de gerenciamento
ms.date: 01/11/2019
ms.assetid: ef9d69a1-9461-43fe-94bb-7c836754bcb5
ms.openlocfilehash: 60566041ff4f99e96c9aee052dbcc17b5e5da9e5
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794034"
---
# <a name="get-the-sample-databases-for-adonet-code-samples"></a>Obter os bancos de dados de exemplo para exemplos de código do ADO.NET

Vários exemplos e orientações na [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] documentação usam bancos de dados de exemplo SQL Server e SQL Server Express. Você pode baixar esses produtos gratuitamente da Microsoft.

## <a name="get-the-northwind-sample-database-for-sql-server"></a>Obtenha o banco de dados de exemplo Northwind para SQL Server

Baixe o script `instnwnd.sql` do repositório GitHub a seguir para criar e carregar o banco de dados de exemplo Northwind para SQL Server:

[Bancos de dados de exemplo Northwind e pubs para Microsoft SQL Server](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/northwind-pubs)

Para poder usar o banco de dados Northwind, você precisa executar o arquivo `instnwnd.sql` de script baixado para recriar o banco de dados em uma instância do SQL Server usando [SQL Server Management Studio](#get_ssms) ou uma ferramenta semelhante. Siga as instruções no arquivo Leiame no repositório.

> [!TIP]
> Se você estiver procurando o banco de dados Northwind para Microsoft Access, consulte [instalar o banco de dados de exemplo Northwind para o Microsoft Access](#northwind_access).

## <a name="northwind_access"></a>Obter o banco de dados de exemplo Northwind para o Microsoft Access

O banco de dados de exemplo Northwind do Microsoft Access não está disponível no centro de download da Microsoft. Para instalar o Northwind diretamente de dentro do Access, faça o seguinte:

1. Abra o Access.

1. Digite **Northwind** na caixa **Pesquisar modelos online** e selecione **Enter**.

1. Na tela de resultados, selecione **Northwind**. Uma nova janela é aberta com uma descrição do banco de dados Northwind.

1. Na nova janela, na caixa de texto **nome do arquivo** , forneça um nome de arquivo para a cópia do banco de dados Northwind.

1. Selecione **Criar**. O Access baixa o banco de dados Northwind e prepara o arquivo.

1. Quando esse processo for concluído, o banco de dados será aberto com uma tela de boas-vindas.

## <a name="get-the-adventureworks-sample-database-for-sql-server"></a>Obtenha o banco de dados de exemplo AdventureWorks para SQL Server

Baixe o banco de dados de exemplo AdventureWorks para SQL Server do seguinte repositório GitHub:

[Bancos de dados de exemplo AdventureWorks](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks)

Depois de baixar um dos arquivos de backup do\*banco de dados (. bak), restaure o backup para uma instância do SQL Server usando o SQL Server Management Studio (SSMS). Consulte [obter SQL Server Management Studio](#get_ssms).

## <a name="get_ssms"></a>Obter SQL Server Management Studio
Se desejar exibir ou modificar um banco de dados que você baixou, você poderá usar o SQL Server Management Studio (SSMS). Baixe o SSMS da seguinte página:

[Baixar SQL Server Management Studio (SSMS)](/sql/ssms/download-sql-server-management-studio-ssms) 

Você também pode exibir e gerenciar bancos de dados no IDE (ambiente de desenvolvimento integrado) do Visual Studio. No [Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017), conecte-se ao banco de dados do **pesquisador de objetos do SQL Server**ou crie uma conexão com o banco de dado no **Gerenciador de servidores**. Abra esses painéis do Explorer no menu **Exibir** .

## <a name="get_sql"></a>Obter SQL Server Express

SQL Server Express é uma edição gratuita de nível de entrada do SQL Server que você pode redistribuir com aplicativos. Baixe SQL Server Express da seguinte página:
  
[Edição do SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express)

Se você estiver usando o [Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017), o SQL Server Express LocalDB será incluído na edição gratuita da Comunidade do Visual Studio, bem como nas edições Professional e superior.  

## <a name="see-also"></a>Consulte também

- [Introdução](getting-started.md)
