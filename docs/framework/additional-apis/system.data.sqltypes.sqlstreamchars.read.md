---
title: Método SqlStreamChars. Read (Char [], Int32, Int32) (System. Data. SqlTypes)
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
ms.openlocfilehash: 9c8a1526e75fdc304022e74a7cc52506762489ea
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395747"
---
# <a name="sqlstreamcharsreadchar-int32-int32-method"></a><span data-ttu-id="fc05d-102">Método SqlStreamChars. Read (Char [], Int32, Int32)</span><span class="sxs-lookup"><span data-stu-id="fc05d-102">SqlStreamChars.Read(Char[], Int32, Int32) Method</span></span>

<span data-ttu-id="fc05d-103">Quando substituído em uma classe derivada, o lê o próximo conjunto de caracteres do fluxo de entrada.</span><span class="sxs-lookup"><span data-stu-id="fc05d-103">When overridden in a derived class, reads the next set of characters from the input stream.</span></span> <span data-ttu-id="fc05d-104">O assembly que contém esse método tem uma relação Friend com SQLAccess. dll.</span><span class="sxs-lookup"><span data-stu-id="fc05d-104">The assembly that contains this method has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="fc05d-105">Ele é destinado ao uso por SQL Server.</span><span class="sxs-lookup"><span data-stu-id="fc05d-105">It's intended for use by SQL Server.</span></span> <span data-ttu-id="fc05d-106">Para outros bancos de dados, use o mecanismo de hospedagem fornecido por esse banco.</span><span class="sxs-lookup"><span data-stu-id="fc05d-106">For other databases, use the hosting mechanism provided by that database.</span></span>

```csharp
public abstract int Read (char[] buffer, int offset, int count);
```

## <a name="parameters"></a><span data-ttu-id="fc05d-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="fc05d-107">Parameters</span></span>

`buffer`\
<span data-ttu-id="fc05d-108">Uma matriz char a ser lida.</span><span class="sxs-lookup"><span data-stu-id="fc05d-108">A char array to read.</span></span>

`offset`\
<span data-ttu-id="fc05d-109">Um deslocamento relativo à origem.</span><span class="sxs-lookup"><span data-stu-id="fc05d-109">An offset relative to origin.</span></span>

`count`\
<span data-ttu-id="fc05d-110">O número de caracteres a serem lidos do fluxo atual.</span><span class="sxs-lookup"><span data-stu-id="fc05d-110">The number of characters to be read from the current stream.</span></span>

## <a name="returns"></a><span data-ttu-id="fc05d-111">Retorna</span><span class="sxs-lookup"><span data-stu-id="fc05d-111">Returns</span></span>

<xref:System.Int32>\
<span data-ttu-id="fc05d-112">O número total de caracteres lidos no buffer.</span><span class="sxs-lookup"><span data-stu-id="fc05d-112">The total number of characters read into the buffer.</span></span>

## <a name="remarks"></a><span data-ttu-id="fc05d-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="fc05d-113">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="fc05d-114">O método `SqlStreamChars.Read` é privado e não se destina a ser usado diretamente no seu código.</span><span class="sxs-lookup"><span data-stu-id="fc05d-114">The `SqlStreamChars.Read` method is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="fc05d-115">A Microsoft não oferece suporte ao uso desse método em um aplicativo de produção em qualquer circunstância.</span><span class="sxs-lookup"><span data-stu-id="fc05d-115">Microsoft does not support the use of this method in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="fc05d-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="fc05d-116">Requirements</span></span>

<span data-ttu-id="fc05d-117">**Namespace:** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="fc05d-117">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="fc05d-118">**Assembly:** System. Data (em System. Data. dll)</span><span class="sxs-lookup"><span data-stu-id="fc05d-118">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="fc05d-119">**.NET Framework versões:** Disponível desde 2,0.</span><span class="sxs-lookup"><span data-stu-id="fc05d-119">**.NET Framework versions:** Available since 2.0.</span></span>
