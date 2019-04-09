---
title: Métodos de System.Convert
ms.date: 03/30/2017
ms.assetid: 3ca6c5b6-ea5d-4ab0-b675-f082135b342c
ms.openlocfilehash: 0d98d159c24e1a47723aeb07a9654fe22b1d9464
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59198212"
---
# <a name="systemconvert-methods"></a><span data-ttu-id="558bd-102">Métodos de System.Convert</span><span class="sxs-lookup"><span data-stu-id="558bd-102">System.Convert Methods</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="558bd-103">não suporta o seguinte <xref:System.Convert> métodos.</span><span class="sxs-lookup"><span data-stu-id="558bd-103">does not support the following <xref:System.Convert> methods.</span></span>  
  
-   <span data-ttu-id="558bd-104">Versões com um parâmetro de <xref:System.IFormatProvider> .</span><span class="sxs-lookup"><span data-stu-id="558bd-104">Versions with an <xref:System.IFormatProvider> parameter.</span></span>  
  
-   <span data-ttu-id="558bd-105">Métodos que envolvem matrizes de char ou matrizes de bytes:</span><span class="sxs-lookup"><span data-stu-id="558bd-105">Methods that involve char arrays or byte arrays:</span></span>  
  
    -   <xref:System.Convert.FromBase64CharArray%2A>  
  
    -   <xref:System.Convert.ToBase64CharArray%2A>  
  
    -   <xref:System.Convert.FromBase64String%2A>  
  
    -   <xref:System.Convert.ToBase64String%2A>  
  
-   <span data-ttu-id="558bd-106">Os seguintes métodos:</span><span class="sxs-lookup"><span data-stu-id="558bd-106">The following methods:</span></span>  
  
    -   `public static <Type2> To<Type2>(<Type1> value);` <span data-ttu-id="558bd-107">onde</span><span class="sxs-lookup"><span data-stu-id="558bd-107">where</span></span>  
  
         `Type1` <span data-ttu-id="558bd-108">e `Type2` são cada um dos `sbyte`, `uint`, `ulong`, ou `ushort`.</span><span class="sxs-lookup"><span data-stu-id="558bd-108">and `Type2` are each one of `sbyte`, `uint`, `ulong`, or `ushort`.</span></span>  
  
    -   <span data-ttu-id="558bd-109">C#:</span><span class="sxs-lookup"><span data-stu-id="558bd-109">C#:</span></span>  
  
         `int To<int type>(string value, int fromBase),`  
  
         `ToString(... value, int toBase)`  
  
    -   <span data-ttu-id="558bd-110">Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="558bd-110">Visual Basic:</span></span>  
  
         `Function To(Of [Numeric])(value as String, fromBase As Integer)`  
  
         `As [Numeric], ToString( value As …, toBase As Integer)`  
  
    -   <xref:System.Convert.IsDBNull%2A>  
  
    -   <xref:System.Convert.GetTypeCode%2A>  
  
    -   <xref:System.Convert.ChangeType%2A>  
  
## <a name="see-also"></a><span data-ttu-id="558bd-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="558bd-111">See also</span></span>

- [<span data-ttu-id="558bd-112">Tipos de dados e funções</span><span class="sxs-lookup"><span data-stu-id="558bd-112">Data Types and Functions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)
