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
ms.openlocfilehash: 3d5284cf6072aa5c1c11cc83355a3e9fa5c96837
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33415916"
---
# <a name="icordebugmanagedcallbacklogswitch-method"></a><span data-ttu-id="276b9-102">Método ICorDebugManagedCallback::LogSwitch</span><span class="sxs-lookup"><span data-stu-id="276b9-102">ICorDebugManagedCallback::LogSwitch Method</span></span>
<span data-ttu-id="276b9-103">Notifica o depurador um thread de runtime (CLR) gerenciado de linguagem comum chamou um método em de <xref:System.Diagnostics.Switch> classe para criar, modificar ou excluir um comutador/rastreamento de depuração.</span><span class="sxs-lookup"><span data-stu-id="276b9-103">Notifies the debugger that a common language runtime (CLR) managed thread has called a method in the <xref:System.Diagnostics.Switch> class to create, modify, or delete a debugging/tracing switch.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="276b9-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="276b9-104">Syntax</span></span>  
  
```  
HRESULT LogSwitch (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugThread     *pThread,  
    [in] LONG                 lLevel,  
    [in] ULONG                ulReason,  
    [in] WCHAR               *pLogSwitchName,  
    [in] WCHAR               *pParentName);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="276b9-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="276b9-105">Parameters</span></span>  
 `PAppDomain`  
 <span data-ttu-id="276b9-106">[in] Um ponteiro para um objeto ICorDebugAppDomain que representa o domínio de aplicativo que contém o thread gerenciado que são criados, modificados ou excluídos de um comutador/rastreamento de depuração.</span><span class="sxs-lookup"><span data-stu-id="276b9-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the managed thread that created, modified, or deleted a debugging/tracing switch.</span></span>  
  
 `pThread`  
 <span data-ttu-id="276b9-107">[in] Um ponteiro para um objeto ICorDebugThread que representa o thread gerenciado.</span><span class="sxs-lookup"><span data-stu-id="276b9-107">[in] A pointer to an ICorDebugThread object that represents the managed thread.</span></span>  
  
 `lLevel`  
 <span data-ttu-id="276b9-108">[in] Um valor que indica o nível de severidade da mensagem descritiva que foram gravado no log de eventos.</span><span class="sxs-lookup"><span data-stu-id="276b9-108">[in] A value that indicates the severity level of the descriptive message that was written to the event log.</span></span>  
  
 `ulReason`  
 <span data-ttu-id="276b9-109">[in] Um valor de [LogSwitchCallReason](../../../../docs/framework/unmanaged-api/debugging/logswitchcallreason-enumeration.md) enumeração que indica a operação executada no comutador/rastreamento de depuração.</span><span class="sxs-lookup"><span data-stu-id="276b9-109">[in] A value of the [LogSwitchCallReason](../../../../docs/framework/unmanaged-api/debugging/logswitchcallreason-enumeration.md) enumeration that indicates the operation performed on the debugging/tracing switch.</span></span>  
  
 `pLogSwitchName`  
 <span data-ttu-id="276b9-110">[in] Um ponteiro para o nome do comutador/rastreamento de depuração.</span><span class="sxs-lookup"><span data-stu-id="276b9-110">[in] A pointer to the name of the debugging/tracing switch.</span></span>  
  
 `pParentName`  
 <span data-ttu-id="276b9-111">[in] Um ponteiro para o nome do pai do comutador/rastreamento de depuração.</span><span class="sxs-lookup"><span data-stu-id="276b9-111">[in] A pointer to the name of the parent of the debugging/tracing switch.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="276b9-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="276b9-112">Requirements</span></span>  
 <span data-ttu-id="276b9-113">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="276b9-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="276b9-114">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="276b9-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="276b9-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="276b9-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="276b9-116">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="276b9-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="276b9-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="276b9-117">See Also</span></span>  
 [<span data-ttu-id="276b9-118">Interface ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="276b9-118">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
