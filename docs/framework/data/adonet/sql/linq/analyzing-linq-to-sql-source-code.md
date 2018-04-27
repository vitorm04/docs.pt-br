---
title: Para analisar o código-fonte LINQ to SQL
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cba3eef8-e108-4478-b588-ad59580e133e
caps.latest.revision: 3
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: 01191e36c71b2f6ac9844f6af2d57b1cb3ed2573
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="analyzing-linq-to-sql-source-code"></a>Para analisar o código-fonte LINQ to SQL
Usando as seguintes etapas, você pode produzir o código-fonte de [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] de base de dados de exemplo Northwind. Você pode comparar elementos modelo de objeto com os elementos de base de dados melhor para ver como os itens diferentes são mapeados.  
  
> [!NOTE]
>  Os desenvolvedores usando o Visual Studio podem usar o [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] para produzir esse código.  
  
1.  Se você ainda não tiver o base de dados de exemplo Northwind no seu computador de desenvolvimento, você poderá baixá-lo gratuitamente. Para obter mais informações, consulte [baixando bancos de dados de exemplo](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).  
  
2.  Use a ferramenta de linha de comando SqlMetal para gerar um arquivo de origem Visual Basic ou C#. Para obter mais informações, consulte [SqlMetal.exe (ferramenta de geração de código)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md). Digitando os seguintes comandos em um prompt de comando, você pode gerar os arquivos de origem Visual Basic e C# que incluem procedimentos armazenados e funções:  
  
    -   `sqlmetal /code:northwind.vb /language:vb "c:\northwnd.mdf" /sprocs /functions /pluralize`  
  
    -   `sqlmetal /code:northwind.cs /language:csharp "c:\northwnd.mdf" /sprocs /functions /pluralize`  
  
## <a name="see-also"></a>Consulte também  
 [Referência](../../../../../../docs/framework/data/adonet/sql/linq/reference.md)  
 [Informações gerais](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
