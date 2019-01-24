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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4b8e0807cd03c7abfee0856d52cae0454b9f1a29
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54587785"
---
# <a name="icordebugmanagedcallbacklogswitch-method"></a><span data-ttu-id="d8957-102">Método ICorDebugManagedCallback::LogSwitch</span><span class="sxs-lookup"><span data-stu-id="d8957-102">ICorDebugManagedCallback::LogSwitch Method</span></span>
<span data-ttu-id="d8957-103">Notifica o depurador um thread de runtime (CLR) gerenciado de linguagem comum chamou um método no <xref:System.Diagnostics.Switch> classe para criar, modificar ou excluir um comutador de depuração/rastreamento.</span><span class="sxs-lookup"><span data-stu-id="d8957-103">Notifies the debugger that a common language runtime (CLR) managed thread has called a method in the <xref:System.Diagnostics.Switch> class to create, modify, or delete a debugging/tracing switch.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8957-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d8957-104">Syntax</span></span>  
  
```  
HRESULT LogSwitch (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugThread     *pThread,  
    [in] LONG                 lLevel,  
    [in] ULONG                ulReason,  
    [in] WCHAR               *pLogSwitchName,  
    [in] WCHAR               *pParentName);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d8957-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d8957-105">Parameters</span></span>  
 `PAppDomain`  
 <span data-ttu-id="d8957-106">[in] Um ponteiro para um objeto ICorDebugAppDomain que representa o domínio de aplicativo que contém o thread gerenciado que criados, modificados ou excluídos de um comutador de depuração/rastreamento.</span><span class="sxs-lookup"><span data-stu-id="d8957-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the managed thread that created, modified, or deleted a debugging/tracing switch.</span></span>  
  
 `pThread`  
 <span data-ttu-id="d8957-107">[in] Um ponteiro para um objeto de ICorDebugThread que representa o thread gerenciado.</span><span class="sxs-lookup"><span data-stu-id="d8957-107">[in] A pointer to an ICorDebugThread object that represents the managed thread.</span></span>  
  
 `lLevel`  
 <span data-ttu-id="d8957-108">[in] Um valor que indica o nível de severidade da mensagem descritiva que foi gravado no log de eventos.</span><span class="sxs-lookup"><span data-stu-id="d8957-108">[in] A value that indicates the severity level of the descriptive message that was written to the event log.</span></span>  
  
 `ulReason`  
 <span data-ttu-id="d8957-109">[in] Um valor igual a [LogSwitchCallReason](../../../../docs/framework/unmanaged-api/debugging/logswitchcallreason-enumeration.md) a enumeração que indica a operação realizada no comutador/rastreamento de depuração.</span><span class="sxs-lookup"><span data-stu-id="d8957-109">[in] A value of the [LogSwitchCallReason](../../../../docs/framework/unmanaged-api/debugging/logswitchcallreason-enumeration.md) enumeration that indicates the operation performed on the debugging/tracing switch.</span></span>  
  
 `pLogSwitchName`  
 <span data-ttu-id="d8957-110">[in] Um ponteiro para o nome do comutador/rastreamento de depuração.</span><span class="sxs-lookup"><span data-stu-id="d8957-110">[in] A pointer to the name of the debugging/tracing switch.</span></span>  
  
 `pParentName`  
 <span data-ttu-id="d8957-111">[in] Um ponteiro para o nome do pai do comutador/rastreamento de depuração.</span><span class="sxs-lookup"><span data-stu-id="d8957-111">[in] A pointer to the name of the parent of the debugging/tracing switch.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d8957-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d8957-112">Requirements</span></span>  
 <span data-ttu-id="d8957-113">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d8957-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d8957-114">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d8957-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d8957-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d8957-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d8957-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d8957-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8957-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d8957-117">See also</span></span>
- [<span data-ttu-id="d8957-118">Interface ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="d8957-118">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
