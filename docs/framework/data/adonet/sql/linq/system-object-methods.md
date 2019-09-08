---
title: Métodos de System.Object
ms.date: 03/30/2017
ms.assetid: 5397fca0-689e-443e-802f-e1cbdc866427
ms.openlocfilehash: d1a36798ef789bbc44f581dfc631feee19e1f66b
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781068"
---
# <a name="systemobject-methods"></a><span data-ttu-id="66551-102">Métodos de System.Object</span><span class="sxs-lookup"><span data-stu-id="66551-102">System.Object Methods</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="66551-103">o oferece suporte <xref:System.Object> aos seguintes métodos.</span><span class="sxs-lookup"><span data-stu-id="66551-103">supports the following <xref:System.Object> methods.</span></span>  
  
|||  
|-|-|  
|<xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType>|<xref:System.Object.Equals%28System.Object%2CSystem.Object%29?displayProperty=nameWithType>|  
|<xref:System.Object.ToString?displayProperty=nameWithType>||  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="66551-104">não oferece suporte aos seguintes métodos de <xref:System.Object> .</span><span class="sxs-lookup"><span data-stu-id="66551-104">does not support the following <xref:System.Object> methods.</span></span>  
  
|||  
|-|-|  
|<xref:System.Object.GetHashCode?displayProperty=nameWithType>|<xref:System.Object.ReferenceEquals%28System.Object%2CSystem.Object%29?displayProperty=nameWithType>|  
|<xref:System.Object.MemberwiseClone?displayProperty=nameWithType>|<xref:System.Object.GetType?displayProperty=nameWithType>|  
|<span data-ttu-id="66551-105"><xref:System.Object.ToString?displayProperty=nameWithType> para tipos binários como `BINARY`, `VARBINARY`, `IMAGE`, e `TIMESTAMP`.</span><span class="sxs-lookup"><span data-stu-id="66551-105"><xref:System.Object.ToString?displayProperty=nameWithType> for binary types such as `BINARY`, `VARBINARY`, `IMAGE`, and `TIMESTAMP`.</span></span>||  
  
## <a name="differences-from-net"></a><span data-ttu-id="66551-106">Diferenças do .NET</span><span class="sxs-lookup"><span data-stu-id="66551-106">Differences from .NET</span></span>  
 <span data-ttu-id="66551-107">A saída de <xref:System.Object.ToString?displayProperty=nameWithType> for Double usa SQL `CONVERT`(nvarchar (30), @x, 2) no SQL.</span><span class="sxs-lookup"><span data-stu-id="66551-107">The output of <xref:System.Object.ToString?displayProperty=nameWithType> for double uses SQL `CONVERT`(NVARCHAR(30), @x, 2) on SQL.</span></span> <span data-ttu-id="66551-108">O SQL usa sempre 16 dígitos e notação científica nesse caso (por exemplo, “0.000000000000000e+000” para 0).</span><span class="sxs-lookup"><span data-stu-id="66551-108">SQL always uses 16 digits and scientific notation in this case (for example, "0.000000000000000e+000" for 0).</span></span> <span data-ttu-id="66551-109">Como resultado, a conversão de <xref:System.Object.ToString?displayProperty=nameWithType> não gerencia a mesma cadeia de caracteres que <xref:System.Convert.ToString%2A?displayProperty=nameWithType> no.NET Framework.</span><span class="sxs-lookup"><span data-stu-id="66551-109">As a result, <xref:System.Object.ToString?displayProperty=nameWithType> conversion does not produce the same string as <xref:System.Convert.ToString%2A?displayProperty=nameWithType> in the .NET Framework.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66551-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="66551-110">See also</span></span>

- [<span data-ttu-id="66551-111">Funções e tipos de dados</span><span class="sxs-lookup"><span data-stu-id="66551-111">Data Types and Functions</span></span>](data-types-and-functions.md)
