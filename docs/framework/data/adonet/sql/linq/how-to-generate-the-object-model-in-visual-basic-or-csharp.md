---
title: 'Como: gerar o modelo de objeto em Visual Basic ou em C#'
ms.date: 03/30/2017
ms.assetid: a0c73b33-5650-420c-b9dc-f49310c201ee
ms.openlocfilehash: e2491cf18be556cb26f084a178b7bf09448c6904
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90546608"
---
# <a name="how-to-generate-the-object-model-in-visual-basic-or-c"></a><span data-ttu-id="62ede-102">Como gerar o modelo de objeto em Visual Basic ou C\#</span><span class="sxs-lookup"><span data-stu-id="62ede-102">How to: Generate the Object Model in Visual Basic or C\#</span></span>
<span data-ttu-id="62ede-103">No [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], um modelo de objeto em sua própria linguagem de programação é mapeado para um banco de dados relacional.</span><span class="sxs-lookup"><span data-stu-id="62ede-103">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], an object model in your own programming language is mapped to a relational database.</span></span> <span data-ttu-id="62ede-104">Duas ferramentas estão disponíveis para gerar automaticamente um modelo de Visual Basic ou C# a partir dos metadados de um banco de dados existente.</span><span class="sxs-lookup"><span data-stu-id="62ede-104">Two tools are available for automatically generating a Visual Basic or C# model from the metadata of an existing database.</span></span>  
  
- <span data-ttu-id="62ede-105">Se você estiver usando o Visual Studio, poderá usar o Object Relational Designer para gerar um modelo de objeto.</span><span class="sxs-lookup"><span data-stu-id="62ede-105">If you are using Visual Studio, you can use the Object Relational Designer to generate an object model.</span></span> <span data-ttu-id="62ede-106">O o/R Designer fornece uma rica interface do usuário para ajudá-lo a gerar um [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] modelo de objeto.</span><span class="sxs-lookup"><span data-stu-id="62ede-106">The O/R Designer provides a rich user interface to help you generate a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] object model.</span></span> <span data-ttu-id="62ede-107">Para obter mais informações, consulte [Ferramentas do LINQ to SQL no Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).</span><span class="sxs-lookup"><span data-stu-id="62ede-107">For more information see, [Linq to SQL Tools in Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).</span></span>
  
- <span data-ttu-id="62ede-108">A ferramenta de linha de comando SQLMetal.</span><span class="sxs-lookup"><span data-stu-id="62ede-108">The SQLMetal command-line tool.</span></span> <span data-ttu-id="62ede-109">Para obter mais informações, consulte [SqlMetal.exe (ferramenta de geração de código)](../../../../tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="62ede-109">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="62ede-110">Se você não tiver um banco de dados existente e não quiser criar um a partir de um modelo de objeto, poderá criar seu modelo de objeto usando o editor de códigos e <xref:System.Data.Linq.DataContext.CreateDatabase%2A>.</span><span class="sxs-lookup"><span data-stu-id="62ede-110">If you do not have an existing database and want to create one from an object model, you can create your object model by using your code editor and <xref:System.Data.Linq.DataContext.CreateDatabase%2A>.</span></span> <span data-ttu-id="62ede-111">Para obter mais informações, consulte [como criar dinamicamente um banco de dados](how-to-dynamically-create-a-database.md).</span><span class="sxs-lookup"><span data-stu-id="62ede-111">For more information, see [How to: Dynamically Create a Database](how-to-dynamically-create-a-database.md).</span></span>  
  
 <span data-ttu-id="62ede-112">A documentação do o/R Designer fornece exemplos de como gerar um modelo de objeto Visual Basic ou C# usando o o/R Designer.</span><span class="sxs-lookup"><span data-stu-id="62ede-112">Documentation for the O/R Designer provides examples of how to generate a Visual Basic or C# object model by using the O/R Designer.</span></span> <span data-ttu-id="62ede-113">As informações a seguir fornecem exemplos de como usar a ferramenta de linha de comando SqlMetal.</span><span class="sxs-lookup"><span data-stu-id="62ede-113">The following information provide examples of how to use the SQLMetal command-line tool.</span></span> <span data-ttu-id="62ede-114">Para obter mais informações, consulte [SqlMetal.exe (ferramenta de geração de código)](../../../../tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="62ede-114">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="62ede-115">Exemplo</span><span class="sxs-lookup"><span data-stu-id="62ede-115">Example</span></span>  
 <span data-ttu-id="62ede-116">A linha de comando SqlMetal mostrada no exemplo a seguir produz Visual Basic código como o modelo de objeto baseado em atributo do banco de dados de exemplo Northwind.</span><span class="sxs-lookup"><span data-stu-id="62ede-116">The SQLMetal command line shown in the following example produces Visual Basic code as the attribute-based object model of the Northwind sample database.</span></span> <span data-ttu-id="62ede-117">Os procedimentos armazenados e funções são renderizados também.</span><span class="sxs-lookup"><span data-stu-id="62ede-117">Stored procedures and functions are also rendered.</span></span>  
  
```console  
sqlmetal /code:northwind.vb /language:vb "c:\northwnd.mdf" /sprocs /functions  
```  
  
## <a name="example"></a><span data-ttu-id="62ede-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="62ede-118">Example</span></span>  
 <span data-ttu-id="62ede-119">A linha de comando SQLMetal mostrada no exemplo a seguir gera código C# como o modelo de objeto baseado em atributos de banco de dados de exemplo Northwind.</span><span class="sxs-lookup"><span data-stu-id="62ede-119">The SQLMetal command line shown in the following example produces C# code as the attribute-based object model of the Northwind sample database.</span></span> <span data-ttu-id="62ede-120">Os procedimentos armazenados e funções também são processados, e os nomes de tabela são automaticamente pluralizados.</span><span class="sxs-lookup"><span data-stu-id="62ede-120">Stored procedures and functions are also rendered, and table names are automatically pluralized.</span></span>  
  
```console  
sqlmetal /code:northwind.cs /language:csharp "c:\northwnd.mdf" /sprocs /functions /pluralize  
```  
  
## <a name="see-also"></a><span data-ttu-id="62ede-121">Confira também</span><span class="sxs-lookup"><span data-stu-id="62ede-121">See also</span></span>

- [<span data-ttu-id="62ede-122">Guia de programação</span><span class="sxs-lookup"><span data-stu-id="62ede-122">Programming Guide</span></span>](programming-guide.md)
- [<span data-ttu-id="62ede-123">Modelo de objeto LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="62ede-123">The LINQ to SQL Object Model</span></span>](the-linq-to-sql-object-model.md)
- [<span data-ttu-id="62ede-124">Aprendendo com explicações passo a passo</span><span class="sxs-lookup"><span data-stu-id="62ede-124">Learning by Walkthroughs</span></span>](learning-by-walkthroughs.md)
- [<span data-ttu-id="62ede-125">Como: personalizar classes de entidade usando o editor de códigos</span><span class="sxs-lookup"><span data-stu-id="62ede-125">How to: Customize Entity Classes by Using the Code Editor</span></span>](how-to-customize-entity-classes-by-using-the-code-editor.md)
- [<span data-ttu-id="62ede-126">Mapeamento baseado em atributos</span><span class="sxs-lookup"><span data-stu-id="62ede-126">Attribute-Based Mapping</span></span>](attribute-based-mapping.md)
- [<span data-ttu-id="62ede-127">SqlMetal.exe (ferramenta de geração de código)</span><span class="sxs-lookup"><span data-stu-id="62ede-127">SqlMetal.exe (Code Generation Tool)</span></span>](../../../../tools/sqlmetal-exe-code-generation-tool.md)
- [<span data-ttu-id="62ede-128">Mapeamento externo</span><span class="sxs-lookup"><span data-stu-id="62ede-128">External Mapping</span></span>](external-mapping.md)
- [<span data-ttu-id="62ede-129">Baixar bancos de dados de amostra</span><span class="sxs-lookup"><span data-stu-id="62ede-129">Downloading Sample Databases</span></span>](downloading-sample-databases.md)
- [<span data-ttu-id="62ede-130">Criando o modelo de objeto</span><span class="sxs-lookup"><span data-stu-id="62ede-130">Creating the Object Model</span></span>](creating-the-object-model.md)
