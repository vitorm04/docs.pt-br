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
ms.openlocfilehash: c7ab77e9316023a97d2eafe8bcccc2b45e240cd0
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83207819"
---
# <a name="icordebugmdagetosthreadid-method"></a><span data-ttu-id="88761-102">Método ICorDebugMDA::GetOSThreadId</span><span class="sxs-lookup"><span data-stu-id="88761-102">ICorDebugMDA::GetOSThreadId Method</span></span>
<span data-ttu-id="88761-103">Obtém o identificador de thread do sistema operacional no qual o MDA (Assistente de depuração gerenciada) representado por [ICorDebugMDA](icordebugmda-interface.md) está em execução.</span><span class="sxs-lookup"><span data-stu-id="88761-103">Gets the operating system (OS) thread identifier upon which the managed debugging assistant (MDA) represented by [ICorDebugMDA](icordebugmda-interface.md) is executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="88761-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="88761-104">Syntax</span></span>  
  
```cpp  
HRESULT GetOSThreadId (  
    [out] DWORD    *pOsTid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="88761-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="88761-105">Parameters</span></span>  
 `pOsTid`  
 <span data-ttu-id="88761-106">fora Um ponteiro para o identificador de thread do sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="88761-106">[out] A pointer to the OS thread identifier.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="88761-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="88761-107">Remarks</span></span>  
 <span data-ttu-id="88761-108">O thread do sistema operacional é usado em vez de um ICorDebugThread para permitir situações em que um MDA seja acionado em um thread nativo ou em um thread gerenciado que ainda não tenha inserido código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="88761-108">The OS thread is used instead of an ICorDebugThread to allow for situations in which an MDA is fired either on a native thread or on a managed thread that has not yet entered managed code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="88761-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="88761-109">Requirements</span></span>  
 <span data-ttu-id="88761-110">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="88761-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="88761-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="88761-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="88761-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="88761-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="88761-113">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="88761-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88761-114">Confira também</span><span class="sxs-lookup"><span data-stu-id="88761-114">See also</span></span>

- [<span data-ttu-id="88761-115">Interface ICorDebugMDA</span><span class="sxs-lookup"><span data-stu-id="88761-115">ICorDebugMDA Interface</span></span>](icordebugmda-interface.md)
- [<span data-ttu-id="88761-116">Diagnosticando erros com assistentes para depuração gerenciada</span><span class="sxs-lookup"><span data-stu-id="88761-116">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
