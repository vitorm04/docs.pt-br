---
title: Método ICorDebugManagedCallback::CreateProcess
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.CreateProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::CreateProcess
helpviewer_keywords:
- ICorDebugManagedCallback::CreateProcess method [.NET Framework debugging]
- CreateProcess method, ICorDebugManagedCallback interface [.NET Framework debugging]
ms.assetid: 8e89d5ee-e4e3-4738-8302-0b7d1cf4846e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 24efa08e9c4b2e242af95112b7f055e9173aaa7c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugmanagedcallbackcreateprocess-method"></a><span data-ttu-id="98e29-102">Método ICorDebugManagedCallback::CreateProcess</span><span class="sxs-lookup"><span data-stu-id="98e29-102">ICorDebugManagedCallback::CreateProcess Method</span></span>
<span data-ttu-id="98e29-103">Notifica o depurador quando um processo for anexado ou iniciado pela primeira vez.</span><span class="sxs-lookup"><span data-stu-id="98e29-103">Notifies the debugger when a process has been attached or started for the first time.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="98e29-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="98e29-104">Syntax</span></span>  
  
```  
HRESULT CreateProcess (  
    [in] ICorDebugProcess *pProcess  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="98e29-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="98e29-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="98e29-106">[in] Um ponteiro para um objeto ICorDebugProcess que representa o processo que foi anexado ou iniciado.</span><span class="sxs-lookup"><span data-stu-id="98e29-106">[in] A pointer to an ICorDebugProcess object that represents the process that has been attached or started.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="98e29-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="98e29-107">Remarks</span></span>  
 <span data-ttu-id="98e29-108">Este método não é chamado depois que o common language runtime for inicializado.</span><span class="sxs-lookup"><span data-stu-id="98e29-108">This method is not called until the common language runtime is initialized.</span></span> <span data-ttu-id="98e29-109">A maioria do [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) métodos retornarão CORDBG_E_NOTREADY antes do `CreateProcess` retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="98e29-109">Most of the [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) methods will return CORDBG_E_NOTREADY before the `CreateProcess` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="98e29-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="98e29-110">Requirements</span></span>  
 <span data-ttu-id="98e29-111">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="98e29-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="98e29-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="98e29-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="98e29-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="98e29-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="98e29-114">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="98e29-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98e29-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="98e29-115">See Also</span></span>  
 [<span data-ttu-id="98e29-116">Interface ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="98e29-116">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
