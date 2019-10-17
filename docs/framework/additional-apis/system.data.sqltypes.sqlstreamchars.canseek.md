---
title: Propriedade SqlStreamChars. CanSeek (System. Data. SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/19/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.CanSeek
- System.Data.SqlTypes.SqlStreamChars.get_CanSeek
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: eb32978f62b7d46f0abf715e2bca347592c0fda8
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395775"
---
# <a name="sqlstreamcharscanseek-property"></a><span data-ttu-id="4a0c4-102">Propriedade SqlStreamChars. CanSeek</span><span class="sxs-lookup"><span data-stu-id="4a0c4-102">SqlStreamChars.CanSeek Property</span></span>

<span data-ttu-id="4a0c4-103">Quando substituído em uma classe derivada, obtém um valor que indica se o fluxo atual dá suporte à operação de busca.</span><span class="sxs-lookup"><span data-stu-id="4a0c4-103">When overridden in a derived class, gets a value that indicates whether the current steam supports the seek operation.</span></span> <span data-ttu-id="4a0c4-104">O assembly que contém essa propriedade tem uma relação Friend com SQLAccess. dll.</span><span class="sxs-lookup"><span data-stu-id="4a0c4-104">The assembly that contains this property has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="4a0c4-105">Ele é destinado ao uso por SQL Server.</span><span class="sxs-lookup"><span data-stu-id="4a0c4-105">It's intended for use by SQL Server.</span></span> <span data-ttu-id="4a0c4-106">Para outros bancos de dados, use o mecanismo de hospedagem fornecido por esse banco.</span><span class="sxs-lookup"><span data-stu-id="4a0c4-106">For other databases, use the hosting mechanism provided by that database.</span></span>

```csharp
public abstract bool CanSeek { get; }
```

## <a name="property-value"></a><span data-ttu-id="4a0c4-107">Valor da propriedade</span><span class="sxs-lookup"><span data-stu-id="4a0c4-107">Property value</span></span>

<xref:System.Boolean>\
<span data-ttu-id="4a0c4-108">`true` se o fluxo atual der suporte à operação de busca; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="4a0c4-108">`true` if the current steam supports the seek operation; otherwise, `false`.</span></span>

## <a name="remarks"></a><span data-ttu-id="4a0c4-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="4a0c4-109">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="4a0c4-110">A propriedade `SqlStreamChars.CanSeek` é privada e não se destina a ser usada diretamente no seu código.</span><span class="sxs-lookup"><span data-stu-id="4a0c4-110">The `SqlStreamChars.CanSeek` property is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="4a0c4-111">A Microsoft não oferece suporte ao uso dessa propriedade em um aplicativo de produção em nenhuma circunstância.</span><span class="sxs-lookup"><span data-stu-id="4a0c4-111">Microsoft does not support the use of this property in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="4a0c4-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4a0c4-112">Requirements</span></span>

<span data-ttu-id="4a0c4-113">**Namespace:** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="4a0c4-113">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="4a0c4-114">**Assembly:** System. Data (em System. Data. dll)</span><span class="sxs-lookup"><span data-stu-id="4a0c4-114">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="4a0c4-115">**.NET Framework versões:** Disponível desde 2,0.</span><span class="sxs-lookup"><span data-stu-id="4a0c4-115">**.NET Framework versions:** Available since 2.0.</span></span>
