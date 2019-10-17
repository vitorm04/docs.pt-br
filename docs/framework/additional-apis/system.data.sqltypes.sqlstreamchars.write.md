---
title: Método SqlStreamChars. Write (Char [], Int32, Int32) (System. Data. SqlTypes)
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
ms.openlocfilehash: 9d952041122ceb3824712bd81cab7ce4789c9db8
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395583"
---
# <a name="sqlstreamcharswritechar-int32-int32-method"></a><span data-ttu-id="c3d0b-102">Método SqlStreamChars. Write (Char [], Int32, Int32)</span><span class="sxs-lookup"><span data-stu-id="c3d0b-102">SqlStreamChars.Write(Char[], Int32, Int32) Method</span></span>

<span data-ttu-id="c3d0b-103">Quando substituído em uma classe derivada, o grava uma sequência de caracteres no fluxo atual e avança a posição atual dentro desse fluxo pelo número de caracteres gravados.</span><span class="sxs-lookup"><span data-stu-id="c3d0b-103">When overridden in a derived class, writes a sequence of characters to the current stream and advances the current position within this stream by the number of characters written.</span></span> <span data-ttu-id="c3d0b-104">O assembly que contém esse método tem uma relação Friend com SQLAccess. dll.</span><span class="sxs-lookup"><span data-stu-id="c3d0b-104">The assembly that contains this method has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="c3d0b-105">Ele é destinado ao uso por SQL Server.</span><span class="sxs-lookup"><span data-stu-id="c3d0b-105">It's intended for use by SQL Server.</span></span> <span data-ttu-id="c3d0b-106">Para outros bancos de dados, use o mecanismo de hospedagem fornecido por esse banco.</span><span class="sxs-lookup"><span data-stu-id="c3d0b-106">For other databases, use the hosting mechanism provided by that database.</span></span>

```csharp
public abstract void Write (char[] buffer, int offset, int count);
```

## <a name="parameters"></a><span data-ttu-id="c3d0b-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c3d0b-107">Parameters</span></span>

`buffer`  
<span data-ttu-id="c3d0b-108">Uma matriz char a ser gravada.</span><span class="sxs-lookup"><span data-stu-id="c3d0b-108">A char array to write.</span></span>

`offset`  
<span data-ttu-id="c3d0b-109">Um deslocamento relativo à origem.</span><span class="sxs-lookup"><span data-stu-id="c3d0b-109">An offset relative to origin.</span></span>

`count`  
<span data-ttu-id="c3d0b-110">O número de caracteres a serem gravados no fluxo atual.</span><span class="sxs-lookup"><span data-stu-id="c3d0b-110">The number of characters to be written to the current stream.</span></span>

## <a name="remarks"></a><span data-ttu-id="c3d0b-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="c3d0b-111">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="c3d0b-112">O método `SqlStreamChars.Write` é privado e não se destina a ser usado diretamente no seu código.</span><span class="sxs-lookup"><span data-stu-id="c3d0b-112">The `SqlStreamChars.Write` method is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="c3d0b-113">A Microsoft não dá suporte ao uso desse método para gravar em um aplicativo de produção sob nenhuma circunstância.</span><span class="sxs-lookup"><span data-stu-id="c3d0b-113">Microsoft does not support the use of this method write in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="c3d0b-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c3d0b-114">Requirements</span></span>

<span data-ttu-id="c3d0b-115">**Namespace:** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="c3d0b-115">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="c3d0b-116">**Assembly:** System. Data (em System. Data. dll)</span><span class="sxs-lookup"><span data-stu-id="c3d0b-116">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="c3d0b-117">**.NET Framework versões:** Disponível desde 2,0.</span><span class="sxs-lookup"><span data-stu-id="c3d0b-117">**.NET Framework versions:** Available since 2.0.</span></span>
