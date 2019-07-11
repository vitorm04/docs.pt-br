---
title: Método ICorDebugMDA::GetOSThreadId
ms.date: 03/30/2017
api_name:
- ICorDebugMDA.GetOSThreadId
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugMDA::GetOSThreadId
helpviewer_keywords:
- ICorDebugMDA::GetOSThreadId method [.NET Framework debugging]
- GetOSThreadId method [.NET Framework debugging]
ms.assetid: 7ca7c364-ade4-4219-b434-9f6ae2359be6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a5d676e0fad33ca994b2e5bcd7adf269e306cb55
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67761928"
---
# <a name="icordebugmdagetosthreadid-method"></a><span data-ttu-id="0dd5c-102">Método ICorDebugMDA::GetOSThreadId</span><span class="sxs-lookup"><span data-stu-id="0dd5c-102">ICorDebugMDA::GetOSThreadId Method</span></span>
<span data-ttu-id="0dd5c-103">Obtém o identificador de thread do sistema operacional (SO) no qual o Assistente para depuração gerenciada (MDA) representado por [ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md) está em execução.</span><span class="sxs-lookup"><span data-stu-id="0dd5c-103">Gets the operating system (OS) thread identifier upon which the managed debugging assistant (MDA) represented by [ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md) is executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0dd5c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0dd5c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetOSThreadId (  
    [out] DWORD    *pOsTid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0dd5c-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0dd5c-105">Parameters</span></span>  
 `pOsTid`  
 <span data-ttu-id="0dd5c-106">[out] Um ponteiro para o identificador de thread do sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="0dd5c-106">[out] A pointer to the OS thread identifier.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0dd5c-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="0dd5c-107">Remarks</span></span>  
 <span data-ttu-id="0dd5c-108">O thread de sistema operacional é usado em vez de um ICorDebugThread para situações em que um MDA é acionado em um thread nativo ou em um thread gerenciado que ainda não tenha entrado em código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="0dd5c-108">The OS thread is used instead of an ICorDebugThread to allow for situations in which an MDA is fired either on a native thread or on a managed thread that has not yet entered managed code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0dd5c-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0dd5c-109">Requirements</span></span>  
 <span data-ttu-id="0dd5c-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0dd5c-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0dd5c-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0dd5c-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0dd5c-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0dd5c-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0dd5c-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0dd5c-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0dd5c-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0dd5c-114">See also</span></span>

- [<span data-ttu-id="0dd5c-115">Interface ICorDebugMDA</span><span class="sxs-lookup"><span data-stu-id="0dd5c-115">ICorDebugMDA Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md)
- [<span data-ttu-id="0dd5c-116">Diagnosticando erros com Assistentes de Depuração Gerenciados</span><span class="sxs-lookup"><span data-stu-id="0dd5c-116">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
