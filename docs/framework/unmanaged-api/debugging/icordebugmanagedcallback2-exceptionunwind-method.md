---
title: "Método ICorDebugManagedCallback2::ExceptionUnwind"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugManagedCallback2.ExceptionUnwind
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugManagedCallback2::ExceptionUnwind
helpviewer_keywords:
- ICorDebugManagedCallback2::ExceptionUnwind method [.NET Framework debugging]
- ExceptionUnwind method [.NET Framework debugging]
ms.assetid: aaf5938d-179c-4eaa-8d35-8523a4fadded
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 64b85311f625e39dd25c48a60dde2fbaf66a957f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmanagedcallback2exceptionunwind-method"></a><span data-ttu-id="f1c63-102">Método ICorDebugManagedCallback2::ExceptionUnwind</span><span class="sxs-lookup"><span data-stu-id="f1c63-102">ICorDebugManagedCallback2::ExceptionUnwind Method</span></span>
<span data-ttu-id="f1c63-103">Fornece uma notificação de status durante o processo de desenrolamento da exceção.</span><span class="sxs-lookup"><span data-stu-id="f1c63-103">Provides a status notification during the exception unwinding process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1c63-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f1c63-104">Syntax</span></span>  
  
```  
HRESULT ExceptionUnwind (  
    [in] ICorDebugAppDomain                  *pAppDomain,  
    [in] ICorDebugThread                     *pThread,  
    [in] CorDebugExceptionUnwindCallbackType  dwEventType,  
    [in] DWORD                                dwFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f1c63-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f1c63-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="f1c63-106">[in] Um ponteiro para um objeto ICorDebugAppDomain que representa o domínio de aplicativo que contém o segmento em que a exceção foi lançada.</span><span class="sxs-lookup"><span data-stu-id="f1c63-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the thread on which the exception was thrown.</span></span>  
  
 `pThread`  
 <span data-ttu-id="f1c63-107">[in] Um ponteiro para um objeto ICorDebugThread que representa o thread em que a exceção foi lançada.</span><span class="sxs-lookup"><span data-stu-id="f1c63-107">[in] A pointer to an ICorDebugThread object that represents the thread on which the exception was thrown.</span></span>  
  
 `dwEventType`  
 <span data-ttu-id="f1c63-108">[in] Um valor da enumeração CorDebugExceptionUnwindCallbackType que especifica o evento que está sendo sinalizado pelo retorno de chamada durante a fase de desenrolamento.</span><span class="sxs-lookup"><span data-stu-id="f1c63-108">[in] A value of the CorDebugExceptionUnwindCallbackType enumeration that specifies the event that is being signaled by the callback during the unwind phase.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="f1c63-109">[in] Um valor de [CorDebugExceptionFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md) enumeração que especifica informações adicionais sobre a exceção.</span><span class="sxs-lookup"><span data-stu-id="f1c63-109">[in] A value of the [CorDebugExceptionFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md) enumeration that specifies additional information about the exception.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f1c63-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="f1c63-110">Remarks</span></span>  
 <span data-ttu-id="f1c63-111">`ExceptionUnwind`é chamado em vários pontos durante a fase de liberação do processo de tratamento de exceção.</span><span class="sxs-lookup"><span data-stu-id="f1c63-111">`ExceptionUnwind` is called at various points during the unwind phase of the exception-handling process.</span></span> <span data-ttu-id="f1c63-112">`ExceptionUnwind`pode ser chamado mais de uma vez durante a liberação de uma única exceção.</span><span class="sxs-lookup"><span data-stu-id="f1c63-112">`ExceptionUnwind` can be called more than once while unwinding a single exception.</span></span>  
  
 <span data-ttu-id="f1c63-113">Se `dwEventType` = DEBUG_EXCEPTION_INTERCEPTED, o ponteiro de instrução será no quadro folha do thread no ponto de sequência antes (podem ser várias instruções antes) da instrução que levou à exceção.</span><span class="sxs-lookup"><span data-stu-id="f1c63-113">If `dwEventType` = DEBUG_EXCEPTION_INTERCEPTED, the instruction pointer will be in the leaf frame of the thread, at the sequence point before (this may be several instructions before) the instruction that led to the exception.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f1c63-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f1c63-114">Requirements</span></span>  
 <span data-ttu-id="f1c63-115">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f1c63-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f1c63-116">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f1c63-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f1c63-117">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f1c63-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f1c63-118">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f1c63-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1c63-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f1c63-119">See Also</span></span>  
 [<span data-ttu-id="f1c63-120">Interface ICorDebugManagedCallback2</span><span class="sxs-lookup"><span data-stu-id="f1c63-120">ICorDebugManagedCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)  
 [<span data-ttu-id="f1c63-121">Interface ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="f1c63-121">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
