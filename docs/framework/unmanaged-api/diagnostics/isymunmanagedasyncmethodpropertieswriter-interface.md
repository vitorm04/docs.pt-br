---
title: Interface ISymUnmanagedAsyncMethodPropertiesWriter
ms.date: 03/30/2017
ms.assetid: caa71820-8058-4b6a-93a2-25ee757d92d3
ms.openlocfilehash: db065357e22ac576600a3ca61dda0882b9206a86
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129158"
---
# <a name="isymunmanagedasyncmethodpropertieswriter-interface"></a><span data-ttu-id="dfa4d-102">Interface ISymUnmanagedAsyncMethodPropertiesWriter</span><span class="sxs-lookup"><span data-stu-id="dfa4d-102">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>
<span data-ttu-id="dfa4d-103">Permite que você defina informações de método assíncrono opcional para cada símbolo de método.</span><span class="sxs-lookup"><span data-stu-id="dfa4d-103">Allows you to define optional async method information for each method symbol.</span></span> <span data-ttu-id="dfa4d-104">Sempre usar com um método aberto; ou seja, entre as chamadas para o [método OpenMethod](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md) e o [método CloseMethod](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closemethod-method.md).</span><span class="sxs-lookup"><span data-stu-id="dfa4d-104">Always use with an opened method; that is, between calls to the [OpenMethod Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md) and the [CloseMethod Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closemethod-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dfa4d-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="dfa4d-105">Syntax</span></span>  
  
```idl  
[object,uuid(FC073774-1739-4232-BD56-A027294BEC15),pointer_default(unique)]interface ISymUnmanagedAsyncMethodPropertiesWriter : IUnknown  
```  
  
## <a name="methods"></a><span data-ttu-id="dfa4d-106">Métodos</span><span class="sxs-lookup"><span data-stu-id="dfa4d-106">Methods</span></span>  
 <span data-ttu-id="dfa4d-107">Essa interface contém os seguintes métodos:</span><span class="sxs-lookup"><span data-stu-id="dfa4d-107">This interface contains the following methods:</span></span>  
  
|<span data-ttu-id="dfa4d-108">Método</span><span class="sxs-lookup"><span data-stu-id="dfa4d-108">Method</span></span>|<span data-ttu-id="dfa4d-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="dfa4d-109">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="dfa4d-110">Método DefineAsyncStepInfo</span><span class="sxs-lookup"><span data-stu-id="dfa4d-110">DefineAsyncStepInfo Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md)|<span data-ttu-id="dfa4d-111">Defina um grupo de operações assíncronas Await no método atual.</span><span class="sxs-lookup"><span data-stu-id="dfa4d-111">Define a group of async await operations in the current method.</span></span><br /><br /> <span data-ttu-id="dfa4d-112">Cada deslocamento de rendimento corresponde a uma instrução de retorno de Await, identificando um possível rendimento.</span><span class="sxs-lookup"><span data-stu-id="dfa4d-112">Each yield offset matches an await's return instruction, identifying a potential yield.</span></span> <span data-ttu-id="dfa4d-113">Cada `breakpointMethod`/`breakpointOffset` par identifica onde a operação assíncrona será retomada; Ele pode estar em um método diferente.</span><span class="sxs-lookup"><span data-stu-id="dfa4d-113">Each `breakpointMethod`/`breakpointOffset` pair identifies where the asynchronous operation will resume; it may be in a different method.</span></span>|  
|[<span data-ttu-id="dfa4d-114">Método DefineCatchHandlerILOffset</span><span class="sxs-lookup"><span data-stu-id="dfa4d-114">DefineCatchHandlerILOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md)|<span data-ttu-id="dfa4d-115">Define o deslocamento de IL para o manipulador catch gerado pelo compilador que encapsula um método assíncrono.</span><span class="sxs-lookup"><span data-stu-id="dfa4d-115">Sets the IL offset for the compiler-generated catch handler that wraps an async method.</span></span><br /><br /> <span data-ttu-id="dfa4d-116">O deslocamento de IL do catch gerado é usado pelo depurador para lidar com o Catch como se fosse um código de não usuário, mesmo que possa ocorrer em um método de código de usuário.</span><span class="sxs-lookup"><span data-stu-id="dfa4d-116">The IL offset of the generated catch is used by the debugger to handle the catch as if it were non-user code, even though it may occur in a user code method.</span></span> <span data-ttu-id="dfa4d-117">Em particular, ele é usado em resposta a um evento de exceção **CatchHandlerFound** .</span><span class="sxs-lookup"><span data-stu-id="dfa4d-117">In particular, it is used in response to a **CatchHandlerFound** exception event.</span></span>|  
|[<span data-ttu-id="dfa4d-118">Método DefineKickoffMethod</span><span class="sxs-lookup"><span data-stu-id="dfa4d-118">DefineKickoffMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md)|<span data-ttu-id="dfa4d-119">Define o método inicial que inicia a operação assíncrona.</span><span class="sxs-lookup"><span data-stu-id="dfa4d-119">Sets the starting method that initiates the async operation.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="dfa4d-120">Requisitos</span><span class="sxs-lookup"><span data-stu-id="dfa4d-120">Requirements</span></span>  
 <span data-ttu-id="dfa4d-121">**Cabeçalho:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="dfa4d-121">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dfa4d-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dfa4d-122">See also</span></span>

- [<span data-ttu-id="dfa4d-123">Interfaces do repositório de símbolos de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="dfa4d-123">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
