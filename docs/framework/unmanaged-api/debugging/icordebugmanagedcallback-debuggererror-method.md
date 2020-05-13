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
ms.openlocfilehash: 8f3697f8b193319ebb7b155ad79b8ec25a0a2266
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83205272"
---
# <a name="icordebugmanagedcallbackdebuggererror-method"></a><span data-ttu-id="7db9a-102">Método ICorDebugManagedCallback::DebuggerError</span><span class="sxs-lookup"><span data-stu-id="7db9a-102">ICorDebugManagedCallback::DebuggerError Method</span></span>
<span data-ttu-id="7db9a-103">Notifica o depurador de que ocorreu um erro ao tentar lidar com um evento do Common Language Runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="7db9a-103">Notifies the debugger that an error has occurred while attempting to handle an event from the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7db9a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7db9a-104">Syntax</span></span>  
  
```cpp  
HRESULT DebuggerError (  
    [in] ICorDebugProcess *pProcess,  
    [in] HRESULT           errorHR,  
    [in] DWORD             errorCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7db9a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7db9a-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="7db9a-106">no Um ponteiro para um objeto "ICorDebugProcess" que representa o processo no qual o evento ocorreu.</span><span class="sxs-lookup"><span data-stu-id="7db9a-106">[in] A pointer to an "ICorDebugProcess" object that represents the process in which the event occurred.</span></span>  
  
 `errorHR`  
 <span data-ttu-id="7db9a-107">no O valor HRESULT que foi retornado do manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="7db9a-107">[in] The HRESULT value that was returned from the event handler.</span></span>  
  
 `errorCode`  
 <span data-ttu-id="7db9a-108">no Um inteiro que especifica o erro CLR.</span><span class="sxs-lookup"><span data-stu-id="7db9a-108">[in] An integer that specifies the CLR error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7db9a-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="7db9a-109">Remarks</span></span>  
 <span data-ttu-id="7db9a-110">O processo pode ser colocado em modo de passagem, dependendo da natureza do erro.</span><span class="sxs-lookup"><span data-stu-id="7db9a-110">The process may be placed into pass-through mode, depending on the nature of the error.</span></span>  
  
 <span data-ttu-id="7db9a-111">O `DebugError` retorno de chamada indica que os serviços de depuração foram desabilitados devido a um erro, portanto, os depuradores devem tornar a mensagem de erro disponível para o usuário.</span><span class="sxs-lookup"><span data-stu-id="7db9a-111">The `DebugError` callback indicates that debugging services have been disabled due to an error, so debuggers should make the error message available to the user.</span></span> <span data-ttu-id="7db9a-112">[ICorDebugProcess:: GetID](icordebugprocess-getid-method.md) será seguro chamar, mas todos os outros métodos, incluindo [ICorDebug:: Terminate](icordebug-terminate-method.md), não devem ser chamados.</span><span class="sxs-lookup"><span data-stu-id="7db9a-112">[ICorDebugProcess::GetID](icordebugprocess-getid-method.md) will be safe to call, but all other methods, including [ICorDebug::Terminate](icordebug-terminate-method.md), should not be called.</span></span> <span data-ttu-id="7db9a-113">O depurador deve usar recursos do sistema operacional para encerrar processos.</span><span class="sxs-lookup"><span data-stu-id="7db9a-113">The debugger should use operating-system facilities for terminating processes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7db9a-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7db9a-114">Requirements</span></span>  
 <span data-ttu-id="7db9a-115">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7db9a-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7db9a-116">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7db9a-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7db9a-117">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7db9a-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7db9a-118">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7db9a-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7db9a-119">Confira também</span><span class="sxs-lookup"><span data-stu-id="7db9a-119">See also</span></span>

- [<span data-ttu-id="7db9a-120">Interface ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="7db9a-120">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
