---
title: Interface ISymUnmanagedAsyncMethodPropertiesWriter
ms.date: 03/30/2017
ms.assetid: caa71820-8058-4b6a-93a2-25ee757d92d3
ms.openlocfilehash: 04876483fd42e3f6e55222416fd0747891734a52
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501853"
---
# <a name="isymunmanagedasyncmethodpropertieswriter-interface"></a><span data-ttu-id="5bc04-102">Interface ISymUnmanagedAsyncMethodPropertiesWriter</span><span class="sxs-lookup"><span data-stu-id="5bc04-102">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>
<span data-ttu-id="5bc04-103">Permite que você defina informações de método assíncrono opcional para cada símbolo de método.</span><span class="sxs-lookup"><span data-stu-id="5bc04-103">Allows you to define optional async method information for each method symbol.</span></span> <span data-ttu-id="5bc04-104">Sempre usar com um método aberto; ou seja, entre as chamadas para o [método OpenMethod](isymunmanagedwriter-openmethod-method.md) e o [método CloseMethod](isymunmanagedwriter-closemethod-method.md).</span><span class="sxs-lookup"><span data-stu-id="5bc04-104">Always use with an opened method; that is, between calls to the [OpenMethod Method](isymunmanagedwriter-openmethod-method.md) and the [CloseMethod Method](isymunmanagedwriter-closemethod-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5bc04-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5bc04-105">Syntax</span></span>  
  
```idl  
[object,uuid(FC073774-1739-4232-BD56-A027294BEC15),pointer_default(unique)]interface ISymUnmanagedAsyncMethodPropertiesWriter : IUnknown  
```  
  
## <a name="methods"></a><span data-ttu-id="5bc04-106">Métodos</span><span class="sxs-lookup"><span data-stu-id="5bc04-106">Methods</span></span>  
 <span data-ttu-id="5bc04-107">Essa interface contém os seguintes métodos:</span><span class="sxs-lookup"><span data-stu-id="5bc04-107">This interface contains the following methods:</span></span>  
  
|<span data-ttu-id="5bc04-108">Método</span><span class="sxs-lookup"><span data-stu-id="5bc04-108">Method</span></span>|<span data-ttu-id="5bc04-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="5bc04-109">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5bc04-110">Método DefineAsyncStepInfo</span><span class="sxs-lookup"><span data-stu-id="5bc04-110">DefineAsyncStepInfo Method</span></span>](isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md)|<span data-ttu-id="5bc04-111">Defina um grupo de operações assíncronas Await no método atual.</span><span class="sxs-lookup"><span data-stu-id="5bc04-111">Define a group of async await operations in the current method.</span></span><br /><br /> <span data-ttu-id="5bc04-112">Cada deslocamento de rendimento corresponde a uma instrução de retorno de Await, identificando um possível rendimento.</span><span class="sxs-lookup"><span data-stu-id="5bc04-112">Each yield offset matches an await's return instruction, identifying a potential yield.</span></span> <span data-ttu-id="5bc04-113">Cada `breakpointMethod` / `breakpointOffset` par identifica onde a operação assíncrona será retomada; ela pode estar em um método diferente.</span><span class="sxs-lookup"><span data-stu-id="5bc04-113">Each `breakpointMethod`/`breakpointOffset` pair identifies where the asynchronous operation will resume; it may be in a different method.</span></span>|  
|[<span data-ttu-id="5bc04-114">Método DefineCatchHandlerILOffset</span><span class="sxs-lookup"><span data-stu-id="5bc04-114">DefineCatchHandlerILOffset Method</span></span>](isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md)|<span data-ttu-id="5bc04-115">Define o deslocamento de IL para o manipulador catch gerado pelo compilador que encapsula um método assíncrono.</span><span class="sxs-lookup"><span data-stu-id="5bc04-115">Sets the IL offset for the compiler-generated catch handler that wraps an async method.</span></span><br /><br /> <span data-ttu-id="5bc04-116">O deslocamento de IL do catch gerado é usado pelo depurador para lidar com o Catch como se fosse um código de não usuário, mesmo que possa ocorrer em um método de código de usuário.</span><span class="sxs-lookup"><span data-stu-id="5bc04-116">The IL offset of the generated catch is used by the debugger to handle the catch as if it were non-user code, even though it may occur in a user code method.</span></span> <span data-ttu-id="5bc04-117">Em particular, ele é usado em resposta a um evento de exceção **CatchHandlerFound** .</span><span class="sxs-lookup"><span data-stu-id="5bc04-117">In particular, it is used in response to a **CatchHandlerFound** exception event.</span></span>|  
|[<span data-ttu-id="5bc04-118">Método DefineKickoffMethod</span><span class="sxs-lookup"><span data-stu-id="5bc04-118">DefineKickoffMethod Method</span></span>](isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md)|<span data-ttu-id="5bc04-119">Define o método inicial que inicia a operação assíncrona.</span><span class="sxs-lookup"><span data-stu-id="5bc04-119">Sets the starting method that initiates the async operation.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5bc04-120">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5bc04-120">Requirements</span></span>  
 <span data-ttu-id="5bc04-121">**Cabeçalho:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="5bc04-121">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5bc04-122">Confira também</span><span class="sxs-lookup"><span data-stu-id="5bc04-122">See also</span></span>

- [<span data-ttu-id="5bc04-123">Interfaces de armazenamento de símbolo de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="5bc04-123">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
