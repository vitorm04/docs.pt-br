---
title: Método ICorDebugManagedCallback::DebuggerError
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.DebuggerError
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::DebuggerError
helpviewer_keywords:
- DebuggerError method [.NET Framework debugging]
- ICorDebugManagedCallback::DebuggerError method [.NET Framework debugging]
ms.assetid: 9e983d11-eaf3-4741-b936-29ec456384a3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fd7909b94343b1fb83836f5c369ddc1993f049d2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59191162"
---
# <a name="icordebugmanagedcallbackdebuggererror-method"></a><span data-ttu-id="0e61f-102">Método ICorDebugManagedCallback::DebuggerError</span><span class="sxs-lookup"><span data-stu-id="0e61f-102">ICorDebugManagedCallback::DebuggerError Method</span></span>
<span data-ttu-id="0e61f-103">Notifica o depurador que ocorreu um erro durante a tentativa de manipular um evento do common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="0e61f-103">Notifies the debugger that an error has occurred while attempting to handle an event from the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e61f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0e61f-104">Syntax</span></span>  
  
```  
HRESULT DebuggerError (  
    [in] ICorDebugProcess *pProcess,  
    [in] HRESULT           errorHR,  
    [in] DWORD             errorCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0e61f-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0e61f-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="0e61f-106">[in] Um ponteiro para um objeto de "ICorDebugProcess" que representa o processo no qual o evento ocorreu.</span><span class="sxs-lookup"><span data-stu-id="0e61f-106">[in] A pointer to an "ICorDebugProcess" object that represents the process in which the event occurred.</span></span>  
  
 `errorHR`  
 <span data-ttu-id="0e61f-107">[in] O valor HRESULT retornado pelo manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="0e61f-107">[in] The HRESULT value that was returned from the event handler.</span></span>  
  
 `errorCode`  
 <span data-ttu-id="0e61f-108">[in] Um inteiro que especifica o erro CLR.</span><span class="sxs-lookup"><span data-stu-id="0e61f-108">[in] An integer that specifies the CLR error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0e61f-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="0e61f-109">Remarks</span></span>  
 <span data-ttu-id="0e61f-110">O processo pode ser colocado no modo de passagem, dependendo da natureza do erro.</span><span class="sxs-lookup"><span data-stu-id="0e61f-110">The process may be placed into pass-through mode, depending on the nature of the error.</span></span>  
  
 <span data-ttu-id="0e61f-111">O `DebugError` retorno de chamada indica que serviços de depuração foram desabilitados devido a um erro, portanto, os depuradores devem disponibilizar a mensagem de erro para o usuário.</span><span class="sxs-lookup"><span data-stu-id="0e61f-111">The `DebugError` callback indicates that debugging services have been disabled due to an error, so debuggers should make the error message available to the user.</span></span> <span data-ttu-id="0e61f-112">[Icordebugprocess:: GetID](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getid-method.md) estarão seguros para a chamada, mas todos os outros métodos, incluindo [icordebug:: Terminate](../../../../docs/framework/unmanaged-api/debugging/icordebug-terminate-method.md), não deve ser chamado.</span><span class="sxs-lookup"><span data-stu-id="0e61f-112">[ICorDebugProcess::GetID](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getid-method.md) will be safe to call, but all other methods, including [ICorDebug::Terminate](../../../../docs/framework/unmanaged-api/debugging/icordebug-terminate-method.md), should not be called.</span></span> <span data-ttu-id="0e61f-113">O depurador deve usar os recursos de sistema operacional para encerrar processos.</span><span class="sxs-lookup"><span data-stu-id="0e61f-113">The debugger should use operating-system facilities for terminating processes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0e61f-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0e61f-114">Requirements</span></span>  
 <span data-ttu-id="0e61f-115">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0e61f-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0e61f-116">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0e61f-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0e61f-117">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0e61f-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0e61f-118">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0e61f-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e61f-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0e61f-119">See also</span></span>

- [<span data-ttu-id="0e61f-120">Interface ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="0e61f-120">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
