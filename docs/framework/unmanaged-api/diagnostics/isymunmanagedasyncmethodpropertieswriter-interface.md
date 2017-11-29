---
title: Interface ISymUnmanagedAsyncMethodPropertiesWriter
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: caa71820-8058-4b6a-93a2-25ee757d92d3
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: dd84ea5ee00df3e59d4907cdf97bc36b7f06d993
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedasyncmethodpropertieswriter-interface"></a><span data-ttu-id="7c02d-102">Interface ISymUnmanagedAsyncMethodPropertiesWriter</span><span class="sxs-lookup"><span data-stu-id="7c02d-102">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>
<span data-ttu-id="7c02d-103">Permite que você defina informações do método assíncrono opcional para o símbolo de cada método.</span><span class="sxs-lookup"><span data-stu-id="7c02d-103">Allows you to define optional async method information for each method symbol.</span></span> <span data-ttu-id="7c02d-104">Sempre use um método aberto; ou seja, entre as chamadas para o [método OpenMethod](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md) e [método CloseMethod](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closemethod-method.md).</span><span class="sxs-lookup"><span data-stu-id="7c02d-104">Always use with an opened method; that is, between calls to the [OpenMethod Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md) and the [CloseMethod Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closemethod-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7c02d-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7c02d-105">Syntax</span></span>  
  
```idl  
[object,uuid(FC073774-1739-4232-BD56-A027294BEC15),pointer_default(unique)]interface ISymUnmanagedAsyncMethodPropertiesWriter : IUnknown  
```  
  
## <a name="methods"></a><span data-ttu-id="7c02d-106">Métodos</span><span class="sxs-lookup"><span data-stu-id="7c02d-106">Methods</span></span>  
 <span data-ttu-id="7c02d-107">Essa interface contém os seguintes métodos:</span><span class="sxs-lookup"><span data-stu-id="7c02d-107">This interface contains the following methods:</span></span>  
  
|<span data-ttu-id="7c02d-108">Método</span><span class="sxs-lookup"><span data-stu-id="7c02d-108">Method</span></span>|<span data-ttu-id="7c02d-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="7c02d-109">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7c02d-110">Método DefineAsyncStepInfo</span><span class="sxs-lookup"><span data-stu-id="7c02d-110">DefineAsyncStepInfo Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md)|<span data-ttu-id="7c02d-111">Definir um grupo de async await operações no método atual.</span><span class="sxs-lookup"><span data-stu-id="7c02d-111">Define a group of async await operations in the current method.</span></span><br /><br /> <span data-ttu-id="7c02d-112">Cada deslocamento yield corresponde a instrução de retorno de uma espera, identificando um rendimento potencial.</span><span class="sxs-lookup"><span data-stu-id="7c02d-112">Each yield offset matches an await's return instruction, identifying a potential yield.</span></span> <span data-ttu-id="7c02d-113">Cada `breakpointMethod` / `breakpointOffset` par identifica onde continuará a operação assíncrona; pode estar em um método diferente.</span><span class="sxs-lookup"><span data-stu-id="7c02d-113">Each `breakpointMethod`/`breakpointOffset` pair identifies where the asynchronous operation will resume; it may be in a different method.</span></span>|  
|[<span data-ttu-id="7c02d-114">Método DefineCatchHandlerILOffset</span><span class="sxs-lookup"><span data-stu-id="7c02d-114">DefineCatchHandlerILOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md)|<span data-ttu-id="7c02d-115">Define o deslocamento para o manipulador catch gerado pelo compilador que encapsula um método assíncrono de IL.</span><span class="sxs-lookup"><span data-stu-id="7c02d-115">Sets the IL offset for the compiler-generated catch handler that wraps an async method.</span></span><br /><br /> <span data-ttu-id="7c02d-116">O deslocamento de IL de catch gerado é usado pelo depurador para tratar catch como se fosse o código não-usuário, mesmo que isso pode ocorrer em um método de código do usuário.</span><span class="sxs-lookup"><span data-stu-id="7c02d-116">The IL offset of the generated catch is used by the debugger to handle the catch as if it were non-user code, even though it may occur in a user code method.</span></span> <span data-ttu-id="7c02d-117">Em particular, ele é usado em resposta a um **CatchHandlerFound** eventos de exceção.</span><span class="sxs-lookup"><span data-stu-id="7c02d-117">In particular, it is used in response to a **CatchHandlerFound** exception event.</span></span>|  
|[<span data-ttu-id="7c02d-118">Método DefineKickoffMethod</span><span class="sxs-lookup"><span data-stu-id="7c02d-118">DefineKickoffMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md)|<span data-ttu-id="7c02d-119">Define o método inicial que inicia a operação assíncrona.</span><span class="sxs-lookup"><span data-stu-id="7c02d-119">Sets the starting method that initiates the async operation.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7c02d-120">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7c02d-120">Requirements</span></span>  
 <span data-ttu-id="7c02d-121">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="7c02d-121">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c02d-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7c02d-122">See Also</span></span>  
 [<span data-ttu-id="7c02d-123">Interfaces de armazenamento de símbolo de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="7c02d-123">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
