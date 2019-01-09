---
title: Propriedade SqlStreamChars.CanSeek (SqlTypes)
author: douglaslMS
ms.author: douglasl
ms.date: 12/19/2018
ms.technology:
- dotnet-data
api_name:
- System.Data.SqlTypes.SqlStreamChars.CanSeek
- System.Data.SqlTypes.SqlStreamChars.get_CanSeek
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: 0145fe87e2c8aa3dd40e73f0089fe40b6b6cca30
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54152729"
---
# <a name="sqlstreamcharscanseek-property"></a><span data-ttu-id="bed00-102">Propriedade SqlStreamChars.CanSeek</span><span class="sxs-lookup"><span data-stu-id="bed00-102">SqlStreamChars.CanSeek Property</span></span>

<span data-ttu-id="bed00-103">Quando substituído em uma classe derivada, obtém um valor que indica se o fluxo atual dá suporte à operação de busca.</span><span class="sxs-lookup"><span data-stu-id="bed00-103">When overridden in a derived class, gets a value that indicates whether the current steam supports the seek operation.</span></span> <span data-ttu-id="bed00-104">O assembly que contém essa propriedade tem uma relação de amigo com SQLAccess.dll.</span><span class="sxs-lookup"><span data-stu-id="bed00-104">The assembly that contains this property has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="bed00-105">Ele é destinado a uso pelo SQL Server.</span><span class="sxs-lookup"><span data-stu-id="bed00-105">It's intended for use by SQL Server.</span></span> <span data-ttu-id="bed00-106">Para outros bancos de dados, use o mecanismo de hospedagem fornecido pelo banco de dados.</span><span class="sxs-lookup"><span data-stu-id="bed00-106">For other databases, use the hosting mechanism provided by that database.</span></span>

```csharp
public abstract bool CanSeek { get; }
```

## <a name="property-value"></a><span data-ttu-id="bed00-107">Valor da propriedade</span><span class="sxs-lookup"><span data-stu-id="bed00-107">Property value</span></span>

<xref:System.Boolean>\
<span data-ttu-id="bed00-108">`true` Se o fluxo atual dá suporte à operação de busca; Caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="bed00-108">`true` if the current steam supports the seek operation; otherwise, `false`.</span></span>

## <a name="remarks"></a><span data-ttu-id="bed00-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="bed00-109">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="bed00-110">O `SqlStreamChars.CanSeek` propriedade é privada e não se destina a ser usado diretamente em seu código.</span><span class="sxs-lookup"><span data-stu-id="bed00-110">The `SqlStreamChars.CanSeek` property is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="bed00-111">Microsoft não suporta o uso deste campo em um aplicativo de produção sob nenhuma circunstância.</span><span class="sxs-lookup"><span data-stu-id="bed00-111">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="bed00-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="bed00-112">Requirements</span></span>

<span data-ttu-id="bed00-113">**Namespace:** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="bed00-113">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="bed00-114">**Assembly:** System. Data (em dll)</span><span class="sxs-lookup"><span data-stu-id="bed00-114">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="bed00-115">**Versões do .NET framework:** Disponível desde o 2.0.</span><span class="sxs-lookup"><span data-stu-id="bed00-115">**.NET Framework versions:** Available since 2.0.</span></span>