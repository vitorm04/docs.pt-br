---
title: Numérico e operadores de comparação
ms.date: 03/30/2017
ms.assetid: 25b4a26a-06f2-4f80-87a9-76705ed46197
ms.openlocfilehash: 733c1e494c29f04aa06a4159c3b1dae219f01b44
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50180330"
---
# <a name="numeric-and-comparison-operators"></a><span data-ttu-id="9e929-102">Numérico e operadores de comparação</span><span class="sxs-lookup"><span data-stu-id="9e929-102">Numeric and Comparison Operators</span></span>
<span data-ttu-id="9e929-103">Aritmética e operadores de comparação funciona como esperado em Common Language Runtime (CLR) exceto como segue:</span><span class="sxs-lookup"><span data-stu-id="9e929-103">Arithmetic and comparison operators work as expected in the common language runtime (CLR) except as follows:</span></span>  
  
-   <span data-ttu-id="9e929-104">O SQL não suporta o operador de módulo em números de ponto flutuante.</span><span class="sxs-lookup"><span data-stu-id="9e929-104">SQL does not support the modulus operator on floating-point numbers.</span></span>  
  
-   <span data-ttu-id="9e929-105">O SQL não oferece suporte a aritmética não-verificada.</span><span class="sxs-lookup"><span data-stu-id="9e929-105">SQL does not support unchecked arithmetic.</span></span>  
  
-   <span data-ttu-id="9e929-106">Operadores de incremento e de redução causam efeitos colaterais quando você usa os em expressões que não podem ser replicadas no SQL e, portanto, não são suportados.</span><span class="sxs-lookup"><span data-stu-id="9e929-106">Increment and decrement operators cause side-effects when you use them in expressions that cannot be replicated in SQL and are, therefore, not supported.</span></span>  
  
## <a name="supported-operators"></a><span data-ttu-id="9e929-107">Operadores suportados</span><span class="sxs-lookup"><span data-stu-id="9e929-107">Supported Operators</span></span>  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="9e929-108">oferece suporte aos seguintes operadores.</span><span class="sxs-lookup"><span data-stu-id="9e929-108">supports the following operators.</span></span>  
  
-   <span data-ttu-id="9e929-109">Operadores aritméticos básicos:</span><span class="sxs-lookup"><span data-stu-id="9e929-109">Basic arithmetic operators:</span></span>  
  
    -   `+`  
  
    -   <span data-ttu-id="9e929-110">`-` (subtração)</span><span class="sxs-lookup"><span data-stu-id="9e929-110">`-` (subtraction)</span></span>  
  
    -   `*`  
  
    -   `/`  
  
    -   <span data-ttu-id="9e929-111">Divisão de inteiros de Visual Basic (`\`)</span><span class="sxs-lookup"><span data-stu-id="9e929-111">Visual Basic integer division (`\`)</span></span>  
  
    -   <span data-ttu-id="9e929-112">`%` (Visual Basic) `Mod`</span><span class="sxs-lookup"><span data-stu-id="9e929-112">`%` (Visual Basic `Mod`)</span></span>  
  
    -   `<<`  
  
    -   `>>`  
  
    -   <span data-ttu-id="9e929-113">`-` (negação unária)</span><span class="sxs-lookup"><span data-stu-id="9e929-113">`-` (unary negation)</span></span>  
  
-   <span data-ttu-id="9e929-114">Operadores de comparação básicos:</span><span class="sxs-lookup"><span data-stu-id="9e929-114">Basic comparison operators:</span></span>  
  
    -   <span data-ttu-id="9e929-115">`=` Visual Basic e C# `==`</span><span class="sxs-lookup"><span data-stu-id="9e929-115">Visual Basic `=` and C# `==`</span></span>  
  
    -   <span data-ttu-id="9e929-116">`<>` Visual Basic e C# `!=`</span><span class="sxs-lookup"><span data-stu-id="9e929-116">Visual Basic `<>` and C# `!=`</span></span>  
  
    -   <span data-ttu-id="9e929-117">Visual Basic `Is/IsNot`</span><span class="sxs-lookup"><span data-stu-id="9e929-117">Visual Basic `Is/IsNot`</span></span>  
  
    -   `<`  
  
    -   `<=`  
  
    -   `>`  
  
    -   `>=`  
  
## <a name="see-also"></a><span data-ttu-id="9e929-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9e929-118">See Also</span></span>  
 [<span data-ttu-id="9e929-119">Funções e tipos de dados</span><span class="sxs-lookup"><span data-stu-id="9e929-119">Data Types and Functions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)  
 [<span data-ttu-id="9e929-120">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="9e929-120">C# Operators</span></span>](../../../../../../docs/csharp/language-reference/operators/index.md)  
 [<span data-ttu-id="9e929-121">Operadores</span><span class="sxs-lookup"><span data-stu-id="9e929-121">Operators</span></span>](../../../../../visual-basic/language-reference/operators/index.md)
