---
title: "Método ICorDebugManagedCallback::LogMessage"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugManagedCallback.LogMessage
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugManagedCallback::LogMessage
helpviewer_keywords:
- ICorDebugManagedCallback::LogMessage method [.NET Framework debugging]
- LogMessage method [.NET Framework debugging]
ms.assetid: d218554a-bf42-4d88-833d-ede30de67a53
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f06e737498f2c12b041467f5f66de55c602615f3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugmanagedcallbacklogmessage-method"></a><span data-ttu-id="d64f4-102">Método ICorDebugManagedCallback::LogMessage</span><span class="sxs-lookup"><span data-stu-id="d64f4-102">ICorDebugManagedCallback::LogMessage Method</span></span>
<span data-ttu-id="d64f4-103">Notifica o depurador um thread de runtime (CLR) gerenciado de linguagem comum chamou um método em de <xref:System.Diagnostics.EventLog> classe para registrar um evento.</span><span class="sxs-lookup"><span data-stu-id="d64f4-103">Notifies the debugger that a common language runtime (CLR) managed thread has called a method in the <xref:System.Diagnostics.EventLog> class to log an event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d64f4-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d64f4-104">Syntax</span></span>  
  
```  
HRESULT LogMessage (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugThread     *pThread,  
    [in] LONG                 lLevel,  
    [in] WCHAR               *pLogSwitchName,  
    [in] WCHAR               *pMessage  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d64f4-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d64f4-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="d64f4-106">[in] Um ponteiro para um objeto ICorDebugAppDomain que representa o domínio de aplicativo que contém o thread gerenciado que registrou o evento.</span><span class="sxs-lookup"><span data-stu-id="d64f4-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the managed thread that logged the event.</span></span>  
  
 `pThread`  
 <span data-ttu-id="d64f4-107">[in] Um ponteiro para um objeto ICorDebugThread que representa o thread gerenciado.</span><span class="sxs-lookup"><span data-stu-id="d64f4-107">[in] A pointer to an ICorDebugThread object that represents the managed thread.</span></span>  
  
 `lLevel`  
 <span data-ttu-id="d64f4-108">[in] Um valor de [LoggingLevelEnum](../../../../docs/framework/unmanaged-api/debugging/logginglevelenum-enumeration.md) enumeração que indica o nível de severidade da mensagem descritiva que foram gravado no log de eventos.</span><span class="sxs-lookup"><span data-stu-id="d64f4-108">[in] A value of the [LoggingLevelEnum](../../../../docs/framework/unmanaged-api/debugging/logginglevelenum-enumeration.md) enumeration that indicates the severity level of the descriptive message that was written to the event log.</span></span>  
  
 `pLogSwitchName`  
 <span data-ttu-id="d64f4-109">[in] Um ponteiro para o nome da opção de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="d64f4-109">[in] A pointer to the name of the tracing switch.</span></span>  
  
 `pMessage`  
 <span data-ttu-id="d64f4-110">[in] Um ponteiro para a mensagem que foram gravado no log de eventos.</span><span class="sxs-lookup"><span data-stu-id="d64f4-110">[in] A pointer to the message that was written to the event log.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d64f4-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d64f4-111">Requirements</span></span>  
 <span data-ttu-id="d64f4-112">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d64f4-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d64f4-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d64f4-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d64f4-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d64f4-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d64f4-115">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d64f4-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d64f4-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d64f4-116">See Also</span></span>  
 [<span data-ttu-id="d64f4-117">Interface ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="d64f4-117">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
