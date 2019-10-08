---
title: 'Como: gerar o modelo de objeto em Visual Basic ou em C#'
ms.date: 03/30/2017
ms.assetid: a0c73b33-5650-420c-b9dc-f49310c201ee
ms.openlocfilehash: 7d2c0600534c93f5884eec48a4bdaa3ce99945e9
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72002807"
---
# <a name="how-to-generate-the-object-model-in-visual-basic-or-c"></a><span data-ttu-id="15691-102">Como: Gerar o modelo de objeto em Visual Basic ou C @ no__t-0</span><span class="sxs-lookup"><span data-stu-id="15691-102">How to: Generate the Object Model in Visual Basic or C\#</span></span>
<span data-ttu-id="15691-103">No [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], um modelo de objeto em sua própria linguagem de programação é mapeado para um banco de dados relacional.</span><span class="sxs-lookup"><span data-stu-id="15691-103">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], an object model in your own programming language is mapped to a relational database.</span></span> <span data-ttu-id="15691-104">Duas ferramentas estão disponíveis para gerar automaticamente um Visual Basic ou C# modelo a partir dos metadados de um banco de dados existente.</span><span class="sxs-lookup"><span data-stu-id="15691-104">Two tools are available for automatically generating a Visual Basic or C# model from the metadata of an existing database.</span></span>  
  
- <span data-ttu-id="15691-105">Se você estiver usando o Visual Studio, poderá usar o Object Relational Designer para gerar um modelo de objeto.</span><span class="sxs-lookup"><span data-stu-id="15691-105">If you are using Visual Studio, you can use the Object Relational Designer to generate an object model.</span></span> <span data-ttu-id="15691-106">O o/R Designer fornece uma rica interface de usuário para ajudá-lo a gerar um modelo de objeto [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="15691-106">The O/R Designer provides a rich user interface to help you generate a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] object model.</span></span> <span data-ttu-id="15691-107">Para obter mais informações, consulte [Ferramentas do LINQ to SQL no Visual Studio](https://docs.microsoft.com/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).</span><span class="sxs-lookup"><span data-stu-id="15691-107">For more information see, [Linq to SQL Tools in Visual Studio](https://docs.microsoft.com/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).</span></span>
  
- <span data-ttu-id="15691-108">A ferramenta de linha de comando SQLMetal.</span><span class="sxs-lookup"><span data-stu-id="15691-108">The SQLMetal command-line tool.</span></span> <span data-ttu-id="15691-109">Para obter mais informações, consulte [SqlMetal.exe (ferramenta de geração de código)](../../../../tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="15691-109">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="15691-110">Se você não tiver um banco de dados existente e não quiser criar um a partir de um modelo de objeto, poderá criar seu modelo de objeto usando o editor de códigos e <xref:System.Data.Linq.DataContext.CreateDatabase%2A>.</span><span class="sxs-lookup"><span data-stu-id="15691-110">If you do not have an existing database and want to create one from an object model, you can create your object model by using your code editor and <xref:System.Data.Linq.DataContext.CreateDatabase%2A>.</span></span> <span data-ttu-id="15691-111">Para obter mais informações, confira [Como: Crie dinamicamente um banco de dados @ no__t-0.</span><span class="sxs-lookup"><span data-stu-id="15691-111">For more information, see [How to: Dynamically Create a Database](how-to-dynamically-create-a-database.md).</span></span>  
  
 <span data-ttu-id="15691-112">A documentação do o/R Designer fornece exemplos de como gerar um modelo de Visual Basic C# ou de objeto usando o o/r designer.</span><span class="sxs-lookup"><span data-stu-id="15691-112">Documentation for the O/R Designer provides examples of how to generate a Visual Basic or C# object model by using the O/R Designer.</span></span> <span data-ttu-id="15691-113">As informações a seguir fornecem exemplos de como usar a ferramenta de linha de comando SqlMetal.</span><span class="sxs-lookup"><span data-stu-id="15691-113">The following information provide examples of how to use the SQLMetal command-line tool.</span></span> <span data-ttu-id="15691-114">Para obter mais informações, consulte [SqlMetal.exe (ferramenta de geração de código)](../../../../tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="15691-114">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="15691-115">Exemplo</span><span class="sxs-lookup"><span data-stu-id="15691-115">Example</span></span>  
 <span data-ttu-id="15691-116">A linha de comando SqlMetal mostrada no exemplo a seguir produz Visual Basic código como o modelo de objeto baseado em atributo do banco de dados de exemplo Northwind.</span><span class="sxs-lookup"><span data-stu-id="15691-116">The SQLMetal command line shown in the following example produces Visual Basic code as the attribute-based object model of the Northwind sample database.</span></span> <span data-ttu-id="15691-117">Os procedimentos armazenados e funções são renderizados também.</span><span class="sxs-lookup"><span data-stu-id="15691-117">Stored procedures and functions are also rendered.</span></span>  
  
```console  
sqlmetal /code:northwind.vb /language:vb "c:\northwnd.mdf" /sprocs /functions  
```  
  
## <a name="example"></a><span data-ttu-id="15691-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="15691-118">Example</span></span>  
 <span data-ttu-id="15691-119">A linha de comando SQLMetal mostrada no exemplo a seguir gera código C# como o modelo de objeto baseado em atributos de banco de dados de exemplo Northwind.</span><span class="sxs-lookup"><span data-stu-id="15691-119">The SQLMetal command line shown in the following example produces C# code as the attribute-based object model of the Northwind sample database.</span></span> <span data-ttu-id="15691-120">Os procedimentos armazenados e funções também são processados, e os nomes de tabela são automaticamente pluralizados.</span><span class="sxs-lookup"><span data-stu-id="15691-120">Stored procedures and functions are also rendered, and table names are automatically pluralized.</span></span>  
  
```console  
sqlmetal /code:northwind.cs /language:csharp "c:\northwnd.mdf" /sprocs /functions /pluralize  
```  
  
## <a name="see-also"></a><span data-ttu-id="15691-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="15691-121">See also</span></span>

- [<span data-ttu-id="15691-122">Guia de Programação</span><span class="sxs-lookup"><span data-stu-id="15691-122">Programming Guide</span></span>](programming-guide.md)
- [<span data-ttu-id="15691-123">O modelo de objeto LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="15691-123">The LINQ to SQL Object Model</span></span>](the-linq-to-sql-object-model.md)
- [<span data-ttu-id="15691-124">Aprendendo com explicações passo a passo</span><span class="sxs-lookup"><span data-stu-id="15691-124">Learning by Walkthroughs</span></span>](learning-by-walkthroughs.md)
- <span data-ttu-id="15691-125">[Como: Personalizar classes de entidade usando o editor de código @ no__t-0</span><span class="sxs-lookup"><span data-stu-id="15691-125">[How to: Customize Entity Classes by Using the Code Editor](how-to-customize-entity-classes-by-using-the-code-editor.md)</span></span>
- [<span data-ttu-id="15691-126">Mapeamento baseado em atributos</span><span class="sxs-lookup"><span data-stu-id="15691-126">Attribute-Based Mapping</span></span>](attribute-based-mapping.md)
- [<span data-ttu-id="15691-127">SqlMetal.exe (Ferramenta de Geração de Código)</span><span class="sxs-lookup"><span data-stu-id="15691-127">SqlMetal.exe (Code Generation Tool)</span></span>](../../../../tools/sqlmetal-exe-code-generation-tool.md)
- [<span data-ttu-id="15691-128">Mapeamento Externo</span><span class="sxs-lookup"><span data-stu-id="15691-128">External Mapping</span></span>](external-mapping.md)
- <span data-ttu-id="15691-129">[Downloading Sample Databases](downloading-sample-databases.md) (Baixando bancos de dados de amostra)</span><span class="sxs-lookup"><span data-stu-id="15691-129">[Downloading Sample Databases](downloading-sample-databases.md)</span></span>
- [<span data-ttu-id="15691-130">Criando o modelo de objeto</span><span class="sxs-lookup"><span data-stu-id="15691-130">Creating the Object Model</span></span>](creating-the-object-model.md)
