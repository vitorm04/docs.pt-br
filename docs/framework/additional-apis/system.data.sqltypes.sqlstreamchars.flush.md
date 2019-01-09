---
title: Método SqlStreamChars.Flush (SqlTypes)
author: douglaslMS
ms.author: douglasl
ms.date: 12/20/2018
ms.technology:
- dotnet-data
api_name:
- System.Data.SqlTypes.SqlStreamChars.Flush
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: ecaf7932a4e832a88b883ceac4746afe6140b38e
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54152739"
---
# <a name="sqlstreamcharsflush-method"></a><span data-ttu-id="b8f14-102">Método SqlStreamChars.Flush</span><span class="sxs-lookup"><span data-stu-id="b8f14-102">SqlStreamChars.Flush Method</span></span>

<span data-ttu-id="b8f14-103">Quando é substituído em uma classe derivada, limpa todos os buffers nesse fluxo e faz com que todos os dados armazenados em buffer sejam gravados no dispositivo subjacente.</span><span class="sxs-lookup"><span data-stu-id="b8f14-103">When overridden in a derived class, clears all buffers for this stream and causes any buffered data to be written to the underlying device.</span></span> <span data-ttu-id="b8f14-104">O assembly que contém este método tem uma relação de amigo com SQLAccess.dll.</span><span class="sxs-lookup"><span data-stu-id="b8f14-104">The assembly that contains this method has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="b8f14-105">Ele é destinado a uso pelo SQL Server.</span><span class="sxs-lookup"><span data-stu-id="b8f14-105">It's intended for use by SQL Server.</span></span> <span data-ttu-id="b8f14-106">Para outros bancos de dados, use o mecanismo de hospedagem fornecido pelo banco de dados.</span><span class="sxs-lookup"><span data-stu-id="b8f14-106">For other databases, use the hosting mechanism provided by that database.</span></span>

## <a name="syntax"></a><span data-ttu-id="b8f14-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b8f14-107">Syntax</span></span>

```csharp
public abstract void Flush ();
```

## <a name="remarks"></a><span data-ttu-id="b8f14-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="b8f14-108">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="b8f14-109">O `SqlStreamChars.Flush` método é privado e não se destina a ser usado diretamente em seu código.</span><span class="sxs-lookup"><span data-stu-id="b8f14-109">The `SqlStreamChars.Flush` method is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="b8f14-110">Microsoft não suporta o uso deste campo em um aplicativo de produção sob nenhuma circunstância.</span><span class="sxs-lookup"><span data-stu-id="b8f14-110">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="b8f14-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b8f14-111">Requirements</span></span>

<span data-ttu-id="b8f14-112">**Namespace:** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="b8f14-112">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="b8f14-113">**Assembly:** System. Data (em dll)</span><span class="sxs-lookup"><span data-stu-id="b8f14-113">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="b8f14-114">**Versões do .NET framework:** Disponível desde o 2.0.</span><span class="sxs-lookup"><span data-stu-id="b8f14-114">**.NET Framework versions:** Available since 2.0.</span></span>