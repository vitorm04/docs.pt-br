---
title: Método SqlStreamChars.Flush (SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/20/2018
ms.technology:
- dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.Flush
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: 6de892572691a016b7bb0eb2a28c0163380bcd03
ms.sourcegitcommit: 3500c4845f96a91a438a02ef2c6b4eef45a5e2af
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/07/2019
ms.locfileid: "55827696"
---
# <a name="sqlstreamcharsflush-method"></a><span data-ttu-id="e993c-102">Método SqlStreamChars.Flush</span><span class="sxs-lookup"><span data-stu-id="e993c-102">SqlStreamChars.Flush Method</span></span>

<span data-ttu-id="e993c-103">Quando é substituído em uma classe derivada, limpa todos os buffers nesse fluxo e faz com que todos os dados armazenados em buffer sejam gravados no dispositivo subjacente.</span><span class="sxs-lookup"><span data-stu-id="e993c-103">When overridden in a derived class, clears all buffers for this stream and causes any buffered data to be written to the underlying device.</span></span> <span data-ttu-id="e993c-104">O assembly que contém este método tem uma relação de amigo com SQLAccess.dll.</span><span class="sxs-lookup"><span data-stu-id="e993c-104">The assembly that contains this method has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="e993c-105">Ele é destinado a uso pelo SQL Server.</span><span class="sxs-lookup"><span data-stu-id="e993c-105">It's intended for use by SQL Server.</span></span> <span data-ttu-id="e993c-106">Para outros bancos de dados, use o mecanismo de hospedagem fornecido pelo banco de dados.</span><span class="sxs-lookup"><span data-stu-id="e993c-106">For other databases, use the hosting mechanism provided by that database.</span></span>

## <a name="syntax"></a><span data-ttu-id="e993c-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e993c-107">Syntax</span></span>

```csharp
public abstract void Flush ();
```

## <a name="remarks"></a><span data-ttu-id="e993c-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="e993c-108">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="e993c-109">O `SqlStreamChars.Flush` método é privado e não se destina a ser usado diretamente em seu código.</span><span class="sxs-lookup"><span data-stu-id="e993c-109">The `SqlStreamChars.Flush` method is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="e993c-110">Microsoft não suporta o uso deste campo em um aplicativo de produção sob nenhuma circunstância.</span><span class="sxs-lookup"><span data-stu-id="e993c-110">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="e993c-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e993c-111">Requirements</span></span>

<span data-ttu-id="e993c-112">**Namespace:** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="e993c-112">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="e993c-113">**Assembly:** System. Data (em dll)</span><span class="sxs-lookup"><span data-stu-id="e993c-113">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="e993c-114">**Versões do .NET framework:** Disponível desde o 2.0.</span><span class="sxs-lookup"><span data-stu-id="e993c-114">**.NET Framework versions:** Available since 2.0.</span></span>