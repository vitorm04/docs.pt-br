---
title: Método ICorDebugManagedCallback::CreateThread
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.CreateThread
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::CreateThread method
helpviewer_keywords:
- ICorDebugManagedCallback::CreateThread method [.NET Framework debugging]
- CreateThread method [.NET Framework debugging]
ms.assetid: 6b961728-21c4-4e8d-ae81-197458be62f4
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dd48fae74665f079100b128990656f3a6d002d43
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54586521"
---
# <a name="icordebugmanagedcallbackcreatethread-method"></a><span data-ttu-id="36dc4-102">Método ICorDebugManagedCallback::CreateThread</span><span class="sxs-lookup"><span data-stu-id="36dc4-102">ICorDebugManagedCallback::CreateThread Method</span></span>
<span data-ttu-id="36dc4-103">Notifica o depurador que um thread foi iniciado executando código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="36dc4-103">Notifies the debugger that a thread has started executing managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="36dc4-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="36dc4-104">Syntax</span></span>  
  
```  
HRESULT CreateThread (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *thread  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="36dc4-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="36dc4-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="36dc4-106">[in] Um ponteiro para um objeto ICorDebugAppDomain que representa o domínio de aplicativo que contém o segmento.</span><span class="sxs-lookup"><span data-stu-id="36dc4-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that contains the thread.</span></span>  
  
 `thread`  
 <span data-ttu-id="36dc4-107">[in] Um ponteiro para um objeto de ICorDebugThread que representa o thread.</span><span class="sxs-lookup"><span data-stu-id="36dc4-107">[in] A pointer to an ICorDebugThread object that represents the thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="36dc4-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="36dc4-108">Remarks</span></span>  
 <span data-ttu-id="36dc4-109">O thread será posicionado na primeira instrução de código gerenciado a ser executado.</span><span class="sxs-lookup"><span data-stu-id="36dc4-109">The thread will be positioned at the first managed code instruction to be executed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="36dc4-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="36dc4-110">Requirements</span></span>  
 <span data-ttu-id="36dc4-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="36dc4-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="36dc4-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="36dc4-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="36dc4-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="36dc4-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="36dc4-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="36dc4-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36dc4-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="36dc4-115">See also</span></span>
- [<span data-ttu-id="36dc4-116">Interface ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="36dc4-116">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
