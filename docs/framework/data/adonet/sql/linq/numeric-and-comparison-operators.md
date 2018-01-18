---
title: "Numérico e operadores de comparação"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 25b4a26a-06f2-4f80-87a9-76705ed46197
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 56558e790b8aee300da0a75ade7c0ac451a0eca1
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2018
---
# <a name="numeric-and-comparison-operators"></a><span data-ttu-id="bad74-102">Numérico e operadores de comparação</span><span class="sxs-lookup"><span data-stu-id="bad74-102">Numeric and Comparison Operators</span></span>
<span data-ttu-id="bad74-103">Aritmética e operadores de comparação funciona como esperado em Common Language Runtime (CLR) exceto como segue:</span><span class="sxs-lookup"><span data-stu-id="bad74-103">Arithmetic and comparison operators work as expected in the common language runtime (CLR) except as follows:</span></span>  
  
-   <span data-ttu-id="bad74-104">O SQL não suporta o operador de módulo em números de ponto flutuante.</span><span class="sxs-lookup"><span data-stu-id="bad74-104">SQL does not support the modulus operator on floating-point numbers.</span></span>  
  
-   <span data-ttu-id="bad74-105">O SQL não oferece suporte a aritmética não-verificada.</span><span class="sxs-lookup"><span data-stu-id="bad74-105">SQL does not support unchecked arithmetic.</span></span>  
  
-   <span data-ttu-id="bad74-106">Operadores de incremento e de redução causam efeitos colaterais quando você usa os em expressões que não podem ser replicadas no SQL e, portanto, não são suportados.</span><span class="sxs-lookup"><span data-stu-id="bad74-106">Increment and decrement operators cause side-effects when you use them in expressions that cannot be replicated in SQL and are, therefore, not supported.</span></span>  
  
## <a name="supported-operators"></a><span data-ttu-id="bad74-107">Operadores suportados</span><span class="sxs-lookup"><span data-stu-id="bad74-107">Supported Operators</span></span>  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="bad74-108"> oferece suporte aos seguintes operadores.</span><span class="sxs-lookup"><span data-stu-id="bad74-108"> supports the following operators.</span></span>  
  
-   <span data-ttu-id="bad74-109">Operadores aritméticos básicos:</span><span class="sxs-lookup"><span data-stu-id="bad74-109">Basic arithmetic operators:</span></span>  
  
    -   `+`  
  
    -   <span data-ttu-id="bad74-110">`-` (subtração)</span><span class="sxs-lookup"><span data-stu-id="bad74-110">`-` (subtraction)</span></span>  
  
    -   `*`  
  
    -   `/`  
  
    -   <span data-ttu-id="bad74-111">Divisão de inteiro do Visual Basic (`\`)</span><span class="sxs-lookup"><span data-stu-id="bad74-111">Visual Basic integer division (`\`)</span></span>  
  
    -   <span data-ttu-id="bad74-112">`%` (Visual Basic) `Mod`</span><span class="sxs-lookup"><span data-stu-id="bad74-112">`%` (Visual Basic `Mod`)</span></span>  
  
    -   `<<`  
  
    -   `>>`  
  
    -   <span data-ttu-id="bad74-113">`-` (negação unária)</span><span class="sxs-lookup"><span data-stu-id="bad74-113">`-` (unary negation)</span></span>  
  
-   <span data-ttu-id="bad74-114">Operadores de comparação básicos:</span><span class="sxs-lookup"><span data-stu-id="bad74-114">Basic comparison operators:</span></span>  
  
    -   <span data-ttu-id="bad74-115">`=` Visual Basic e C# `==`</span><span class="sxs-lookup"><span data-stu-id="bad74-115">Visual Basic `=` and C# `==`</span></span>  
  
    -   <span data-ttu-id="bad74-116">`<>` Visual Basic e C# `!=`</span><span class="sxs-lookup"><span data-stu-id="bad74-116">Visual Basic `<>` and C# `!=`</span></span>  
  
    -   <span data-ttu-id="bad74-117">Visual Basic `Is/IsNot`</span><span class="sxs-lookup"><span data-stu-id="bad74-117">Visual Basic `Is/IsNot`</span></span>  
  
    -   `<`  
  
    -   `<=`  
  
    -   `>`  
  
    -   `>=`  
  
## <a name="see-also"></a><span data-ttu-id="bad74-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bad74-118">See Also</span></span>  
 [<span data-ttu-id="bad74-119">Funções e tipos de dados</span><span class="sxs-lookup"><span data-stu-id="bad74-119">Data Types and Functions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)  
 [<span data-ttu-id="bad74-120">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="bad74-120">C# Operators</span></span>](http://msdn.microsoft.com/library/0301e31f-22ad-49af-ac3c-d5eae7f0ac43)  
 [<span data-ttu-id="bad74-121">Operadores</span><span class="sxs-lookup"><span data-stu-id="bad74-121">Operators</span></span>](../../../../../visual-basic/language-reference/operators/index.md)
