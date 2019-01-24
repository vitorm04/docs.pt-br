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
ms.openlocfilehash: 7693111427f3181adcd2127ad5ecb2a317e30921
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54515609"
---
# <a name="icordebugmanagedcallbackcreateprocess-method"></a><span data-ttu-id="ffca4-102">Método ICorDebugManagedCallback::CreateProcess</span><span class="sxs-lookup"><span data-stu-id="ffca4-102">ICorDebugManagedCallback::CreateProcess Method</span></span>
<span data-ttu-id="ffca4-103">Notifica o depurador quando um processo foi anexado ou iniciado pela primeira vez.</span><span class="sxs-lookup"><span data-stu-id="ffca4-103">Notifies the debugger when a process has been attached or started for the first time.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ffca4-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ffca4-104">Syntax</span></span>  
  
```  
HRESULT CreateProcess (  
    [in] ICorDebugProcess *pProcess  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ffca4-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ffca4-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="ffca4-106">[in] Um ponteiro para um objeto ICorDebugProcess que representa o processo que foi anexado ou iniciado.</span><span class="sxs-lookup"><span data-stu-id="ffca4-106">[in] A pointer to an ICorDebugProcess object that represents the process that has been attached or started.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ffca4-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="ffca4-107">Remarks</span></span>  
 <span data-ttu-id="ffca4-108">Esse método não é chamado até que o common language runtime é inicializado.</span><span class="sxs-lookup"><span data-stu-id="ffca4-108">This method is not called until the common language runtime is initialized.</span></span> <span data-ttu-id="ffca4-109">A maioria dos [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) métodos retornarão CORDBG_E_NOTREADY antes do `CreateProcess` retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="ffca4-109">Most of the [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) methods will return CORDBG_E_NOTREADY before the `CreateProcess` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ffca4-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ffca4-110">Requirements</span></span>  
 <span data-ttu-id="ffca4-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ffca4-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ffca4-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ffca4-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ffca4-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ffca4-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ffca4-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ffca4-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ffca4-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ffca4-115">See also</span></span>
- [<span data-ttu-id="ffca4-116">Interface ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="ffca4-116">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
