---
title: Método SqlStreamChars.Dispose(Boolean) (SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/20/2018
ms.technology:
- dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.Dispose
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: 4e6cfd6d4c04b1a2835b6e34b82c95b564dea588
ms.sourcegitcommit: 3500c4845f96a91a438a02ef2c6b4eef45a5e2af
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/07/2019
ms.locfileid: "55826857"
---
# <a name="sqlstreamcharsdisposeboolean-method"></a><span data-ttu-id="8b30e-102">Método SqlStreamChars.Dispose(Boolean)</span><span class="sxs-lookup"><span data-stu-id="8b30e-102">SqlStreamChars.Dispose(Boolean) Method</span></span>

<span data-ttu-id="8b30e-103">Quando substituído em uma classe derivada, libera os recursos usados pelo fluxo.</span><span class="sxs-lookup"><span data-stu-id="8b30e-103">When overridden in a derived class, releases the resources used by the stream.</span></span> <span data-ttu-id="8b30e-104">O assembly que contém este método tem uma relação de amigo com SQLAccess.dll.</span><span class="sxs-lookup"><span data-stu-id="8b30e-104">The assembly that contains this method has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="8b30e-105">Ele é destinado a uso pelo SQL Server.</span><span class="sxs-lookup"><span data-stu-id="8b30e-105">It's intended for use by SQL Server.</span></span> <span data-ttu-id="8b30e-106">Para outros bancos de dados, use o mecanismo de hospedagem fornecido pelo banco de dados.</span><span class="sxs-lookup"><span data-stu-id="8b30e-106">For other databases, use the hosting mechanism provided by that database.</span></span>

```csharp
protected virtual void Dispose (bool disposing);
```

## <a name="parameters"></a><span data-ttu-id="8b30e-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8b30e-107">Parameters</span></span>

`disposing`\
<span data-ttu-id="8b30e-108">`true` para liberar recursos gerenciados e não gerenciados; `false` para liberar apenas recursos não gerenciados.</span><span class="sxs-lookup"><span data-stu-id="8b30e-108">`true` to release both managed and unmanaged resources; `false` to release only unmanaged resources.</span></span>

## <a name="remarks"></a><span data-ttu-id="8b30e-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="8b30e-109">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="8b30e-110">O `SqlStreamChars.Dispose` método é privado e não se destina a ser usado diretamente em seu código.</span><span class="sxs-lookup"><span data-stu-id="8b30e-110">The `SqlStreamChars.Dispose` method is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="8b30e-111">Microsoft não suporta o uso deste campo em um aplicativo de produção sob nenhuma circunstância.</span><span class="sxs-lookup"><span data-stu-id="8b30e-111">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="8b30e-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8b30e-112">Requirements</span></span>

<span data-ttu-id="8b30e-113">**Namespace:** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="8b30e-113">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="8b30e-114">**Assembly:** System. Data (em dll)</span><span class="sxs-lookup"><span data-stu-id="8b30e-114">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="8b30e-115">**Versões do .NET framework:** Disponível desde o 2.0.</span><span class="sxs-lookup"><span data-stu-id="8b30e-115">**.NET Framework versions:** Available since 2.0.</span></span>