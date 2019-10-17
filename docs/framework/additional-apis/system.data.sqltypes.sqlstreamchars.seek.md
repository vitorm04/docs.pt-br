---
title: Método SqlStreamChars. Seek (Int64, SeekOrigin) (System. Data. SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/20/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.Seek
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: db8aba0a86c140ba62af8056011226532d415951
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395590"
---
# <a name="sqlstreamcharsseekint64-seekorigin-method"></a><span data-ttu-id="9424e-102">Método SqlStreamChars. Seek (Int64, SeekOrigin)</span><span class="sxs-lookup"><span data-stu-id="9424e-102">SqlStreamChars.Seek(Int64, SeekOrigin) Method</span></span>

<span data-ttu-id="9424e-103">Quando substituído em uma classe derivada, define a posição dentro do fluxo atual.</span><span class="sxs-lookup"><span data-stu-id="9424e-103">When overridden in a derived class, sets the position within the current stream.</span></span> <span data-ttu-id="9424e-104">O assembly que contém esse método tem uma relação Friend com SQLAccess. dll.</span><span class="sxs-lookup"><span data-stu-id="9424e-104">The assembly that contains this method has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="9424e-105">Ele é destinado ao uso por SQL Server.</span><span class="sxs-lookup"><span data-stu-id="9424e-105">It's intended for use by SQL Server.</span></span> <span data-ttu-id="9424e-106">Para outros bancos de dados, use o mecanismo de hospedagem fornecido por esse banco.</span><span class="sxs-lookup"><span data-stu-id="9424e-106">For other databases, use the hosting mechanism provided by that database.</span></span>

```csharp
public abstract long Seek (long offset, System.IO.SeekOrigin origin);
```

## <a name="parameters"></a><span data-ttu-id="9424e-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="9424e-107">Parameters</span></span>

`offset`\
<span data-ttu-id="9424e-108">Um deslocamento de bytes em relação a `origin`.</span><span class="sxs-lookup"><span data-stu-id="9424e-108">A byte offset relative to `origin`.</span></span>

`origin`\
<span data-ttu-id="9424e-109">Um dos valores de enumeração que indica o ponto de referência do qual obter a nova posição.</span><span class="sxs-lookup"><span data-stu-id="9424e-109">One of the enumeration values that indicates the reference point from which to obtain the new position.</span></span>

## <a name="returns"></a><span data-ttu-id="9424e-110">Retorna</span><span class="sxs-lookup"><span data-stu-id="9424e-110">Returns</span></span>

<xref:System.Int32>\
<span data-ttu-id="9424e-111">A nova posição dentro do fluxo atual.</span><span class="sxs-lookup"><span data-stu-id="9424e-111">The new position within the current stream.</span></span>

## <a name="remarks"></a><span data-ttu-id="9424e-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="9424e-112">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="9424e-113">O método `SqlStreamChars.Seek` é privado e não se destina a ser usado diretamente no seu código.</span><span class="sxs-lookup"><span data-stu-id="9424e-113">The `SqlStreamChars.Seek` method is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="9424e-114">A Microsoft não oferece suporte ao uso desse método em um aplicativo de produção em qualquer circunstância.</span><span class="sxs-lookup"><span data-stu-id="9424e-114">Microsoft does not support the use of this method in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="9424e-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9424e-115">Requirements</span></span>

<span data-ttu-id="9424e-116">**Namespace:** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="9424e-116">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="9424e-117">**Assembly:** System. Data (em System. Data. dll)</span><span class="sxs-lookup"><span data-stu-id="9424e-117">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="9424e-118">**.NET Framework versões:** Disponível desde 2,0.</span><span class="sxs-lookup"><span data-stu-id="9424e-118">**.NET Framework versions:** Available since 2.0.</span></span>
