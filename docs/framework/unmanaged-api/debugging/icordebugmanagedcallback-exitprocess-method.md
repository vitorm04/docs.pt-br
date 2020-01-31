---
title: Método ICorDebugManagedCallback::ExitProcess
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.ExitProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::ExitProcess
helpviewer_keywords:
- ExitProcess method, ICorDebugManagedCallback interface [.NET Framework debugging]
- ICorDebugManagedCallback::ExitProcess method [.NET Framework debugging]
ms.assetid: 63a7d47a-0d54-4e29-9767-9f09feaa38b7
topic_type:
- apiref
ms.openlocfilehash: 4380b8a3803e164aab7318821a9dbde32ecc3a0b
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76781747"
---
# <a name="icordebugmanagedcallbackexitprocess-method"></a><span data-ttu-id="5286d-102">Método ICorDebugManagedCallback::ExitProcess</span><span class="sxs-lookup"><span data-stu-id="5286d-102">ICorDebugManagedCallback::ExitProcess Method</span></span>
<span data-ttu-id="5286d-103">Notifica o depurador de que um processo foi encerrado.</span><span class="sxs-lookup"><span data-stu-id="5286d-103">Notifies the debugger that a process has exited.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5286d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5286d-104">Syntax</span></span>  
  
```cpp  
HRESULT ExitProcess (  
    [in] ICorDebugProcess *pProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5286d-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5286d-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="5286d-106">no Um ponteiro para um objeto ICorDebugProcess que representa o processo.</span><span class="sxs-lookup"><span data-stu-id="5286d-106">[in] A pointer to an ICorDebugProcess object that represents the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5286d-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="5286d-107">Remarks</span></span>  
 <span data-ttu-id="5286d-108">Não é possível continuar a partir de um evento `ExitProcess`.</span><span class="sxs-lookup"><span data-stu-id="5286d-108">You cannot continue from an `ExitProcess` event.</span></span> <span data-ttu-id="5286d-109">Esse evento pode ser acionado de forma assíncrona a outros eventos enquanto o processo parece estar parado.</span><span class="sxs-lookup"><span data-stu-id="5286d-109">This event may fire asynchronously to other events while the process appears to be stopped.</span></span> <span data-ttu-id="5286d-110">Isso pode ocorrer se o processo for encerrado enquanto é interrompido, geralmente devido a alguma força externa.</span><span class="sxs-lookup"><span data-stu-id="5286d-110">This can occur if the process terminates while stopped, usually due to some external force.</span></span>  
  
 <span data-ttu-id="5286d-111">Se o Common Language Runtime (CLR) já estiver expedindo um retorno de chamada gerenciado, esse evento será atrasado até que o retorno de chamada seja retornado.</span><span class="sxs-lookup"><span data-stu-id="5286d-111">If the common language runtime (CLR) is already dispatching a managed callback, this event will be delayed until after that callback has returned.</span></span>  
  
 <span data-ttu-id="5286d-112">O evento `ExitProcess` é o único evento Exit/Unload que é garantido para ser chamado no desligamento.</span><span class="sxs-lookup"><span data-stu-id="5286d-112">The `ExitProcess` event is the only exit/unload event that is guaranteed to get called on shutdown.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5286d-113">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="5286d-113">Requirements</span></span>  
 <span data-ttu-id="5286d-114">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5286d-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5286d-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5286d-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5286d-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5286d-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5286d-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5286d-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5286d-118">Veja também</span><span class="sxs-lookup"><span data-stu-id="5286d-118">See also</span></span>

- [<span data-ttu-id="5286d-119">Interface ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="5286d-119">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
