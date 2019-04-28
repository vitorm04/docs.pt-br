---
title: Métodos de System.Convert
ms.date: 03/30/2017
ms.assetid: 3ca6c5b6-ea5d-4ab0-b675-f082135b342c
ms.openlocfilehash: 9836820f2c084a80fcc0a4856f20597716344dfd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61877026"
---
# <a name="systemconvert-methods"></a><span data-ttu-id="7f1d6-102">Métodos de System.Convert</span><span class="sxs-lookup"><span data-stu-id="7f1d6-102">System.Convert Methods</span></span>

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="7f1d6-103">não oferece suporte aos seguintes métodos de <xref:System.Convert> .</span><span class="sxs-lookup"><span data-stu-id="7f1d6-103">does not support the following <xref:System.Convert> methods.</span></span>

- <span data-ttu-id="7f1d6-104">Versões com um parâmetro de <xref:System.IFormatProvider> .</span><span class="sxs-lookup"><span data-stu-id="7f1d6-104">Versions with an <xref:System.IFormatProvider> parameter.</span></span>

- <span data-ttu-id="7f1d6-105">Métodos que envolvem matrizes de char ou matrizes de bytes:</span><span class="sxs-lookup"><span data-stu-id="7f1d6-105">Methods that involve char arrays or byte arrays:</span></span>

  - <xref:System.Convert.FromBase64CharArray%2A>

  - <xref:System.Convert.ToBase64CharArray%2A>

  - <xref:System.Convert.FromBase64String%2A>

  - <xref:System.Convert.ToBase64String%2A>

- <span data-ttu-id="7f1d6-106">Os seguintes métodos:</span><span class="sxs-lookup"><span data-stu-id="7f1d6-106">The following methods:</span></span>

  - <span data-ttu-id="7f1d6-107">`public static <Type2> To<Type2>(<Type1> value);` onde</span><span class="sxs-lookup"><span data-stu-id="7f1d6-107">`public static <Type2> To<Type2>(<Type1> value);` where</span></span>

    <span data-ttu-id="7f1d6-108">`Type1` e `Type2` são cada um de `sbyte`, `uint`, `ulong`, ou `ushort`.</span><span class="sxs-lookup"><span data-stu-id="7f1d6-108">`Type1` and `Type2` are each one of `sbyte`, `uint`, `ulong`, or `ushort`.</span></span>

  - <span data-ttu-id="7f1d6-109">C#:</span><span class="sxs-lookup"><span data-stu-id="7f1d6-109">C#:</span></span>

    `int To<int type>(string value, int fromBase),`

    `ToString(... value, int toBase)`

  - <span data-ttu-id="7f1d6-110">Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="7f1d6-110">Visual Basic:</span></span>

    `Function To(Of [Numeric])(value as String, fromBase As Integer)`

    `As [Numeric], ToString( value As …, toBase As Integer)`

  - <xref:System.Convert.IsDBNull%2A>

  - <xref:System.Convert.GetTypeCode%2A>

  - <xref:System.Convert.ChangeType%2A>

## <a name="see-also"></a><span data-ttu-id="7f1d6-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7f1d6-111">See also</span></span>

- [<span data-ttu-id="7f1d6-112">Funções e tipos de dados</span><span class="sxs-lookup"><span data-stu-id="7f1d6-112">Data Types and Functions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)
