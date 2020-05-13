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
ms.openlocfilehash: c60af0ccfb143e68be3b987b0caf92fe3d992b4d
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212695"
---
# <a name="icordebugmanagedcallbacklogmessage-method"></a><span data-ttu-id="ab216-102">Método ICorDebugManagedCallback::LogMessage</span><span class="sxs-lookup"><span data-stu-id="ab216-102">ICorDebugManagedCallback::LogMessage Method</span></span>
<span data-ttu-id="ab216-103">Notifica o depurador de que um thread gerenciado Common Language Runtime (CLR) chamou um método na <xref:System.Diagnostics.EventLog> classe para registrar um evento.</span><span class="sxs-lookup"><span data-stu-id="ab216-103">Notifies the debugger that a common language runtime (CLR) managed thread has called a method in the <xref:System.Diagnostics.EventLog> class to log an event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab216-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ab216-104">Syntax</span></span>  
  
```cpp  
HRESULT LogMessage (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugThread     *pThread,  
    [in] LONG                 lLevel,  
    [in] WCHAR               *pLogSwitchName,  
    [in] WCHAR               *pMessage  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ab216-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ab216-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="ab216-106">no Um ponteiro para um objeto ICorDebugAppDomain que representa o domínio do aplicativo que contém o thread gerenciado que registrou o evento.</span><span class="sxs-lookup"><span data-stu-id="ab216-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the managed thread that logged the event.</span></span>  
  
 `pThread`  
 <span data-ttu-id="ab216-107">no Um ponteiro para um objeto ICorDebugThread que representa o thread gerenciado.</span><span class="sxs-lookup"><span data-stu-id="ab216-107">[in] A pointer to an ICorDebugThread object that represents the managed thread.</span></span>  
  
 `lLevel`  
 <span data-ttu-id="ab216-108">no Um valor da enumeração [LoggingLevelEnum](logginglevelenum-enumeration.md) que indica o nível de severidade da mensagem descritiva que foi gravada no log de eventos.</span><span class="sxs-lookup"><span data-stu-id="ab216-108">[in] A value of the [LoggingLevelEnum](logginglevelenum-enumeration.md) enumeration that indicates the severity level of the descriptive message that was written to the event log.</span></span>  
  
 `pLogSwitchName`  
 <span data-ttu-id="ab216-109">no Um ponteiro para o nome da opção de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="ab216-109">[in] A pointer to the name of the tracing switch.</span></span>  
  
 `pMessage`  
 <span data-ttu-id="ab216-110">no Um ponteiro para a mensagem que foi gravada no log de eventos.</span><span class="sxs-lookup"><span data-stu-id="ab216-110">[in] A pointer to the message that was written to the event log.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ab216-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ab216-111">Requirements</span></span>  
 <span data-ttu-id="ab216-112">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ab216-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ab216-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ab216-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ab216-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ab216-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ab216-115">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ab216-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab216-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="ab216-116">See also</span></span>

- [<span data-ttu-id="ab216-117">Interface ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="ab216-117">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
