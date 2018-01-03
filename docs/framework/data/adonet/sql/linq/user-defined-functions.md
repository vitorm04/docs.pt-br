---
title: "Funções definidas pelo usuário"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3304c9b2-5c7a-4a95-9d45-4f260dcb606e
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 833ffbbccfb35fd51ddde5dbeb4e3de3d79923ae
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="user-defined-functions"></a><span data-ttu-id="b034d-102">Funções definidas pelo usuário</span><span class="sxs-lookup"><span data-stu-id="b034d-102">User-Defined Functions</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="b034d-103"> usa métodos no seu modelo de objeto para representar funções definidas pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="b034d-103"> uses methods in your object model to represent user-defined functions.</span></span> <span data-ttu-id="b034d-104">Você designa métodos como funções aplicando o atributo de <xref:System.Data.Linq.Mapping.FunctionAttribute> e, quando for necessário, o atributo de <xref:System.Data.Linq.Mapping.ParameterAttribute> .</span><span class="sxs-lookup"><span data-stu-id="b034d-104">You designate methods as functions by applying the <xref:System.Data.Linq.Mapping.FunctionAttribute> attribute and, where required, the <xref:System.Data.Linq.Mapping.ParameterAttribute> attribute.</span></span> <span data-ttu-id="b034d-105">Para obter mais informações, consulte [o LINQ no modelo de objeto do SQL](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md).</span><span class="sxs-lookup"><span data-stu-id="b034d-105">For more information, see [The LINQ to SQL Object Model](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md).</span></span>  
  
 <span data-ttu-id="b034d-106">Para evitar <xref:System.InvalidOperationException>, funções definidas pelo usuário em [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] devem estar em um das seguintes formas:</span><span class="sxs-lookup"><span data-stu-id="b034d-106">To avoid an <xref:System.InvalidOperationException>, user-defined functions in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] must be in one of the following forms:</span></span>  
  
-   <span data-ttu-id="b034d-107">Uma função empacotada como um chamada de método que tem os atributos corretos de mapeamento.</span><span class="sxs-lookup"><span data-stu-id="b034d-107">A function wrapped as a method call having the correct mapping attributes.</span></span> <span data-ttu-id="b034d-108">Para obter mais informações, consulte [mapeamento baseado no atributo](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="b034d-108">For more information, see [Attribute-Based Mapping](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md).</span></span>  
  
-   <span data-ttu-id="b034d-109">Um específico do método SQL estático a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b034d-109">A static SQL method specific to [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>  
  
-   <span data-ttu-id="b034d-110">Uma função suportada por um método de [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="b034d-110">A function supported by a [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] method.</span></span>  
  
 <span data-ttu-id="b034d-111">Os tópicos nesta seção de apresentação como formar e chamar esses métodos em seu aplicativo se você escreve o código que você mesmo.</span><span class="sxs-lookup"><span data-stu-id="b034d-111">The topics in this section show how to form and call these methods in your application if you write the code yourself.</span></span> <span data-ttu-id="b034d-112">Os desenvolvedores que usam [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] normalmente usariam [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] para mapear funções definidas pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="b034d-112">Developers using [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] would typically use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] to map user-defined functions.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b034d-113">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="b034d-113">In This Section</span></span>  
 [<span data-ttu-id="b034d-114">Como usar as funções definidas pelo usuário com valor escalar</span><span class="sxs-lookup"><span data-stu-id="b034d-114">How to: Use Scalar-Valued User-Defined Functions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-use-scalar-valued-user-defined-functions.md)  
 <span data-ttu-id="b034d-115">Descreve como implementar uma função que retorna valores escalares.</span><span class="sxs-lookup"><span data-stu-id="b034d-115">Describes how to implement a function that returns scalar values.</span></span>  
  
 [<span data-ttu-id="b034d-116">Como usar as funções definidas pelo usuário com valor de tabela</span><span class="sxs-lookup"><span data-stu-id="b034d-116">How to: Use Table-Valued User-Defined Functions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-use-table-valued-user-defined-functions.md)  
 <span data-ttu-id="b034d-117">Descreve como implementar uma função que retorna apresentam valores.</span><span class="sxs-lookup"><span data-stu-id="b034d-117">Describes how to implement a function that returns table values.</span></span>  
  
 [<span data-ttu-id="b034d-118">Como chamar funções definidas pelo usuário embutido</span><span class="sxs-lookup"><span data-stu-id="b034d-118">How to: Call User-Defined Functions Inline</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-call-user-defined-functions-inline.md)  
 <span data-ttu-id="b034d-119">Descreve como fazer chamadas a funções embutidas e as diferenças em execução quando o chamada é feita embutido.</span><span class="sxs-lookup"><span data-stu-id="b034d-119">Describes how to make inline calls to functions and the differences in execution when the call is made inline.</span></span>
