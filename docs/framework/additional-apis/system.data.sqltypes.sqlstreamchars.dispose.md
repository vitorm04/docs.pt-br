---
title: Método SqlStreamChars. Dispose (booliano) (System. Data. SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/20/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.Dispose
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: 44dc97835b8a7141064e8de4d2d5325c40be5a34
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395762"
---
# <a name="sqlstreamcharsdisposeboolean-method"></a><span data-ttu-id="7a90b-102">Método SqlStreamChars. Dispose (booliano)</span><span class="sxs-lookup"><span data-stu-id="7a90b-102">SqlStreamChars.Dispose(Boolean) Method</span></span>

<span data-ttu-id="7a90b-103">Quando substituído em uma classe derivada, libera os recursos usados pelo fluxo.</span><span class="sxs-lookup"><span data-stu-id="7a90b-103">When overridden in a derived class, releases the resources used by the stream.</span></span> <span data-ttu-id="7a90b-104">O assembly que contém esse método tem uma relação Friend com SQLAccess. dll.</span><span class="sxs-lookup"><span data-stu-id="7a90b-104">The assembly that contains this method has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="7a90b-105">Ele é destinado ao uso por SQL Server.</span><span class="sxs-lookup"><span data-stu-id="7a90b-105">It's intended for use by SQL Server.</span></span> <span data-ttu-id="7a90b-106">Para outros bancos de dados, use o mecanismo de hospedagem fornecido por esse banco.</span><span class="sxs-lookup"><span data-stu-id="7a90b-106">For other databases, use the hosting mechanism provided by that database.</span></span>

```csharp
protected virtual void Dispose (bool disposing);
```

## <a name="parameters"></a><span data-ttu-id="7a90b-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7a90b-107">Parameters</span></span>

`disposing`\
<span data-ttu-id="7a90b-108">`true` para liberar recursos gerenciados e não gerenciados; `false` para liberar apenas recursos não gerenciados.</span><span class="sxs-lookup"><span data-stu-id="7a90b-108">`true` to release both managed and unmanaged resources; `false` to release only unmanaged resources.</span></span>

## <a name="remarks"></a><span data-ttu-id="7a90b-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="7a90b-109">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="7a90b-110">O método `SqlStreamChars.Dispose` é privado e não se destina a ser usado diretamente no seu código.</span><span class="sxs-lookup"><span data-stu-id="7a90b-110">The `SqlStreamChars.Dispose` method is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="7a90b-111">A Microsoft não oferece suporte ao uso desse método em um aplicativo de produção em qualquer circunstância.</span><span class="sxs-lookup"><span data-stu-id="7a90b-111">Microsoft does not support the use of this method in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="7a90b-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7a90b-112">Requirements</span></span>

<span data-ttu-id="7a90b-113">**Namespace:** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="7a90b-113">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="7a90b-114">**Assembly:** System. Data (em System. Data. dll)</span><span class="sxs-lookup"><span data-stu-id="7a90b-114">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="7a90b-115">**.NET Framework versões:** Disponível desde 2,0.</span><span class="sxs-lookup"><span data-stu-id="7a90b-115">**.NET Framework versions:** Available since 2.0.</span></span>
