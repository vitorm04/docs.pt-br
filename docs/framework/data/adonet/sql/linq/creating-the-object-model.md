---
title: Criando o modelo de objeto
ms.date: 03/30/2017
ms.assetid: 27afce86-9b1d-45fb-8e0b-636bf671a236
ms.openlocfilehash: 7724d6e75b350e5c57f090d42ef1f49c4d3593b8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33359927"
---
# <a name="creating-the-object-model"></a><span data-ttu-id="1b41b-102">Criando o modelo de objeto</span><span class="sxs-lookup"><span data-stu-id="1b41b-102">Creating the Object Model</span></span>
<span data-ttu-id="1b41b-103">Você pode criar seu modelo de objeto de um banco de dados existente e usar o modelo em seu estado padrão.</span><span class="sxs-lookup"><span data-stu-id="1b41b-103">You can create your object model from an existing database and use the model in its default state.</span></span> <span data-ttu-id="1b41b-104">Você também pode personalizar vários aspectos do modelo e seu comportamento.</span><span class="sxs-lookup"><span data-stu-id="1b41b-104">You can also customize many aspects of the model and its behavior.</span></span>  
  
 <span data-ttu-id="1b41b-105">Se você estiver usando o Visual Studio, você pode usar o [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] para criar seu modelo de objeto.</span><span class="sxs-lookup"><span data-stu-id="1b41b-105">If you are using Visual Studio, you can use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] to create your object model.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1b41b-106">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="1b41b-106">In This Section</span></span>  
 [<span data-ttu-id="1b41b-107">Como gerar o modelo de objeto em Visual Basic ou C#</span><span class="sxs-lookup"><span data-stu-id="1b41b-107">How to: Generate the Object Model in Visual Basic or C#</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-generate-the-object-model-in-visual-basic-or-csharp.md)  
 <span data-ttu-id="1b41b-108">Descreve como usar a ferramenta de linha de comando SQLMetal.</span><span class="sxs-lookup"><span data-stu-id="1b41b-108">Describes how to use the SQLMetal command-line tool.</span></span> <span data-ttu-id="1b41b-109">Também fornece um link para o [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] para usuários do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="1b41b-109">Also provides a link to the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] for Visual Studio users</span></span>  
  
 [<span data-ttu-id="1b41b-110">Como gerar o modelo de objeto como um arquivo externo</span><span class="sxs-lookup"><span data-stu-id="1b41b-110">How to: Generate the Object Model as an External File</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-generate-the-object-model-as-an-external-file.md)  
 <span data-ttu-id="1b41b-111">Descreve como gerar um arquivo de mapeamento externo em vez de usar o mapeamento baseado em atributos.</span><span class="sxs-lookup"><span data-stu-id="1b41b-111">Describes how to generate an external mapping file instead of using attribute-based mapping.</span></span>  
  
 [<span data-ttu-id="1b41b-112">Como gerar código personalizado modificando um arquivo DBML</span><span class="sxs-lookup"><span data-stu-id="1b41b-112">How to: Generate Customized Code by Modifying a DBML File</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-generate-customized-code-by-modifying-a-dbml-file.md)  
 <span data-ttu-id="1b41b-113">Descreve como gerar o código do Visual Basic ou c# em um arquivo de metadados DBML.</span><span class="sxs-lookup"><span data-stu-id="1b41b-113">Describes how to generate Visual Basic or C# code from a DBML metadata file.</span></span>  
  
 [<span data-ttu-id="1b41b-114">Como validar DBML e arquivos de mapeamento externos</span><span class="sxs-lookup"><span data-stu-id="1b41b-114">How to: Validate DBML and External Mapping Files</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-validate-dbml-and-external-mapping-files.md)  
 <span data-ttu-id="1b41b-115">Descreve como validar os arquivos de mapeamento que você modificou (avançado).</span><span class="sxs-lookup"><span data-stu-id="1b41b-115">Describes how to validate mapping files that you have modified (advanced).</span></span>  
  
 [<span data-ttu-id="1b41b-116">Como tornar entidades serializáveis</span><span class="sxs-lookup"><span data-stu-id="1b41b-116">How to: Make Entities Serializable</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-make-entities-serializable.md)  
 <span data-ttu-id="1b41b-117">Descreve como adicionar os atributos apropriados para tornar as entidades serializáveis.</span><span class="sxs-lookup"><span data-stu-id="1b41b-117">Describes how to add appropriate attributes to make entities serializable.</span></span>  
  
 [<span data-ttu-id="1b41b-118">Como personalizar classes de entidade usando o Editor de código</span><span class="sxs-lookup"><span data-stu-id="1b41b-118">How to: Customize Entity Classes by Using the Code Editor</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)  
 <span data-ttu-id="1b41b-119">Descreve como usar o editor de códigos para escrever seu próprio código de mapeamento, ou personalizar o código que foi gerado automaticamente.</span><span class="sxs-lookup"><span data-stu-id="1b41b-119">Describes how to use the code editor to write your own mapping code, or customize code that has been autogenerated.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="1b41b-120">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="1b41b-120">Related Sections</span></span>  
 [<span data-ttu-id="1b41b-121">O modelo de objeto LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="1b41b-121">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)  
 <span data-ttu-id="1b41b-122">Fornece detalhes sobre o [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] modelo de objeto.</span><span class="sxs-lookup"><span data-stu-id="1b41b-122">Provides details about the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] object model.</span></span>  
  
 [<span data-ttu-id="1b41b-123">Etapas típicas para usar o LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="1b41b-123">Typical Steps for Using LINQ to SQL</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/typical-steps-for-using-linq-to-sql.md)  
 <span data-ttu-id="1b41b-124">Explica as etapas típicas que você segue para implementar um aplicativo [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1b41b-124">Explains the typical steps that you follow to implement a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] application.</span></span>
