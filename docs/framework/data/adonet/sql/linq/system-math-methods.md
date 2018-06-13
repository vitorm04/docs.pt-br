---
title: Métodos de System.Math
ms.date: 03/30/2017
ms.assetid: 0f299521-6f41-4720-bd70-67c93fc50948
ms.openlocfilehash: 8d0ac9e9eb394deaa9dcab1a276e3ef00e2ac01b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33357110"
---
# <a name="systemmath-methods"></a><span data-ttu-id="5ac13-102">Métodos de System.Math</span><span class="sxs-lookup"><span data-stu-id="5ac13-102">System.Math Methods</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="5ac13-103"> não oferece suporte aos seguintes métodos de <xref:System.Math> .</span><span class="sxs-lookup"><span data-stu-id="5ac13-103"> does not support the following <xref:System.Math> methods.</span></span>  
  
-   <xref:System.Math.DivRem%28System.Int32%2CSystem.Int32%2CSystem.Int32%40%29?displayProperty=nameWithType>  
  
-   <xref:System.Math.DivRem%28System.Int64%2CSystem.Int64%2CSystem.Int64%40%29?displayProperty=nameWithType>  
  
-   <xref:System.Math.IEEERemainder%28System.Double%2CSystem.Double%29?displayProperty=nameWithType>  
  
## <a name="differences-from-net"></a><span data-ttu-id="5ac13-104">Diferenças do .NET</span><span class="sxs-lookup"><span data-stu-id="5ac13-104">Differences from .NET</span></span>  
 <span data-ttu-id="5ac13-105">O.NET Framework tem a semântica por arredondamento diferente do SQL Server.</span><span class="sxs-lookup"><span data-stu-id="5ac13-105">The .NET Framework has different rounding semantics from SQL Server.</span></span> <span data-ttu-id="5ac13-106">O <xref:System.Math.Round%2A> método no .NET Framework executa *do arredondamento bancário*, no qual os números que termina em.5 arredondar para o mais próximo do mesmo dígitos em vez de para o dígito mais próximo.</span><span class="sxs-lookup"><span data-stu-id="5ac13-106">The <xref:System.Math.Round%2A> method in the .NET Framework performs *Banker's rounding*, where numbers that ends in .5 round to the nearest even digit instead of to the next higher digit.</span></span> <span data-ttu-id="5ac13-107">Por exemplo, círculos 2,5 a 2, quando círculos 3,5 a 4.</span><span class="sxs-lookup"><span data-stu-id="5ac13-107">For example, 2.5 rounds to 2, while 3.5 rounds to 4.</span></span> <span data-ttu-id="5ac13-108">(Essa técnica ajuda a evitar a polarização sistemática para os valores mais altos em grandes transações de dados.)</span><span class="sxs-lookup"><span data-stu-id="5ac13-108">(This technique helps avoid systematic bias toward higher values in large data transactions.)</span></span>  
  
 <span data-ttu-id="5ac13-109">Em SQL, a função de `ROUND` vez arredondará sempre fora de 0.</span><span class="sxs-lookup"><span data-stu-id="5ac13-109">In SQL, the `ROUND` function instead always rounds away from 0.</span></span> <span data-ttu-id="5ac13-110">Portanto círculos 2,5 a 3, contrastado com o arredondamento para 2 no.NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5ac13-110">Therefore 2.5 rounds to 3, contrasted with its rounding to 2 in the .NET Framework.</span></span>  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="5ac13-111"> passa completamente a semântica do SQL `ROUND` e não tenta implementar arredondamento bancário.</span><span class="sxs-lookup"><span data-stu-id="5ac13-111"> passes through to the SQL `ROUND` semantics and does not try to implement Banker's rounding.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ac13-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5ac13-112">See Also</span></span>  
 [<span data-ttu-id="5ac13-113">Funções e tipos de dados</span><span class="sxs-lookup"><span data-stu-id="5ac13-113">Data Types and Functions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)
