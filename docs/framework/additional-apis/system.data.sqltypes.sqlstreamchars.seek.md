---
title: Método SqlStreamChars.Seek (Int64, SeekOrigin) (SqlTypes)
author: douglaslMS
ms.author: douglasl
ms.date: 12/20/2018
ms.technology:
- dotnet-data
api_name:
- System.Data.SqlTypes.SqlStreamChars.Seek
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: aab3195ec0d300a7f001f98f2d646c85be939356
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54152549"
---
# <a name="sqlstreamcharsseekint64-seekorigin-method"></a><span data-ttu-id="50c6a-102">Método SqlStreamChars.Seek (Int64, SeekOrigin)</span><span class="sxs-lookup"><span data-stu-id="50c6a-102">SqlStreamChars.Seek(Int64, SeekOrigin) Method</span></span>

<span data-ttu-id="50c6a-103">Quando substituído em uma classe derivada, define a posição dentro do fluxo atual.</span><span class="sxs-lookup"><span data-stu-id="50c6a-103">When overridden in a derived class, sets the position within the current stream.</span></span> <span data-ttu-id="50c6a-104">O assembly que contém este método tem uma relação de amigo com SQLAccess.dll.</span><span class="sxs-lookup"><span data-stu-id="50c6a-104">The assembly that contains this method has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="50c6a-105">Ele é destinado a uso pelo SQL Server.</span><span class="sxs-lookup"><span data-stu-id="50c6a-105">It's intended for use by SQL Server.</span></span> <span data-ttu-id="50c6a-106">Para outros bancos de dados, use o mecanismo de hospedagem fornecido pelo banco de dados.</span><span class="sxs-lookup"><span data-stu-id="50c6a-106">For other databases, use the hosting mechanism provided by that database.</span></span>

```csharp
public abstract long Seek (long offset, System.IO.SeekOrigin origin);
```

## <a name="parameters"></a><span data-ttu-id="50c6a-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="50c6a-107">Parameters</span></span>

`offset`\
<span data-ttu-id="50c6a-108">Um deslocamento de bytes em relação a `origin`.</span><span class="sxs-lookup"><span data-stu-id="50c6a-108">A byte offset relative to `origin`.</span></span>

`origin`\
<span data-ttu-id="50c6a-109">Um dos valores de enumeração que indica o ponto de referência do qual obter a nova posição.</span><span class="sxs-lookup"><span data-stu-id="50c6a-109">One of the enumeration values that indicates the reference point from which to obtain the new position.</span></span>

## <a name="returns"></a><span data-ttu-id="50c6a-110">Retorna</span><span class="sxs-lookup"><span data-stu-id="50c6a-110">Returns</span></span>

<xref:System.Int32>\
<span data-ttu-id="50c6a-111">A nova posição dentro do fluxo atual.</span><span class="sxs-lookup"><span data-stu-id="50c6a-111">The new position within the current stream.</span></span>

## <a name="remarks"></a><span data-ttu-id="50c6a-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="50c6a-112">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="50c6a-113">O `SqlStreamChars.Seek` método é privado e não se destina a ser usado diretamente em seu código.</span><span class="sxs-lookup"><span data-stu-id="50c6a-113">The `SqlStreamChars.Seek` method is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="50c6a-114">Microsoft não suporta o uso deste campo em um aplicativo de produção sob nenhuma circunstância.</span><span class="sxs-lookup"><span data-stu-id="50c6a-114">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="50c6a-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="50c6a-115">Requirements</span></span>

<span data-ttu-id="50c6a-116">**Namespace:** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="50c6a-116">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="50c6a-117">**Assembly:** System. Data (em dll)</span><span class="sxs-lookup"><span data-stu-id="50c6a-117">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="50c6a-118">**Versões do .NET framework:** Disponível desde o 2.0.</span><span class="sxs-lookup"><span data-stu-id="50c6a-118">**.NET Framework versions:** Available since 2.0.</span></span>