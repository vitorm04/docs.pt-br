---
title: Métodos de System.Math
ms.date: 03/30/2017
ms.assetid: 0f299521-6f41-4720-bd70-67c93fc50948
ms.openlocfilehash: 1dae31b30962505c07c198f3bd35fceb8f400efb
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59141707"
---
# <a name="systemmath-methods"></a><span data-ttu-id="e75eb-102">Métodos de System.Math</span><span class="sxs-lookup"><span data-stu-id="e75eb-102">System.Math Methods</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="e75eb-103">não suporta o seguinte <xref:System.Math> métodos.</span><span class="sxs-lookup"><span data-stu-id="e75eb-103">does not support the following <xref:System.Math> methods.</span></span>  
  
-   <xref:System.Math.DivRem%28System.Int32%2CSystem.Int32%2CSystem.Int32%40%29?displayProperty=nameWithType>  
  
-   <xref:System.Math.DivRem%28System.Int64%2CSystem.Int64%2CSystem.Int64%40%29?displayProperty=nameWithType>  
  
-   <xref:System.Math.IEEERemainder%28System.Double%2CSystem.Double%29?displayProperty=nameWithType>  
  
## <a name="differences-from-net"></a><span data-ttu-id="e75eb-104">Diferenças do .NET</span><span class="sxs-lookup"><span data-stu-id="e75eb-104">Differences from .NET</span></span>  
 <span data-ttu-id="e75eb-105">O.NET Framework tem a semântica por arredondamento diferente do SQL Server.</span><span class="sxs-lookup"><span data-stu-id="e75eb-105">The .NET Framework has different rounding semantics from SQL Server.</span></span> <span data-ttu-id="e75eb-106">O <xref:System.Math.Round%2A> método no .NET Framework realiza *arredondamento bancário*, onde os números que terminam em. 5 são arredondados para o dígito em vez de para o dígito mais próximo mais próximo.</span><span class="sxs-lookup"><span data-stu-id="e75eb-106">The <xref:System.Math.Round%2A> method in the .NET Framework performs *Banker's rounding*, where numbers that ends in .5 round to the nearest even digit instead of to the next higher digit.</span></span> <span data-ttu-id="e75eb-107">Por exemplo, círculos 2,5 a 2, quando círculos 3,5 a 4.</span><span class="sxs-lookup"><span data-stu-id="e75eb-107">For example, 2.5 rounds to 2, while 3.5 rounds to 4.</span></span> <span data-ttu-id="e75eb-108">(Essa técnica ajuda a evitar a polarização sistemática para os valores mais altos em grandes transações de dados.)</span><span class="sxs-lookup"><span data-stu-id="e75eb-108">(This technique helps avoid systematic bias toward higher values in large data transactions.)</span></span>  
  
 <span data-ttu-id="e75eb-109">Em SQL, a função de `ROUND` vez arredondará sempre fora de 0.</span><span class="sxs-lookup"><span data-stu-id="e75eb-109">In SQL, the `ROUND` function instead always rounds away from 0.</span></span> <span data-ttu-id="e75eb-110">Portanto círculos 2,5 a 3, contrastado com o arredondamento para 2 no.NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e75eb-110">Therefore 2.5 rounds to 3, contrasted with its rounding to 2 in the .NET Framework.</span></span>  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="e75eb-111">passa para o SQL `ROUND` semântica e não tenta implementar arredondamento bancário.</span><span class="sxs-lookup"><span data-stu-id="e75eb-111">passes through to the SQL `ROUND` semantics and does not try to implement Banker's rounding.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e75eb-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e75eb-112">See also</span></span>

- [<span data-ttu-id="e75eb-113">Tipos de dados e funções</span><span class="sxs-lookup"><span data-stu-id="e75eb-113">Data Types and Functions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)
