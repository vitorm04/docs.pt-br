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
ms.openlocfilehash: 7a49bd6626518179c9b5ef008fca28d304537cc8
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83205256"
---
# <a name="icordebugmanagedcallbackexitprocess-method"></a><span data-ttu-id="7737b-102">Método ICorDebugManagedCallback::ExitProcess</span><span class="sxs-lookup"><span data-stu-id="7737b-102">ICorDebugManagedCallback::ExitProcess Method</span></span>
<span data-ttu-id="7737b-103">Notifica o depurador de que um processo foi encerrado.</span><span class="sxs-lookup"><span data-stu-id="7737b-103">Notifies the debugger that a process has exited.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7737b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7737b-104">Syntax</span></span>  
  
```cpp  
HRESULT ExitProcess (  
    [in] ICorDebugProcess *pProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7737b-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7737b-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="7737b-106">no Um ponteiro para um objeto ICorDebugProcess que representa o processo.</span><span class="sxs-lookup"><span data-stu-id="7737b-106">[in] A pointer to an ICorDebugProcess object that represents the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7737b-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="7737b-107">Remarks</span></span>  
 <span data-ttu-id="7737b-108">Você não pode continuar a partir de um `ExitProcess` evento.</span><span class="sxs-lookup"><span data-stu-id="7737b-108">You cannot continue from an `ExitProcess` event.</span></span> <span data-ttu-id="7737b-109">Esse evento pode ser acionado de forma assíncrona a outros eventos enquanto o processo parece estar parado.</span><span class="sxs-lookup"><span data-stu-id="7737b-109">This event may fire asynchronously to other events while the process appears to be stopped.</span></span> <span data-ttu-id="7737b-110">Isso pode ocorrer se o processo for encerrado enquanto é interrompido, geralmente devido a alguma força externa.</span><span class="sxs-lookup"><span data-stu-id="7737b-110">This can occur if the process terminates while stopped, usually due to some external force.</span></span>  
  
 <span data-ttu-id="7737b-111">Se o Common Language Runtime (CLR) já estiver expedindo um retorno de chamada gerenciado, esse evento será atrasado até que o retorno de chamada seja retornado.</span><span class="sxs-lookup"><span data-stu-id="7737b-111">If the common language runtime (CLR) is already dispatching a managed callback, this event will be delayed until after that callback has returned.</span></span>  
  
 <span data-ttu-id="7737b-112">O `ExitProcess` evento é o único evento Exit/Unload que é garantido para ser chamado no desligamento.</span><span class="sxs-lookup"><span data-stu-id="7737b-112">The `ExitProcess` event is the only exit/unload event that is guaranteed to get called on shutdown.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7737b-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7737b-113">Requirements</span></span>  
 <span data-ttu-id="7737b-114">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7737b-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7737b-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7737b-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7737b-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7737b-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7737b-117">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7737b-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7737b-118">Confira também</span><span class="sxs-lookup"><span data-stu-id="7737b-118">See also</span></span>

- [<span data-ttu-id="7737b-119">Interface ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="7737b-119">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
