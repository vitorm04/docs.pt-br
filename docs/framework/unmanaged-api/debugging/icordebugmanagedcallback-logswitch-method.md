---
title: Método ICorDebugManagedCallback::LogSwitch
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.LogSwitch
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::LogSwitch
helpviewer_keywords:
- LogSwitch method [.NET Framework debugging]
- ICorDebugManagedCallback::LogSwitch method [.NET Framework debugging]
ms.assetid: 0ac59d27-783f-4a87-b7a8-baa3ccc54582
topic_type:
- apiref
ms.openlocfilehash: a72eabb1b405c67f5603164e56a589a237603d2f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130689"
---
# <a name="icordebugmanagedcallbacklogswitch-method"></a><span data-ttu-id="27772-102">Método ICorDebugManagedCallback::LogSwitch</span><span class="sxs-lookup"><span data-stu-id="27772-102">ICorDebugManagedCallback::LogSwitch Method</span></span>
<span data-ttu-id="27772-103">Notifica o depurador de que um thread gerenciado Common Language Runtime (CLR) chamou um método na classe <xref:System.Diagnostics.Switch> para criar, modificar ou excluir uma opção de depuração/rastreamento.</span><span class="sxs-lookup"><span data-stu-id="27772-103">Notifies the debugger that a common language runtime (CLR) managed thread has called a method in the <xref:System.Diagnostics.Switch> class to create, modify, or delete a debugging/tracing switch.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27772-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="27772-104">Syntax</span></span>  
  
```cpp  
HRESULT LogSwitch (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugThread     *pThread,  
    [in] LONG                 lLevel,  
    [in] ULONG                ulReason,  
    [in] WCHAR               *pLogSwitchName,  
    [in] WCHAR               *pParentName);  
```  
  
## <a name="parameters"></a><span data-ttu-id="27772-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="27772-105">Parameters</span></span>  
 `PAppDomain`  
 <span data-ttu-id="27772-106">no Um ponteiro para um objeto ICorDebugAppDomain que representa o domínio do aplicativo que contém o thread gerenciado que criou, modificou ou excluiu uma opção de depuração/rastreamento.</span><span class="sxs-lookup"><span data-stu-id="27772-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the managed thread that created, modified, or deleted a debugging/tracing switch.</span></span>  
  
 `pThread`  
 <span data-ttu-id="27772-107">no Um ponteiro para um objeto ICorDebugThread que representa o thread gerenciado.</span><span class="sxs-lookup"><span data-stu-id="27772-107">[in] A pointer to an ICorDebugThread object that represents the managed thread.</span></span>  
  
 `lLevel`  
 <span data-ttu-id="27772-108">no Um valor que indica o nível de severidade da mensagem descritiva que foi gravada no log de eventos.</span><span class="sxs-lookup"><span data-stu-id="27772-108">[in] A value that indicates the severity level of the descriptive message that was written to the event log.</span></span>  
  
 `ulReason`  
 <span data-ttu-id="27772-109">no Um valor da enumeração [LogSwitchCallReason](../../../../docs/framework/unmanaged-api/debugging/logswitchcallreason-enumeration.md) que indica a operação executada na opção de depuração/rastreamento.</span><span class="sxs-lookup"><span data-stu-id="27772-109">[in] A value of the [LogSwitchCallReason](../../../../docs/framework/unmanaged-api/debugging/logswitchcallreason-enumeration.md) enumeration that indicates the operation performed on the debugging/tracing switch.</span></span>  
  
 `pLogSwitchName`  
 <span data-ttu-id="27772-110">no Um ponteiro para o nome da opção de depuração/rastreamento.</span><span class="sxs-lookup"><span data-stu-id="27772-110">[in] A pointer to the name of the debugging/tracing switch.</span></span>  
  
 `pParentName`  
 <span data-ttu-id="27772-111">no Um ponteiro para o nome do pai da opção de depuração/rastreamento.</span><span class="sxs-lookup"><span data-stu-id="27772-111">[in] A pointer to the name of the parent of the debugging/tracing switch.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="27772-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="27772-112">Requirements</span></span>  
 <span data-ttu-id="27772-113">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="27772-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="27772-114">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="27772-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="27772-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="27772-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="27772-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="27772-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27772-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="27772-117">See also</span></span>

- [<span data-ttu-id="27772-118">Interface ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="27772-118">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
