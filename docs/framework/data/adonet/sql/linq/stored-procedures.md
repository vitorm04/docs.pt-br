---
title: Procedimentos armazenados
ms.date: 03/30/2017
ms.assetid: 4d23dd7a-a85f-44ff-a717-af7d0950c0fc
ms.openlocfilehash: 80ea105eef33ebb2a0e52d91a631258400ea3dff
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70792486"
---
# <a name="stored-procedures"></a><span data-ttu-id="745c4-102">Procedimentos armazenados</span><span class="sxs-lookup"><span data-stu-id="745c4-102">Stored Procedures</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="745c4-103">usa métodos em seu modelo de objeto para representar procedimentos armazenados no banco de dados.</span><span class="sxs-lookup"><span data-stu-id="745c4-103">uses methods in your object model to represent stored procedures in the database.</span></span> <span data-ttu-id="745c4-104">Você designa métodos como procedimentos armazenados aplicando o atributo <xref:System.Data.Linq.Mapping.FunctionAttribute> e, quando for necessário, o atributo <xref:System.Data.Linq.Mapping.ParameterAttribute>.</span><span class="sxs-lookup"><span data-stu-id="745c4-104">You designate methods as stored procedures by applying the <xref:System.Data.Linq.Mapping.FunctionAttribute> attribute and, where required, the <xref:System.Data.Linq.Mapping.ParameterAttribute> attribute.</span></span> <span data-ttu-id="745c4-105">Para obter mais informações, consulte [o modelo de objeto LINQ to SQL](the-linq-to-sql-object-model.md).</span><span class="sxs-lookup"><span data-stu-id="745c4-105">For more information, see [The LINQ to SQL Object Model](the-linq-to-sql-object-model.md).</span></span>  
  
 <span data-ttu-id="745c4-106">Os desenvolvedores que usam o Visual Studio normalmente usariam o Object Relational Designer para mapear procedimentos armazenados.</span><span class="sxs-lookup"><span data-stu-id="745c4-106">Developers using Visual Studio would typically use the Object Relational Designer to map stored procedures.</span></span> <span data-ttu-id="745c4-107">Os tópicos nesta seção de apresentação como formar e chamar esses métodos em seu aplicativo se você escreve o código que você mesmo.</span><span class="sxs-lookup"><span data-stu-id="745c4-107">The topics in this section show how to form and call these methods in your application if you write the code yourself.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="745c4-108">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="745c4-108">In This Section</span></span>  
 [<span data-ttu-id="745c4-109">Como: Retornar conjuntos de linhas</span><span class="sxs-lookup"><span data-stu-id="745c4-109">How to: Return Rowsets</span></span>](how-to-return-rowsets.md)  
 <span data-ttu-id="745c4-110">Descreve como retornar linhas de dados e mostra como usar um parâmetro de entrada.</span><span class="sxs-lookup"><span data-stu-id="745c4-110">Describes how to return rows of data and shows how to use an input parameter.</span></span>  
  
 [<span data-ttu-id="745c4-111">Como: Usar procedimentos armazenados que usam parâmetros</span><span class="sxs-lookup"><span data-stu-id="745c4-111">How to: Use Stored Procedures that Take Parameters</span></span>](how-to-use-stored-procedures-that-take-parameters.md)  
 <span data-ttu-id="745c4-112">Descreve como usar os parâmetros de entrada e saída.</span><span class="sxs-lookup"><span data-stu-id="745c4-112">Describes how to use input and output parameters.</span></span>  
  
 [<span data-ttu-id="745c4-113">Como: Usar procedimentos armazenados mapeados para várias formas de resultado</span><span class="sxs-lookup"><span data-stu-id="745c4-113">How to: Use Stored Procedures Mapped for Multiple Result Shapes</span></span>](how-to-use-stored-procedures-mapped-for-multiple-result-shapes.md)  
 <span data-ttu-id="745c4-114">Descreve como fornecer para retornos de várias formas no mesmo procedimento armazenado.</span><span class="sxs-lookup"><span data-stu-id="745c4-114">Describes how to provide for returns of multiple shapes in the same stored procedure.</span></span>  
  
 [<span data-ttu-id="745c4-115">Como: Usar procedimentos armazenados mapeados para formas de resultados sequenciais</span><span class="sxs-lookup"><span data-stu-id="745c4-115">How to: Use Stored Procedures Mapped for Sequential Result Shapes</span></span>](how-to-use-stored-procedures-mapped-for-sequential-result-shapes.md)  
 <span data-ttu-id="745c4-116">Descreve como fornecer para várias formas onde a sequência de retorno é conhecida.</span><span class="sxs-lookup"><span data-stu-id="745c4-116">Describes how to provide for multiple shapes where the return sequence is known.</span></span>  
  
 [<span data-ttu-id="745c4-117">Personalizando operações usando procedimentos armazenados</span><span class="sxs-lookup"><span data-stu-id="745c4-117">Customizing Operations By Using Stored Procedures</span></span>](customizing-operations-by-using-stored-procedures.md)  
 <span data-ttu-id="745c4-118">Descreve como usar procedimentos armazenados para implementar operações de inserção, atualização e exclusão.</span><span class="sxs-lookup"><span data-stu-id="745c4-118">Describes how to use stored procedures to implement insert, update, and delete operations.</span></span>  
  
 [<span data-ttu-id="745c4-119">Personalizando operações usando procedimentos armazenados exclusivamente</span><span class="sxs-lookup"><span data-stu-id="745c4-119">Customizing Operations by Using Stored Procedures Exclusively</span></span>](customizing-operations-by-using-stored-procedures-exclusively.md)  
 <span data-ttu-id="745c4-120">Descreve como usar nada além de procedimentos armazenados para implementar operações de inserção, atualização e exclusão.</span><span class="sxs-lookup"><span data-stu-id="745c4-120">Describes how to use nothing but stored procedures to implement insert, update, and delete operations.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="745c4-121">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="745c4-121">Related Sections</span></span>  
 [<span data-ttu-id="745c4-122">Guia de Programação</span><span class="sxs-lookup"><span data-stu-id="745c4-122">Programming Guide</span></span>](programming-guide.md)  
 <span data-ttu-id="745c4-123">Fornece informações sobre como criar e usar seu modelo de objeto do [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="745c4-123">Provides information about how to create and use your [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] object model.</span></span>  
  
 [<span data-ttu-id="745c4-124">Passo a passo: Usando apenas procedimentos armazenados (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="745c4-124">Walkthrough: Using Only Stored Procedures (Visual Basic)</span></span>](walkthrough-using-only-stored-procedures-visual-basic.md)  
 <span data-ttu-id="745c4-125">Inclui os procedimentos que ilustram como usar procedimentos armazenados no Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="745c4-125">Includes procedures that illustrate how to use stored procedures in Visual Basic.</span></span>  
  
 [<span data-ttu-id="745c4-126">Passo a passo: Usando apenas procedimentos armazenados (C#)</span><span class="sxs-lookup"><span data-stu-id="745c4-126">Walkthrough: Using Only Stored Procedures (C#)</span></span>](walkthrough-using-only-stored-procedures-csharp.md)  
 <span data-ttu-id="745c4-127">Inclui os procedimentos que ilustram como usar procedimentos armazenados no C#.</span><span class="sxs-lookup"><span data-stu-id="745c4-127">Includes procedures that illustrate how to use stored procedures in C#.</span></span>
