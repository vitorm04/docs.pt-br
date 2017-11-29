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
# <a name="how-to-generate-the-object-model-in-visual-basic-or-c"></a><span data-ttu-id="eaa67-102">Como gerar o modelo de objeto em Visual Basic ou C#</span><span class="sxs-lookup"><span data-stu-id="eaa67-102">How to: Generate the Object Model in Visual Basic or C#</span></span> #
<span data-ttu-id="eaa67-103">No [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], um modelo de objeto em sua própria linguagem de programação é mapeado para um banco de dados relacional.</span><span class="sxs-lookup"><span data-stu-id="eaa67-103">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], an object model in your own programming language is mapped to a relational database.</span></span> <span data-ttu-id="eaa67-104">Duas ferramentas estão disponíveis para gerar automaticamente um [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] ou c# modelo de metadados do banco de dados existente.</span><span class="sxs-lookup"><span data-stu-id="eaa67-104">Two tools are available for automatically generating a [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] or C# model from the metadata of an existing database.</span></span>  
  
-   <span data-ttu-id="eaa67-105">Se você estiver usando o [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)], poderá usar o [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] para gerar um modelo de objeto.</span><span class="sxs-lookup"><span data-stu-id="eaa67-105">If you are using [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)], you can use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] to generate an object model.</span></span> <span data-ttu-id="eaa67-106">O [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] fornece uma interface de usuário avançada para ajudá-lo a gerar um [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] modelo de objeto.</span><span class="sxs-lookup"><span data-stu-id="eaa67-106">The [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] provides a rich user interface to help you generate a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] object model.</span></span> <span data-ttu-id="eaa67-107">Para obter mais informações, consulte [Linq to SQL Tools no Visual Studio](https://docs.microsoft.com/en-us/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).</span><span class="sxs-lookup"><span data-stu-id="eaa67-107">For more information see, [Linq to SQL Tools in Visual Studio](https://docs.microsoft.com/en-us/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).</span></span>
  
-   <span data-ttu-id="eaa67-108">A ferramenta de linha de comando SQLMetal.</span><span class="sxs-lookup"><span data-stu-id="eaa67-108">The SQLMetal command-line tool.</span></span> <span data-ttu-id="eaa67-109">Para obter mais informações, consulte [SqlMetal.exe (ferramenta de geração de código)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="eaa67-109">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="eaa67-110">Se você não tiver um banco de dados existente e não quiser criar um a partir de um modelo de objeto, poderá criar seu modelo de objeto usando o editor de códigos e <xref:System.Data.Linq.DataContext.CreateDatabase%2A>.</span><span class="sxs-lookup"><span data-stu-id="eaa67-110">If you do not have an existing database and want to create one from an object model, you can create your object model by using your code editor and <xref:System.Data.Linq.DataContext.CreateDatabase%2A>.</span></span> <span data-ttu-id="eaa67-111">Para obter mais informações, consulte [como: criar dinamicamente um banco de dados](../../../../../../docs/framework/data/adonet/sql/linq/how-to-dynamically-create-a-database.md).</span><span class="sxs-lookup"><span data-stu-id="eaa67-111">For more information, see [How to: Dynamically Create a Database](../../../../../../docs/framework/data/adonet/sql/linq/how-to-dynamically-create-a-database.md).</span></span>  
  
 <span data-ttu-id="eaa67-112">Documentação para o [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] fornece exemplos de como gerar um [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] ou modelo de objeto c# usando o [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="eaa67-112">Documentation for the [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] provides examples of how to generate a [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] or C# object model by using the [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)].</span></span> <span data-ttu-id="eaa67-113">As informações a seguir fornecem exemplos de como usar a ferramenta de linha de comando SQLMetal.</span><span class="sxs-lookup"><span data-stu-id="eaa67-113">The following information provide examples of how to use the SQLMetal command-line tool.</span></span> <span data-ttu-id="eaa67-114">Para obter mais informações, consulte [SqlMetal.exe (ferramenta de geração de código)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="eaa67-114">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="eaa67-115">Exemplo</span><span class="sxs-lookup"><span data-stu-id="eaa67-115">Example</span></span>  
 <span data-ttu-id="eaa67-116">A linha de comando SQLMetal mostrada no exemplo a seguir gera código [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] como o modelo de objeto baseado em atributos do banco de dados de exemplo Northwind.</span><span class="sxs-lookup"><span data-stu-id="eaa67-116">The SQLMetal command line shown in the following example produces [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] code as the attribute-based object model of the Northwind sample database.</span></span> <span data-ttu-id="eaa67-117">Os procedimentos armazenados e funções são renderizados também.</span><span class="sxs-lookup"><span data-stu-id="eaa67-117">Stored procedures and functions are also rendered.</span></span>  
  
```  
sqlmetal /code:northwind.vb /language:vb "c:\northwnd.mdf" /sprocs /functions  
```  
  
## <a name="example"></a><span data-ttu-id="eaa67-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="eaa67-118">Example</span></span>  
 <span data-ttu-id="eaa67-119">A linha de comando SQLMetal mostrada no exemplo a seguir gera código C# como o modelo de objeto baseado em atributos de banco de dados de exemplo Northwind.</span><span class="sxs-lookup"><span data-stu-id="eaa67-119">The SQLMetal command line shown in the following example produces C# code as the attribute-based object model of the Northwind sample database.</span></span> <span data-ttu-id="eaa67-120">Os procedimentos armazenados e funções também são processados, e os nomes de tabela são automaticamente pluralizados.</span><span class="sxs-lookup"><span data-stu-id="eaa67-120">Stored procedures and functions are also rendered, and table names are automatically pluralized.</span></span>  
  
```  
sqlmetal /code:northwind.cs /language:csharp "c:\northwnd.mdf" /sprocs /functions /pluralize  
```  
  
## <a name="see-also"></a><span data-ttu-id="eaa67-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="eaa67-121">See Also</span></span>  
 [<span data-ttu-id="eaa67-122">Guia de Programação</span><span class="sxs-lookup"><span data-stu-id="eaa67-122">Programming Guide</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/programming-guide.md)  
 [<span data-ttu-id="eaa67-123">O LINQ no modelo de objeto do SQL</span><span class="sxs-lookup"><span data-stu-id="eaa67-123">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)  
 [<span data-ttu-id="eaa67-124">Aprendendo com explicações passo a passo</span><span class="sxs-lookup"><span data-stu-id="eaa67-124">Learning by Walkthroughs</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)  
 [<span data-ttu-id="eaa67-125">Como: Personalizar Classes de entidade usando o Editor de código</span><span class="sxs-lookup"><span data-stu-id="eaa67-125">How to: Customize Entity Classes by Using the Code Editor</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)  
 [<span data-ttu-id="eaa67-126">Mapeamento de atributo</span><span class="sxs-lookup"><span data-stu-id="eaa67-126">Attribute-Based Mapping</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md)  
 [<span data-ttu-id="eaa67-127">SqlMetal.exe (Ferramenta de Geração de Código)</span><span class="sxs-lookup"><span data-stu-id="eaa67-127">SqlMetal.exe (Code Generation Tool)</span></span>](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md)  
 [<span data-ttu-id="eaa67-128">Mapeamento Externo</span><span class="sxs-lookup"><span data-stu-id="eaa67-128">External Mapping</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md)  
 <span data-ttu-id="eaa67-129">[Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md) (Baixando bancos de dados de amostra)</span><span class="sxs-lookup"><span data-stu-id="eaa67-129">[Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)</span></span>  
 [<span data-ttu-id="eaa67-130">Criando o modelo de objeto</span><span class="sxs-lookup"><span data-stu-id="eaa67-130">Creating the Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)
