---
title: Método Exception. PrepForRemoting (sistema)
ms.date: 10/08/2019
topic_type:
- apiref
api_name:
- System.Exception.PrepForRemoting
api_location:
- mscorlib.dll
api_type:
- Assembly
ms.openlocfilehash: ce1c24578690a1643b7f5af0e44eaae95ed7b0a2
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77214893"
---
# <a name="exceptionprepforremoting-method"></a><span data-ttu-id="6adf4-102">Método Exception.PrepForRemoting</span><span class="sxs-lookup"><span data-stu-id="6adf4-102">Exception.PrepForRemoting Method</span></span>

<span data-ttu-id="6adf4-103">Preserva o rastreamento de pilha do lado do servidor anexando-o à mensagem antes que a exceção seja relançada no site de chamada do cliente.</span><span class="sxs-lookup"><span data-stu-id="6adf4-103">Preserves the server-side stack trace by appending it to the message before the exception is rethrown at the client call site.</span></span>

```csharp
internal Exception PrepForRemoting();
```

## <a name="returns"></a><span data-ttu-id="6adf4-104">Retornos</span><span class="sxs-lookup"><span data-stu-id="6adf4-104">Returns</span></span>

<xref:System.Exception>  
<span data-ttu-id="6adf4-105">Esta instância <xref:System.Exception>.</span><span class="sxs-lookup"><span data-stu-id="6adf4-105">This <xref:System.Exception> instance.</span></span>

## <a name="remarks"></a><span data-ttu-id="6adf4-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="6adf4-106">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="6adf4-107">O método `Exception.PrepForRemoting` é interno e não deve ser usado diretamente no seu código.</span><span class="sxs-lookup"><span data-stu-id="6adf4-107">The `Exception.PrepForRemoting` method is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="6adf4-108">A Microsoft não oferece suporte ao uso desse método em um aplicativo de produção em qualquer circunstância.</span><span class="sxs-lookup"><span data-stu-id="6adf4-108">Microsoft does not support the use of this method in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="6adf4-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6adf4-109">Requirements</span></span>

<span data-ttu-id="6adf4-110">**Namespace:** <xref:System></span><span class="sxs-lookup"><span data-stu-id="6adf4-110">**Namespace:** <xref:System></span></span>

<span data-ttu-id="6adf4-111">**Assembly:** mscorlib. dll (em mscorlib. dll)</span><span class="sxs-lookup"><span data-stu-id="6adf4-111">**Assembly:** mscorlib.dll (in mscorlib.dll)</span></span>

<span data-ttu-id="6adf4-112">**.NET Framework versões:** Disponível desde 1,0.</span><span class="sxs-lookup"><span data-stu-id="6adf4-112">**.NET Framework versions:** Available since 1.0.</span></span>
