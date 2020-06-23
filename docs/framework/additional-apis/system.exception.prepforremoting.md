---
title: Método Exception. PrepForRemoting (sistema)
description: Examine o método Exception. PrepForRemoting no .NET. O método adiciona o rastreamento de pilha do lado do servidor à mensagem antes que a exceção seja relançada no cliente.
ms.date: 10/08/2019
topic_type:
- apiref
api_name:
- System.Exception.PrepForRemoting
api_location:
- mscorlib.dll
api_type:
- Assembly
ms.openlocfilehash: 9ceb73499ae3bb308975e6db5b961bfe40165ba3
ms.sourcegitcommit: 1c37a894c923bea021a3cc38ce7cba946357bbe1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/19/2020
ms.locfileid: "85105260"
---
# <a name="exceptionprepforremoting-method"></a><span data-ttu-id="e079c-104">Método Exception.PrepForRemoting</span><span class="sxs-lookup"><span data-stu-id="e079c-104">Exception.PrepForRemoting Method</span></span>

<span data-ttu-id="e079c-105">Preserva o rastreamento de pilha do lado do servidor anexando-o à mensagem antes que a exceção seja relançada no site de chamada do cliente.</span><span class="sxs-lookup"><span data-stu-id="e079c-105">Preserves the server-side stack trace by appending it to the message before the exception is rethrown at the client call site.</span></span>

```csharp
internal Exception PrepForRemoting();
```

## <a name="returns"></a><span data-ttu-id="e079c-106">Retornos</span><span class="sxs-lookup"><span data-stu-id="e079c-106">Returns</span></span>

<xref:System.Exception>  
<span data-ttu-id="e079c-107">Esta instância <xref:System.Exception>.</span><span class="sxs-lookup"><span data-stu-id="e079c-107">This <xref:System.Exception> instance.</span></span>

## <a name="remarks"></a><span data-ttu-id="e079c-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="e079c-108">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="e079c-109">O `Exception.PrepForRemoting` método é interno e não deve ser usado diretamente no seu código.</span><span class="sxs-lookup"><span data-stu-id="e079c-109">The `Exception.PrepForRemoting` method is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="e079c-110">A Microsoft não oferece suporte ao uso desse método em um aplicativo de produção em qualquer circunstância.</span><span class="sxs-lookup"><span data-stu-id="e079c-110">Microsoft does not support the use of this method in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="e079c-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e079c-111">Requirements</span></span>

<span data-ttu-id="e079c-112">**Namespace:** <xref:System></span><span class="sxs-lookup"><span data-stu-id="e079c-112">**Namespace:** <xref:System></span></span>

<span data-ttu-id="e079c-113">**Assembly:** mscorlib.dll (em mscorlib.dll)</span><span class="sxs-lookup"><span data-stu-id="e079c-113">**Assembly:** mscorlib.dll (in mscorlib.dll)</span></span>

<span data-ttu-id="e079c-114">**.NET Framework versões:** Disponível desde 1,0.</span><span class="sxs-lookup"><span data-stu-id="e079c-114">**.NET Framework versions:** Available since 1.0.</span></span>
