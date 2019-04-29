---
title: Método SqlStreamChars.Write (Char [], Int32, Int32) (SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/20/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.Write
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: 4084c7161eaa91d78eab32f1c14624e0032cdfcf
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61705903"
---
# <a name="sqlstreamcharswritechar-int32-int32-method"></a><span data-ttu-id="fd161-102">SqlStreamChars.Write(Char[], Int32, Int32) Method</span><span class="sxs-lookup"><span data-stu-id="fd161-102">SqlStreamChars.Write(Char[], Int32, Int32) Method</span></span>

<span data-ttu-id="fd161-103">Quando substituído em uma classe derivada, grava uma sequência de caracteres no fluxo atual e avança a posição atual dentro desse fluxo pelo número de caracteres gravados.</span><span class="sxs-lookup"><span data-stu-id="fd161-103">When overridden in a derived class, writes a sequence of characters to the current stream and advances the current position within this stream by the number of characters written.</span></span> <span data-ttu-id="fd161-104">O assembly que contém este método tem uma relação de amigo com SQLAccess.dll.</span><span class="sxs-lookup"><span data-stu-id="fd161-104">The assembly that contains this method has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="fd161-105">Ele é destinado a uso pelo SQL Server.</span><span class="sxs-lookup"><span data-stu-id="fd161-105">It's intended for use by SQL Server.</span></span> <span data-ttu-id="fd161-106">Para outros bancos de dados, use o mecanismo de hospedagem fornecido pelo banco de dados.</span><span class="sxs-lookup"><span data-stu-id="fd161-106">For other databases, use the hosting mechanism provided by that database.</span></span>

```csharp
public abstract void Write (char[] buffer, int offset, int count);
```

## <a name="parameters"></a><span data-ttu-id="fd161-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="fd161-107">Parameters</span></span>

`buffer`  
<span data-ttu-id="fd161-108">Uma matriz de char para gravar.</span><span class="sxs-lookup"><span data-stu-id="fd161-108">A char array to write.</span></span>

`offset`  
<span data-ttu-id="fd161-109">Um deslocamento relativo à origem.</span><span class="sxs-lookup"><span data-stu-id="fd161-109">An offset relative to origin.</span></span>

`count`  
<span data-ttu-id="fd161-110">O número de caracteres a serem gravados no fluxo atual.</span><span class="sxs-lookup"><span data-stu-id="fd161-110">The number of characters to be written to the current stream.</span></span>

## <a name="remarks"></a><span data-ttu-id="fd161-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="fd161-111">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="fd161-112">O `SqlStreamChars.Write` método é privado e não se destina a ser usado diretamente em seu código.</span><span class="sxs-lookup"><span data-stu-id="fd161-112">The `SqlStreamChars.Write` method is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="fd161-113">Microsoft não suporta o uso deste campo em um aplicativo de produção sob nenhuma circunstância.</span><span class="sxs-lookup"><span data-stu-id="fd161-113">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="fd161-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="fd161-114">Requirements</span></span>

<span data-ttu-id="fd161-115">**Namespace:** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="fd161-115">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="fd161-116">**Assembly:** System. Data (em dll)</span><span class="sxs-lookup"><span data-stu-id="fd161-116">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="fd161-117">**Versões do .NET framework:** Disponível desde o 2.0.</span><span class="sxs-lookup"><span data-stu-id="fd161-117">**.NET Framework versions:** Available since 2.0.</span></span>
