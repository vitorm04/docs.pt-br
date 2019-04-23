---
title: Método ICorDebugManagedCallback2::ExceptionUnwind
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2.ExceptionUnwind
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2::ExceptionUnwind
helpviewer_keywords:
- ICorDebugManagedCallback2::ExceptionUnwind method [.NET Framework debugging]
- ExceptionUnwind method [.NET Framework debugging]
ms.assetid: aaf5938d-179c-4eaa-8d35-8523a4fadded
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: faba9631e85ac84ff1517b64e9a3f5567ee7c9dc
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59214787"
---
# <a name="icordebugmanagedcallback2exceptionunwind-method"></a><span data-ttu-id="5a976-102">Método ICorDebugManagedCallback2::ExceptionUnwind</span><span class="sxs-lookup"><span data-stu-id="5a976-102">ICorDebugManagedCallback2::ExceptionUnwind Method</span></span>
<span data-ttu-id="5a976-103">Fornece uma notificação de status durante o processo de desenrolamento de exceção.</span><span class="sxs-lookup"><span data-stu-id="5a976-103">Provides a status notification during the exception unwinding process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a976-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5a976-104">Syntax</span></span>  
  
```  
HRESULT ExceptionUnwind (  
    [in] ICorDebugAppDomain                  *pAppDomain,  
    [in] ICorDebugThread                     *pThread,  
    [in] CorDebugExceptionUnwindCallbackType  dwEventType,  
    [in] DWORD                                dwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5a976-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5a976-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="5a976-106">[in] Um ponteiro para um objeto ICorDebugAppDomain que representa o domínio de aplicativo que contém o segmento em que a exceção foi lançada.</span><span class="sxs-lookup"><span data-stu-id="5a976-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the thread on which the exception was thrown.</span></span>  
  
 `pThread`  
 <span data-ttu-id="5a976-107">[in] Um ponteiro para um objeto de ICorDebugThread que representa o thread no qual a exceção foi lançada.</span><span class="sxs-lookup"><span data-stu-id="5a976-107">[in] A pointer to an ICorDebugThread object that represents the thread on which the exception was thrown.</span></span>  
  
 `dwEventType`  
 <span data-ttu-id="5a976-108">[in] Um valor de enumeração CorDebugExceptionUnwindCallbackType que especifica o evento que está sendo sinalizado pelo retorno de chamada durante a fase de desenrolamento.</span><span class="sxs-lookup"><span data-stu-id="5a976-108">[in] A value of the CorDebugExceptionUnwindCallbackType enumeration that specifies the event that is being signaled by the callback during the unwind phase.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="5a976-109">[in] Um valor igual a [CorDebugExceptionFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md) enumeração que especifica informações adicionais sobre a exceção.</span><span class="sxs-lookup"><span data-stu-id="5a976-109">[in] A value of the [CorDebugExceptionFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md) enumeration that specifies additional information about the exception.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5a976-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="5a976-110">Remarks</span></span>  
 <span data-ttu-id="5a976-111">`ExceptionUnwind` é chamado em vários pontos durante a fase de desenrolamento do processo de manipulação de exceção.</span><span class="sxs-lookup"><span data-stu-id="5a976-111">`ExceptionUnwind` is called at various points during the unwind phase of the exception-handling process.</span></span> <span data-ttu-id="5a976-112">`ExceptionUnwind` pode ser chamado mais de uma vez durante o desenrolamento de uma única exceção.</span><span class="sxs-lookup"><span data-stu-id="5a976-112">`ExceptionUnwind` can be called more than once while unwinding a single exception.</span></span>  
  
 <span data-ttu-id="5a976-113">Se `dwEventType` = DEBUG_EXCEPTION_INTERCEPTED, o ponteiro de instrução será no quadro de thread, no ponto de sequência antes de folha (Isso pode ser várias instruções de antes) da instrução que conduziram à exceção.</span><span class="sxs-lookup"><span data-stu-id="5a976-113">If `dwEventType` = DEBUG_EXCEPTION_INTERCEPTED, the instruction pointer will be in the leaf frame of the thread, at the sequence point before (this may be several instructions before) the instruction that led to the exception.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5a976-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5a976-114">Requirements</span></span>  
 <span data-ttu-id="5a976-115">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5a976-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5a976-116">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5a976-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5a976-117">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5a976-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5a976-118">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5a976-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a976-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5a976-119">See also</span></span>

- [<span data-ttu-id="5a976-120">Interface ICorDebugManagedCallback2</span><span class="sxs-lookup"><span data-stu-id="5a976-120">ICorDebugManagedCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="5a976-121">Interface ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="5a976-121">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
