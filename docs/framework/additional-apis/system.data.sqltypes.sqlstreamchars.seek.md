---
title: Método SqlStreamChars.Seek (Int64, SeekOrigin) (SqlTypes)
author: douglaslMS
ms.author: douglasl
ms.date: 12/20/2018
ms.technology:
- dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.Seek
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: 1710c802324920e324b18ddea843f0a532fa0d17
ms.sourcegitcommit: a36cfc9dbbfc04bd88971f96e8a3f8e283c15d42
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/11/2019
ms.locfileid: "54222981"
---
# <a name="sqlstreamcharsseekint64-seekorigin-method"></a><span data-ttu-id="dde83-102">Método SqlStreamChars.Seek (Int64, SeekOrigin)</span><span class="sxs-lookup"><span data-stu-id="dde83-102">SqlStreamChars.Seek(Int64, SeekOrigin) Method</span></span>

<span data-ttu-id="dde83-103">Quando substituído em uma classe derivada, define a posição dentro do fluxo atual.</span><span class="sxs-lookup"><span data-stu-id="dde83-103">When overridden in a derived class, sets the position within the current stream.</span></span> <span data-ttu-id="dde83-104">O assembly que contém este método tem uma relação de amigo com SQLAccess.dll.</span><span class="sxs-lookup"><span data-stu-id="dde83-104">The assembly that contains this method has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="dde83-105">Ele é destinado a uso pelo SQL Server.</span><span class="sxs-lookup"><span data-stu-id="dde83-105">It's intended for use by SQL Server.</span></span> <span data-ttu-id="dde83-106">Para outros bancos de dados, use o mecanismo de hospedagem fornecido pelo banco de dados.</span><span class="sxs-lookup"><span data-stu-id="dde83-106">For other databases, use the hosting mechanism provided by that database.</span></span>

```csharp
public abstract long Seek (long offset, System.IO.SeekOrigin origin);
```

## <a name="parameters"></a><span data-ttu-id="dde83-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="dde83-107">Parameters</span></span>

`offset`\
<span data-ttu-id="dde83-108">Um deslocamento de bytes em relação a `origin`.</span><span class="sxs-lookup"><span data-stu-id="dde83-108">A byte offset relative to `origin`.</span></span>

`origin`\
<span data-ttu-id="dde83-109">Um dos valores de enumeração que indica o ponto de referência do qual obter a nova posição.</span><span class="sxs-lookup"><span data-stu-id="dde83-109">One of the enumeration values that indicates the reference point from which to obtain the new position.</span></span>

## <a name="returns"></a><span data-ttu-id="dde83-110">Retorna</span><span class="sxs-lookup"><span data-stu-id="dde83-110">Returns</span></span>

<xref:System.Int32>\
<span data-ttu-id="dde83-111">A nova posição dentro do fluxo atual.</span><span class="sxs-lookup"><span data-stu-id="dde83-111">The new position within the current stream.</span></span>

## <a name="remarks"></a><span data-ttu-id="dde83-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="dde83-112">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="dde83-113">O `SqlStreamChars.Seek` método é privado e não se destina a ser usado diretamente em seu código.</span><span class="sxs-lookup"><span data-stu-id="dde83-113">The `SqlStreamChars.Seek` method is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="dde83-114">Microsoft não suporta o uso deste campo em um aplicativo de produção sob nenhuma circunstância.</span><span class="sxs-lookup"><span data-stu-id="dde83-114">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="dde83-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="dde83-115">Requirements</span></span>

<span data-ttu-id="dde83-116">**Namespace:** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="dde83-116">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="dde83-117">**Assembly:** System. Data (em dll)</span><span class="sxs-lookup"><span data-stu-id="dde83-117">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="dde83-118">**Versões do .NET framework:** Disponível desde o 2.0.</span><span class="sxs-lookup"><span data-stu-id="dde83-118">**.NET Framework versions:** Available since 2.0.</span></span>