---
title: Método SqlStreamChars. Flush (System. Data. SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/20/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.Flush
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: 38ade5ce38cfe5003b2d06c0d8bb2db1a20bc05b
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395619"
---
# <a name="sqlstreamcharsflush-method"></a><span data-ttu-id="13ccc-102">Método SqlStreamChars. Flush</span><span class="sxs-lookup"><span data-stu-id="13ccc-102">SqlStreamChars.Flush Method</span></span>

<span data-ttu-id="13ccc-103">Quando é substituído em uma classe derivada, limpa todos os buffers nesse fluxo e faz com que todos os dados armazenados em buffer sejam gravados no dispositivo subjacente.</span><span class="sxs-lookup"><span data-stu-id="13ccc-103">When overridden in a derived class, clears all buffers for this stream and causes any buffered data to be written to the underlying device.</span></span> <span data-ttu-id="13ccc-104">O assembly que contém esse método tem uma relação Friend com SQLAccess. dll.</span><span class="sxs-lookup"><span data-stu-id="13ccc-104">The assembly that contains this method has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="13ccc-105">Ele é destinado ao uso por SQL Server.</span><span class="sxs-lookup"><span data-stu-id="13ccc-105">It's intended for use by SQL Server.</span></span> <span data-ttu-id="13ccc-106">Para outros bancos de dados, use o mecanismo de hospedagem fornecido por esse banco.</span><span class="sxs-lookup"><span data-stu-id="13ccc-106">For other databases, use the hosting mechanism provided by that database.</span></span>

## <a name="syntax"></a><span data-ttu-id="13ccc-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="13ccc-107">Syntax</span></span>

```csharp
public abstract void Flush ();
```

## <a name="remarks"></a><span data-ttu-id="13ccc-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="13ccc-108">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="13ccc-109">O método `SqlStreamChars.Flush` é privado e não se destina a ser usado diretamente no seu código.</span><span class="sxs-lookup"><span data-stu-id="13ccc-109">The `SqlStreamChars.Flush` method is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="13ccc-110">A Microsoft não oferece suporte ao uso desse método em um aplicativo de produção em qualquer circunstância.</span><span class="sxs-lookup"><span data-stu-id="13ccc-110">Microsoft does not support the use of this method in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="13ccc-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="13ccc-111">Requirements</span></span>

<span data-ttu-id="13ccc-112">**Namespace:** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="13ccc-112">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="13ccc-113">**Assembly:** System. Data (em System. Data. dll)</span><span class="sxs-lookup"><span data-stu-id="13ccc-113">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="13ccc-114">**.NET Framework versões:** Disponível desde 2,0.</span><span class="sxs-lookup"><span data-stu-id="13ccc-114">**.NET Framework versions:** Available since 2.0.</span></span>
