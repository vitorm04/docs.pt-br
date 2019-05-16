---
title: Método SqlStreamChars.Dispose(Boolean) (SqlTypes)
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
ms.openlocfilehash: 2cad6015c1c4d72300d8413b7accead12f79a0be
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65634310"
---
# <a name="sqlstreamcharsdisposeboolean-method"></a><span data-ttu-id="e44a6-102">Método SqlStreamChars.Dispose(Boolean)</span><span class="sxs-lookup"><span data-stu-id="e44a6-102">SqlStreamChars.Dispose(Boolean) Method</span></span>

<span data-ttu-id="e44a6-103">Quando substituído em uma classe derivada, libera os recursos usados pelo fluxo.</span><span class="sxs-lookup"><span data-stu-id="e44a6-103">When overridden in a derived class, releases the resources used by the stream.</span></span> <span data-ttu-id="e44a6-104">O assembly que contém este método tem uma relação de amigo com SQLAccess.dll.</span><span class="sxs-lookup"><span data-stu-id="e44a6-104">The assembly that contains this method has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="e44a6-105">Ele é destinado a uso pelo SQL Server.</span><span class="sxs-lookup"><span data-stu-id="e44a6-105">It's intended for use by SQL Server.</span></span> <span data-ttu-id="e44a6-106">Para outros bancos de dados, use o mecanismo de hospedagem fornecido pelo banco de dados.</span><span class="sxs-lookup"><span data-stu-id="e44a6-106">For other databases, use the hosting mechanism provided by that database.</span></span>

```csharp
protected virtual void Dispose (bool disposing);
```

## <a name="parameters"></a><span data-ttu-id="e44a6-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e44a6-107">Parameters</span></span>

`disposing`\
<span data-ttu-id="e44a6-108">`true` para liberar recursos gerenciados e não gerenciados; `false` para liberar apenas recursos não gerenciados.</span><span class="sxs-lookup"><span data-stu-id="e44a6-108">`true` to release both managed and unmanaged resources; `false` to release only unmanaged resources.</span></span>

## <a name="remarks"></a><span data-ttu-id="e44a6-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="e44a6-109">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="e44a6-110">O `SqlStreamChars.Dispose` método é privado e não se destina a ser usado diretamente em seu código.</span><span class="sxs-lookup"><span data-stu-id="e44a6-110">The `SqlStreamChars.Dispose` method is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="e44a6-111">Microsoft não suporta o uso deste campo em um aplicativo de produção sob nenhuma circunstância.</span><span class="sxs-lookup"><span data-stu-id="e44a6-111">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="e44a6-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e44a6-112">Requirements</span></span>

<span data-ttu-id="e44a6-113">**Namespace:** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="e44a6-113">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="e44a6-114">**Assembly:** System. Data (em dll)</span><span class="sxs-lookup"><span data-stu-id="e44a6-114">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="e44a6-115">**Versões do .NET framework:** Disponível desde o 2.0.</span><span class="sxs-lookup"><span data-stu-id="e44a6-115">**.NET Framework versions:** Available since 2.0.</span></span>
