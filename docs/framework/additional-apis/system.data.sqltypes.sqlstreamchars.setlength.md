---
title: Método SqlStreamChars. SetLength (Int64) (System. Data. SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/20/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.SetLength
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: 291d6e9395581f2370dafc728521a314d54a686d
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395718"
---
# <a name="sqlstreamcharssetlengthint64-method"></a><span data-ttu-id="e7129-102">Método SqlStreamChars. SetLength (Int64)</span><span class="sxs-lookup"><span data-stu-id="e7129-102">SqlStreamChars.SetLength(Int64) Method</span></span>

<span data-ttu-id="e7129-103">Quando substituído em uma classe derivada, libera os recursos usados pelo fluxo.</span><span class="sxs-lookup"><span data-stu-id="e7129-103">When overridden in a derived class, releases the resources used by the stream.</span></span> <span data-ttu-id="e7129-104">O assembly que contém esse método tem uma relação Friend com SQLAccess. dll.</span><span class="sxs-lookup"><span data-stu-id="e7129-104">The assembly that contains this method has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="e7129-105">Ele é destinado ao uso por SQL Server.</span><span class="sxs-lookup"><span data-stu-id="e7129-105">It's intended for use by SQL Server.</span></span> <span data-ttu-id="e7129-106">Para outros bancos de dados, use o mecanismo de hospedagem fornecido por esse banco.</span><span class="sxs-lookup"><span data-stu-id="e7129-106">For other databases, use the hosting mechanism provided by that database.</span></span>

```csharp
public abstract void SetLength (long value);
```

## <a name="parameters"></a><span data-ttu-id="e7129-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e7129-107">Parameters</span></span>

`value`\
<span data-ttu-id="e7129-108">O tamanho desejado do fluxo atual em bytes.</span><span class="sxs-lookup"><span data-stu-id="e7129-108">The desired length of the current stream in bytes.</span></span>

## <a name="remarks"></a><span data-ttu-id="e7129-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="e7129-109">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="e7129-110">O método `SqlStreamChars.SetLength` é privado e não se destina a ser usado diretamente no seu código.</span><span class="sxs-lookup"><span data-stu-id="e7129-110">The `SqlStreamChars.SetLength` method is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="e7129-111">A Microsoft não oferece suporte ao uso desse método em um aplicativo de produção em qualquer circunstância.</span><span class="sxs-lookup"><span data-stu-id="e7129-111">Microsoft does not support the use of this method in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="e7129-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e7129-112">Requirements</span></span>

<span data-ttu-id="e7129-113">**Namespace:** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="e7129-113">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="e7129-114">**Assembly:** System. Data (em System. Data. dll)</span><span class="sxs-lookup"><span data-stu-id="e7129-114">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="e7129-115">**.NET Framework versões:** Disponível desde 2,0.</span><span class="sxs-lookup"><span data-stu-id="e7129-115">**.NET Framework versions:** Available since 2.0.</span></span>
