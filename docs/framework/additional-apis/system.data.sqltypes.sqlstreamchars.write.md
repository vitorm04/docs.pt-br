---
title: Método SqlStreamChars.Write (Char [], Int32, Int32) (SqlTypes)
author: douglaslMS
ms.author: douglasl
ms.date: 12/20/2018
ms.technology:
- dotnet-data
api_name:
- System.Data.SqlTypes.SqlStreamChars.Write
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: e8c8ee7ab7a744c1a1d18212f1c7f9788c91ea0d
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54152569"
---
# <a name="sqlstreamcharswritechar-int32-int32-method"></a><span data-ttu-id="18e5d-102">Método SqlStreamChars.Write (Char [], Int32, Int32)</span><span class="sxs-lookup"><span data-stu-id="18e5d-102">SqlStreamChars.Write(Char[], Int32, Int32) Method</span></span>

<span data-ttu-id="18e5d-103">Quando substituído em uma classe derivada, grava uma sequência de caracteres no fluxo atual e avança a posição atual dentro desse fluxo pelo número de caracteres gravados.</span><span class="sxs-lookup"><span data-stu-id="18e5d-103">When overridden in a derived class, writes a sequence of characters to the current stream and advances the current position within this stream by the number of characters written.</span></span> <span data-ttu-id="18e5d-104">O assembly que contém este método tem uma relação de amigo com SQLAccess.dll.</span><span class="sxs-lookup"><span data-stu-id="18e5d-104">The assembly that contains this method has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="18e5d-105">Ele é destinado a uso pelo SQL Server.</span><span class="sxs-lookup"><span data-stu-id="18e5d-105">It's intended for use by SQL Server.</span></span> <span data-ttu-id="18e5d-106">Para outros bancos de dados, use o mecanismo de hospedagem fornecido pelo banco de dados.</span><span class="sxs-lookup"><span data-stu-id="18e5d-106">For other databases, use the hosting mechanism provided by that database.</span></span>

```csharp
public abstract void Write (char[] buffer, int offset, int count);
```

## <a name="parameters"></a><span data-ttu-id="18e5d-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="18e5d-107">Parameters</span></span>

`buffer`  
<span data-ttu-id="18e5d-108">Uma matriz de char para gravar.</span><span class="sxs-lookup"><span data-stu-id="18e5d-108">A char array to write.</span></span>

`offset`  
<span data-ttu-id="18e5d-109">Um deslocamento relativo à origem.</span><span class="sxs-lookup"><span data-stu-id="18e5d-109">An offset relative to origin.</span></span>

`count`  
<span data-ttu-id="18e5d-110">O número de caracteres a serem gravados no fluxo atual.</span><span class="sxs-lookup"><span data-stu-id="18e5d-110">The number of characters to be written to the current stream.</span></span>

## <a name="remarks"></a><span data-ttu-id="18e5d-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="18e5d-111">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="18e5d-112">O `SqlStreamChars.Write` método é privado e não se destina a ser usado diretamente em seu código.</span><span class="sxs-lookup"><span data-stu-id="18e5d-112">The `SqlStreamChars.Write` method is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="18e5d-113">Microsoft não suporta o uso deste campo em um aplicativo de produção sob nenhuma circunstância.</span><span class="sxs-lookup"><span data-stu-id="18e5d-113">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="18e5d-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="18e5d-114">Requirements</span></span>

<span data-ttu-id="18e5d-115">**Namespace:** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="18e5d-115">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="18e5d-116">**Assembly:** System. Data (em dll)</span><span class="sxs-lookup"><span data-stu-id="18e5d-116">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="18e5d-117">**Versões do .NET framework:** Disponível desde o 2.0.</span><span class="sxs-lookup"><span data-stu-id="18e5d-117">**.NET Framework versions:** Available since 2.0.</span></span>