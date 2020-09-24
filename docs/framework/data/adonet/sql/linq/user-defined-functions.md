---
title: Funções definidas pelo usuário
ms.date: 03/30/2017
ms.assetid: 3304c9b2-5c7a-4a95-9d45-4f260dcb606e
ms.openlocfilehash: 061e07ba91a1742c90a594bf42f12e64172b2481
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91164110"
---
# <a name="user-defined-functions"></a><span data-ttu-id="b23bb-102">Funções definidas pelo usuário</span><span class="sxs-lookup"><span data-stu-id="b23bb-102">User-Defined Functions</span></span>

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="b23bb-103">usa métodos no seu modelo de objeto para representar funções definidas pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="b23bb-103">uses methods in your object model to represent user-defined functions.</span></span> <span data-ttu-id="b23bb-104">Você designa métodos como funções aplicando o atributo de <xref:System.Data.Linq.Mapping.FunctionAttribute> e, quando for necessário, o atributo de <xref:System.Data.Linq.Mapping.ParameterAttribute> .</span><span class="sxs-lookup"><span data-stu-id="b23bb-104">You designate methods as functions by applying the <xref:System.Data.Linq.Mapping.FunctionAttribute> attribute and, where required, the <xref:System.Data.Linq.Mapping.ParameterAttribute> attribute.</span></span> <span data-ttu-id="b23bb-105">Para obter mais informações, consulte [o modelo de objeto LINQ to SQL](the-linq-to-sql-object-model.md).</span><span class="sxs-lookup"><span data-stu-id="b23bb-105">For more information, see [The LINQ to SQL Object Model](the-linq-to-sql-object-model.md).</span></span>  
  
 <span data-ttu-id="b23bb-106">Para evitar <xref:System.InvalidOperationException>, funções definidas pelo usuário em [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] devem estar em um das seguintes formas:</span><span class="sxs-lookup"><span data-stu-id="b23bb-106">To avoid an <xref:System.InvalidOperationException>, user-defined functions in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] must be in one of the following forms:</span></span>  
  
- <span data-ttu-id="b23bb-107">Uma função empacotada como um chamada de método que tem os atributos corretos de mapeamento.</span><span class="sxs-lookup"><span data-stu-id="b23bb-107">A function wrapped as a method call having the correct mapping attributes.</span></span> <span data-ttu-id="b23bb-108">Para obter mais informações, consulte [mapeamento baseado em atributo](attribute-based-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="b23bb-108">For more information, see [Attribute-Based Mapping](attribute-based-mapping.md).</span></span>  
  
- <span data-ttu-id="b23bb-109">Um específico do método SQL estático a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b23bb-109">A static SQL method specific to [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>  
  
- <span data-ttu-id="b23bb-110">Uma função com suporte de um método .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b23bb-110">A function supported by a .NET Framework method.</span></span>  
  
 <span data-ttu-id="b23bb-111">Os tópicos nesta seção de apresentação como formar e chamar esses métodos em seu aplicativo se você escreve o código que você mesmo.</span><span class="sxs-lookup"><span data-stu-id="b23bb-111">The topics in this section show how to form and call these methods in your application if you write the code yourself.</span></span> <span data-ttu-id="b23bb-112">Os desenvolvedores que usam o Visual Studio normalmente usariam o Object Relational Designer para mapear funções definidas pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="b23bb-112">Developers using Visual Studio would typically use the Object Relational Designer to map user-defined functions.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b23bb-113">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="b23bb-113">In This Section</span></span>  

 [<span data-ttu-id="b23bb-114">Como: usar funções definidas pelo usuário com valor escalar</span><span class="sxs-lookup"><span data-stu-id="b23bb-114">How to: Use Scalar-Valued User-Defined Functions</span></span>](how-to-use-scalar-valued-user-defined-functions.md)  
 <span data-ttu-id="b23bb-115">Descreve como implementar uma função que retorna valores escalares.</span><span class="sxs-lookup"><span data-stu-id="b23bb-115">Describes how to implement a function that returns scalar values.</span></span>  
  
 [<span data-ttu-id="b23bb-116">Como: usar funções definidas pelo usuário com valor de tabela</span><span class="sxs-lookup"><span data-stu-id="b23bb-116">How to: Use Table-Valued User-Defined Functions</span></span>](how-to-use-table-valued-user-defined-functions.md)  
 <span data-ttu-id="b23bb-117">Descreve como implementar uma função que retorna apresentam valores.</span><span class="sxs-lookup"><span data-stu-id="b23bb-117">Describes how to implement a function that returns table values.</span></span>  
  
 [<span data-ttu-id="b23bb-118">Como: chamar funções embutidas definidas pelo usuário</span><span class="sxs-lookup"><span data-stu-id="b23bb-118">How to: Call User-Defined Functions Inline</span></span>](how-to-call-user-defined-functions-inline.md)  
 <span data-ttu-id="b23bb-119">Descreve como fazer chamadas a funções embutidas e as diferenças em execução quando o chamada é feita embutido.</span><span class="sxs-lookup"><span data-stu-id="b23bb-119">Describes how to make inline calls to functions and the differences in execution when the call is made inline.</span></span>
