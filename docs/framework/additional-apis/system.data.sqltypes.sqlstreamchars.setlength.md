---
title: Método SqlStreamChars.SetLength(Int64) (SqlTypes)
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
ms.openlocfilehash: 1283fea83cf77bbc898d460feedc72b898a65fb7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61675163"
---
# <a name="sqlstreamcharssetlengthint64-method"></a><span data-ttu-id="a2a9f-102">Método SqlStreamChars.SetLength(Int64)</span><span class="sxs-lookup"><span data-stu-id="a2a9f-102">SqlStreamChars.SetLength(Int64) Method</span></span>

<span data-ttu-id="a2a9f-103">Quando substituído em uma classe derivada, libera os recursos usados pelo fluxo.</span><span class="sxs-lookup"><span data-stu-id="a2a9f-103">When overridden in a derived class, releases the resources used by the stream.</span></span> <span data-ttu-id="a2a9f-104">O assembly que contém este método tem uma relação de amigo com SQLAccess.dll.</span><span class="sxs-lookup"><span data-stu-id="a2a9f-104">The assembly that contains this method has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="a2a9f-105">Ele é destinado a uso pelo SQL Server.</span><span class="sxs-lookup"><span data-stu-id="a2a9f-105">It's intended for use by SQL Server.</span></span> <span data-ttu-id="a2a9f-106">Para outros bancos de dados, use o mecanismo de hospedagem fornecido pelo banco de dados.</span><span class="sxs-lookup"><span data-stu-id="a2a9f-106">For other databases, use the hosting mechanism provided by that database.</span></span>

```csharp
public abstract void SetLength (long value);
```

## <a name="parameters"></a><span data-ttu-id="a2a9f-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a2a9f-107">Parameters</span></span>

`value`\
<span data-ttu-id="a2a9f-108">O tamanho desejado do fluxo atual em bytes.</span><span class="sxs-lookup"><span data-stu-id="a2a9f-108">The desired length of the current stream in bytes.</span></span>

## <a name="remarks"></a><span data-ttu-id="a2a9f-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="a2a9f-109">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="a2a9f-110">O `SqlStreamChars.SetLength` método é privado e não se destina a ser usado diretamente em seu código.</span><span class="sxs-lookup"><span data-stu-id="a2a9f-110">The `SqlStreamChars.SetLength` method is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="a2a9f-111">Microsoft não suporta o uso deste campo em um aplicativo de produção sob nenhuma circunstância.</span><span class="sxs-lookup"><span data-stu-id="a2a9f-111">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="a2a9f-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a2a9f-112">Requirements</span></span>

<span data-ttu-id="a2a9f-113">**Namespace:** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="a2a9f-113">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="a2a9f-114">**Assembly:** System. Data (em dll)</span><span class="sxs-lookup"><span data-stu-id="a2a9f-114">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="a2a9f-115">**Versões do .NET framework:** Disponível desde o 2.0.</span><span class="sxs-lookup"><span data-stu-id="a2a9f-115">**.NET Framework versions:** Available since 2.0.</span></span>