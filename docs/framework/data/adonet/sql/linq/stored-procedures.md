---
title: Procedimentos armazenados
ms.date: 03/30/2017
ms.assetid: 4d23dd7a-a85f-44ff-a717-af7d0950c0fc
ms.openlocfilehash: 9201965192f300de62679c1e5be75cf98a24e700
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33360590"
---
# <a name="stored-procedures"></a><span data-ttu-id="00610-102">Procedimentos armazenados</span><span class="sxs-lookup"><span data-stu-id="00610-102">Stored Procedures</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="00610-103"> usa métodos em seu modelo de objeto para representar os procedimentos armazenados no banco de dados.</span><span class="sxs-lookup"><span data-stu-id="00610-103"> uses methods in your object model to represent stored procedures in the database.</span></span> <span data-ttu-id="00610-104">Você designa métodos como procedimentos armazenados aplicando o atributo <xref:System.Data.Linq.Mapping.FunctionAttribute> e, quando for necessário, o atributo <xref:System.Data.Linq.Mapping.ParameterAttribute>.</span><span class="sxs-lookup"><span data-stu-id="00610-104">You designate methods as stored procedures by applying the <xref:System.Data.Linq.Mapping.FunctionAttribute> attribute and, where required, the <xref:System.Data.Linq.Mapping.ParameterAttribute> attribute.</span></span> <span data-ttu-id="00610-105">Para obter mais informações, consulte [o LINQ no modelo de objeto do SQL](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md).</span><span class="sxs-lookup"><span data-stu-id="00610-105">For more information, see [The LINQ to SQL Object Model](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md).</span></span>  
  
 <span data-ttu-id="00610-106">Os desenvolvedores usando o Visual Studio normalmente usaria o [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] para mapear os procedimentos armazenados.</span><span class="sxs-lookup"><span data-stu-id="00610-106">Developers using Visual Studio would typically use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] to map stored procedures.</span></span> <span data-ttu-id="00610-107">Os tópicos nesta seção de apresentação como formar e chamar esses métodos em seu aplicativo se você escreve o código que você mesmo.</span><span class="sxs-lookup"><span data-stu-id="00610-107">The topics in this section show how to form and call these methods in your application if you write the code yourself.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="00610-108">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="00610-108">In This Section</span></span>  
 [<span data-ttu-id="00610-109">Como retornar conjuntos de linhas</span><span class="sxs-lookup"><span data-stu-id="00610-109">How to: Return Rowsets</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-return-rowsets.md)  
 <span data-ttu-id="00610-110">Descreve como retornar linhas de dados e mostra como usar um parâmetro de entrada.</span><span class="sxs-lookup"><span data-stu-id="00610-110">Describes how to return rows of data and shows how to use an input parameter.</span></span>  
  
 [<span data-ttu-id="00610-111">Como usar procedimentos armazenados que usam parâmetros</span><span class="sxs-lookup"><span data-stu-id="00610-111">How to: Use Stored Procedures that Take Parameters</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-use-stored-procedures-that-take-parameters.md)  
 <span data-ttu-id="00610-112">Descreve como usar os parâmetros de entrada e saída.</span><span class="sxs-lookup"><span data-stu-id="00610-112">Describes how to use input and output parameters.</span></span>  
  
 [<span data-ttu-id="00610-113">Como usar procedimentos armazenados mapeados para várias formas de resultado</span><span class="sxs-lookup"><span data-stu-id="00610-113">How to: Use Stored Procedures Mapped for Multiple Result Shapes</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-use-stored-procedures-mapped-for-multiple-result-shapes.md)  
 <span data-ttu-id="00610-114">Descreve como fornecer para retornos de várias formas no mesmo procedimento armazenado.</span><span class="sxs-lookup"><span data-stu-id="00610-114">Describes how to provide for returns of multiple shapes in the same stored procedure.</span></span>  
  
 [<span data-ttu-id="00610-115">Como usar procedimentos armazenados mapeados para formas sequenciais de resultado</span><span class="sxs-lookup"><span data-stu-id="00610-115">How to: Use Stored Procedures Mapped for Sequential Result Shapes</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-use-stored-procedures-mapped-for-sequential-result-shapes.md)  
 <span data-ttu-id="00610-116">Descreve como fornecer para várias formas onde a sequência de retorno é conhecida.</span><span class="sxs-lookup"><span data-stu-id="00610-116">Describes how to provide for multiple shapes where the return sequence is known.</span></span>  
  
 [<span data-ttu-id="00610-117">Personalizando operações usando procedimentos armazenados</span><span class="sxs-lookup"><span data-stu-id="00610-117">Customizing Operations By Using Stored Procedures</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/customizing-operations-by-using-stored-procedures.md)  
 <span data-ttu-id="00610-118">Descreve como usar procedimentos armazenados para implementar operações de inserção, atualização e exclusão.</span><span class="sxs-lookup"><span data-stu-id="00610-118">Describes how to use stored procedures to implement insert, update, and delete operations.</span></span>  
  
 [<span data-ttu-id="00610-119">Personalizando operações usando procedimentos armazenados exclusivamente</span><span class="sxs-lookup"><span data-stu-id="00610-119">Customizing Operations by Using Stored Procedures Exclusively</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/customizing-operations-by-using-stored-procedures-exclusively.md)  
 <span data-ttu-id="00610-120">Descreve como usar nada além de procedimentos armazenados para implementar operações de inserção, atualização e exclusão.</span><span class="sxs-lookup"><span data-stu-id="00610-120">Describes how to use nothing but stored procedures to implement insert, update, and delete operations.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="00610-121">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="00610-121">Related Sections</span></span>  
 [<span data-ttu-id="00610-122">Guia de Programação</span><span class="sxs-lookup"><span data-stu-id="00610-122">Programming Guide</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/programming-guide.md)  
 <span data-ttu-id="00610-123">Fornece informações sobre como criar e usar seu modelo de objeto do [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="00610-123">Provides information about how to create and use your [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] object model.</span></span>  
  
 [<span data-ttu-id="00610-124">Passo a passo: usando somente procedimentos armazenados (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="00610-124">Walkthrough: Using Only Stored Procedures (Visual Basic)</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-using-only-stored-procedures-visual-basic.md)  
 <span data-ttu-id="00610-125">Inclui os procedimentos que ilustram como usar procedimentos armazenados no Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="00610-125">Includes procedures that illustrate how to use stored procedures in Visual Basic.</span></span>  
  
 [<span data-ttu-id="00610-126">Passo a passo: usando somente procedimentos armazenados (C#)</span><span class="sxs-lookup"><span data-stu-id="00610-126">Walkthrough: Using Only Stored Procedures (C#)</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-using-only-stored-procedures-csharp.md)  
 <span data-ttu-id="00610-127">Inclui os procedimentos que ilustram como usar procedimentos armazenados no C#.</span><span class="sxs-lookup"><span data-stu-id="00610-127">Includes procedures that illustrate how to use stored procedures in C#.</span></span>
