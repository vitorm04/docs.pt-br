---
title: Propriedade SqlStreamChars.CanSeek (SqlTypes)
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
ms.openlocfilehash: b85e21c6bc89d2a00ff8d302f67a3d074d5e7b8f
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65634381"
---
# <a name="sqlstreamcharscanseek-property"></a><span data-ttu-id="741dc-102">Propriedade SqlStreamChars.CanSeek</span><span class="sxs-lookup"><span data-stu-id="741dc-102">SqlStreamChars.CanSeek Property</span></span>

<span data-ttu-id="741dc-103">Quando substituído em uma classe derivada, obtém um valor que indica se o fluxo atual dá suporte à operação de busca.</span><span class="sxs-lookup"><span data-stu-id="741dc-103">When overridden in a derived class, gets a value that indicates whether the current steam supports the seek operation.</span></span> <span data-ttu-id="741dc-104">O assembly que contém essa propriedade tem uma relação de amigo com SQLAccess.dll.</span><span class="sxs-lookup"><span data-stu-id="741dc-104">The assembly that contains this property has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="741dc-105">Ele é destinado a uso pelo SQL Server.</span><span class="sxs-lookup"><span data-stu-id="741dc-105">It's intended for use by SQL Server.</span></span> <span data-ttu-id="741dc-106">Para outros bancos de dados, use o mecanismo de hospedagem fornecido pelo banco de dados.</span><span class="sxs-lookup"><span data-stu-id="741dc-106">For other databases, use the hosting mechanism provided by that database.</span></span>

```csharp
public abstract bool CanSeek { get; }
```

## <a name="property-value"></a><span data-ttu-id="741dc-107">Valor da propriedade</span><span class="sxs-lookup"><span data-stu-id="741dc-107">Property value</span></span>

<xref:System.Boolean>\
<span data-ttu-id="741dc-108">`true` Se o fluxo atual dá suporte à operação de busca; Caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="741dc-108">`true` if the current steam supports the seek operation; otherwise, `false`.</span></span>

## <a name="remarks"></a><span data-ttu-id="741dc-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="741dc-109">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="741dc-110">O `SqlStreamChars.CanSeek` propriedade é privada e não se destina a ser usado diretamente em seu código.</span><span class="sxs-lookup"><span data-stu-id="741dc-110">The `SqlStreamChars.CanSeek` property is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="741dc-111">Microsoft não suporta o uso deste campo em um aplicativo de produção sob nenhuma circunstância.</span><span class="sxs-lookup"><span data-stu-id="741dc-111">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="741dc-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="741dc-112">Requirements</span></span>

<span data-ttu-id="741dc-113">**Namespace:** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="741dc-113">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="741dc-114">**Assembly:** System. Data (em dll)</span><span class="sxs-lookup"><span data-stu-id="741dc-114">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="741dc-115">**Versões do .NET framework:** Disponível desde o 2.0.</span><span class="sxs-lookup"><span data-stu-id="741dc-115">**.NET Framework versions:** Available since 2.0.</span></span>
