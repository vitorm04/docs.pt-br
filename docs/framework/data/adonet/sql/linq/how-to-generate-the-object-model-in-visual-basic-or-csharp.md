---
title: Como gerar o modelo de objeto em Visual Basic ou C#
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a0c73b33-5650-420c-b9dc-f49310c201ee
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 6ff5a314fb4264f57f1db3e8475a2e3105897f19
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-generate-the-object-model-in-visual-basic-or-c"></a>Como gerar o modelo de objeto em Visual Basic ou C# #
No [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], um modelo de objeto em sua própria linguagem de programação é mapeado para um banco de dados relacional. Duas ferramentas estão disponíveis para gerar automaticamente um [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] ou c# modelo de metadados do banco de dados existente.  
  
-   Se você estiver usando o [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)], poderá usar o [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] para gerar um modelo de objeto. O [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] fornece uma interface de usuário avançada para ajudá-lo a gerar um [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] modelo de objeto. Para obter mais informações, consulte [Linq to SQL Tools no Visual Studio](https://docs.microsoft.com/en-us/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).
  
-   A ferramenta de linha de comando SQLMetal. Para obter mais informações, consulte [SqlMetal.exe (ferramenta de geração de código)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).  
  
    > [!NOTE]
    >  Se você não tiver um banco de dados existente e não quiser criar um a partir de um modelo de objeto, poderá criar seu modelo de objeto usando o editor de códigos e <xref:System.Data.Linq.DataContext.CreateDatabase%2A>. Para obter mais informações, consulte [como: criar dinamicamente um banco de dados](../../../../../../docs/framework/data/adonet/sql/linq/how-to-dynamically-create-a-database.md).  
  
 Documentação para o [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] fornece exemplos de como gerar um [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] ou modelo de objeto c# usando o [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)]. As informações a seguir fornecem exemplos de como usar a ferramenta de linha de comando SQLMetal. Para obter mais informações, consulte [SqlMetal.exe (ferramenta de geração de código)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).  
  
## <a name="example"></a>Exemplo  
 A linha de comando SQLMetal mostrada no exemplo a seguir gera código [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] como o modelo de objeto baseado em atributos do banco de dados de exemplo Northwind. Os procedimentos armazenados e funções são renderizados também.  
  
```  
sqlmetal /code:northwind.vb /language:vb "c:\northwnd.mdf" /sprocs /functions  
```  
  
## <a name="example"></a>Exemplo  
 A linha de comando SQLMetal mostrada no exemplo a seguir gera código C# como o modelo de objeto baseado em atributos de banco de dados de exemplo Northwind. Os procedimentos armazenados e funções também são processados, e os nomes de tabela são automaticamente pluralizados.  
  
```  
sqlmetal /code:northwind.cs /language:csharp "c:\northwnd.mdf" /sprocs /functions /pluralize  
```  
  
## <a name="see-also"></a>Consulte também  
 [Guia de Programação](../../../../../../docs/framework/data/adonet/sql/linq/programming-guide.md)  
 [O LINQ no modelo de objeto do SQL](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)  
 [Aprendendo com explicações passo a passo](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)  
 [Como: Personalizar Classes de entidade usando o Editor de código](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)  
 [Mapeamento de atributo](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md)  
 [SqlMetal.exe (Ferramenta de Geração de Código)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md)  
 [Mapeamento Externo](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md)  
 [Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md) (Baixando bancos de dados de amostra)  
 [Criando o modelo de objeto](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)
