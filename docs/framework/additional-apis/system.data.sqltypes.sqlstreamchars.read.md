---
title: Método SqlStreamChars.Read (Char [], Int32, Int32) (SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/20/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.Read
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: df92acfd4050eb16d3a101b20b9b44560273f4d5
ms.sourcegitcommit: d938c39afb9216db377d0f0ecdaa53936a851059
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/29/2019
ms.locfileid: "58633641"
---
# <a name="sqlstreamcharsreadchar-int32-int32-method"></a><span data-ttu-id="0202f-102">SqlStreamChars.Read(Char[], Int32, Int32) Method</span><span class="sxs-lookup"><span data-stu-id="0202f-102">SqlStreamChars.Read(Char[], Int32, Int32) Method</span></span>

<span data-ttu-id="0202f-103">Quando substituído em uma classe derivada, lê o próximo conjunto de caracteres do fluxo de entrada.</span><span class="sxs-lookup"><span data-stu-id="0202f-103">When overridden in a derived class, reads the next set of characters from the input stream.</span></span> <span data-ttu-id="0202f-104">O assembly que contém este método tem uma relação de amigo com SQLAccess.dll.</span><span class="sxs-lookup"><span data-stu-id="0202f-104">The assembly that contains this method has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="0202f-105">Ele é destinado a uso pelo SQL Server.</span><span class="sxs-lookup"><span data-stu-id="0202f-105">It's intended for use by SQL Server.</span></span> <span data-ttu-id="0202f-106">Para outros bancos de dados, use o mecanismo de hospedagem fornecido pelo banco de dados.</span><span class="sxs-lookup"><span data-stu-id="0202f-106">For other databases, use the hosting mechanism provided by that database.</span></span>

```csharp
public abstract int Read (char[] buffer, int offset, int count);
```

## <a name="parameters"></a><span data-ttu-id="0202f-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0202f-107">Parameters</span></span>

`buffer`\
<span data-ttu-id="0202f-108">Uma matriz de char para ler.</span><span class="sxs-lookup"><span data-stu-id="0202f-108">A char array to read.</span></span>

`offset`\
<span data-ttu-id="0202f-109">Um deslocamento relativo à origem.</span><span class="sxs-lookup"><span data-stu-id="0202f-109">An offset relative to origin.</span></span>

`count`\
<span data-ttu-id="0202f-110">O número de caracteres a serem lidos do fluxo atual.</span><span class="sxs-lookup"><span data-stu-id="0202f-110">The number of characters to be read from the current stream.</span></span>

## <a name="returns"></a><span data-ttu-id="0202f-111">Retorna</span><span class="sxs-lookup"><span data-stu-id="0202f-111">Returns</span></span>

<xref:System.Int32>\
<span data-ttu-id="0202f-112">O número total de caracteres lidos no buffer.</span><span class="sxs-lookup"><span data-stu-id="0202f-112">The total number of characters read into the buffer.</span></span>

## <a name="remarks"></a><span data-ttu-id="0202f-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="0202f-113">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="0202f-114">O `SqlStreamChars.Read` método é privado e não se destina a ser usado diretamente em seu código.</span><span class="sxs-lookup"><span data-stu-id="0202f-114">The `SqlStreamChars.Read` method is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="0202f-115">Microsoft não suporta o uso deste campo em um aplicativo de produção sob nenhuma circunstância.</span><span class="sxs-lookup"><span data-stu-id="0202f-115">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="0202f-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0202f-116">Requirements</span></span>

<span data-ttu-id="0202f-117">**Namespace:** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="0202f-117">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="0202f-118">**Assembly:** System. Data (em dll)</span><span class="sxs-lookup"><span data-stu-id="0202f-118">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="0202f-119">**Versões do .NET framework:** Disponível desde o 2.0.</span><span class="sxs-lookup"><span data-stu-id="0202f-119">**.NET Framework versions:** Available since 2.0.</span></span>