---
title: Método ICorDebugManagedCallback::LogMessage
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.LogMessage
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::LogMessage
helpviewer_keywords:
- ICorDebugManagedCallback::LogMessage method [.NET Framework debugging]
- LogMessage method [.NET Framework debugging]
ms.assetid: d218554a-bf42-4d88-833d-ede30de67a53
topic_type:
- apiref
ms.openlocfilehash: 4306c4ae44b0ae1ade2bf374981492fa1a4df76f
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788374"
---
# <a name="icordebugmanagedcallbacklogmessage-method"></a><span data-ttu-id="b9a31-102">Método ICorDebugManagedCallback::LogMessage</span><span class="sxs-lookup"><span data-stu-id="b9a31-102">ICorDebugManagedCallback::LogMessage Method</span></span>
<span data-ttu-id="b9a31-103">Notifica o depurador de que um thread gerenciado Common Language Runtime (CLR) chamou um método na classe <xref:System.Diagnostics.EventLog> para registrar um evento.</span><span class="sxs-lookup"><span data-stu-id="b9a31-103">Notifies the debugger that a common language runtime (CLR) managed thread has called a method in the <xref:System.Diagnostics.EventLog> class to log an event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b9a31-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b9a31-104">Syntax</span></span>  
  
```cpp  
HRESULT LogMessage (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugThread     *pThread,  
    [in] LONG                 lLevel,  
    [in] WCHAR               *pLogSwitchName,  
    [in] WCHAR               *pMessage  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b9a31-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b9a31-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="b9a31-106">no Um ponteiro para um objeto ICorDebugAppDomain que representa o domínio do aplicativo que contém o thread gerenciado que registrou o evento.</span><span class="sxs-lookup"><span data-stu-id="b9a31-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the managed thread that logged the event.</span></span>  
  
 `pThread`  
 <span data-ttu-id="b9a31-107">no Um ponteiro para um objeto ICorDebugThread que representa o thread gerenciado.</span><span class="sxs-lookup"><span data-stu-id="b9a31-107">[in] A pointer to an ICorDebugThread object that represents the managed thread.</span></span>  
  
 `lLevel`  
 <span data-ttu-id="b9a31-108">no Um valor da enumeração [LoggingLevelEnum](logginglevelenum-enumeration.md) que indica o nível de severidade da mensagem descritiva que foi gravada no log de eventos.</span><span class="sxs-lookup"><span data-stu-id="b9a31-108">[in] A value of the [LoggingLevelEnum](logginglevelenum-enumeration.md) enumeration that indicates the severity level of the descriptive message that was written to the event log.</span></span>  
  
 `pLogSwitchName`  
 <span data-ttu-id="b9a31-109">no Um ponteiro para o nome da opção de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="b9a31-109">[in] A pointer to the name of the tracing switch.</span></span>  
  
 `pMessage`  
 <span data-ttu-id="b9a31-110">no Um ponteiro para a mensagem que foi gravada no log de eventos.</span><span class="sxs-lookup"><span data-stu-id="b9a31-110">[in] A pointer to the message that was written to the event log.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b9a31-111">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="b9a31-111">Requirements</span></span>  
 <span data-ttu-id="b9a31-112">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b9a31-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b9a31-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b9a31-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b9a31-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b9a31-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b9a31-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b9a31-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9a31-116">Veja também</span><span class="sxs-lookup"><span data-stu-id="b9a31-116">See also</span></span>

- [<span data-ttu-id="b9a31-117">Interface ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="b9a31-117">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
