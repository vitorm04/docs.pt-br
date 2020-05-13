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
ms.openlocfilehash: 0e9ed8054711297173e880c9eecb12c3f5bd0a68
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83207131"
---
# <a name="icordebugmanagedcallbackcreateprocess-method"></a><span data-ttu-id="e78d7-102">Método ICorDebugManagedCallback::CreateProcess</span><span class="sxs-lookup"><span data-stu-id="e78d7-102">ICorDebugManagedCallback::CreateProcess Method</span></span>
<span data-ttu-id="e78d7-103">Notifica o depurador quando um processo foi anexado ou iniciado pela primeira vez.</span><span class="sxs-lookup"><span data-stu-id="e78d7-103">Notifies the debugger when a process has been attached or started for the first time.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e78d7-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e78d7-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateProcess (  
    [in] ICorDebugProcess *pProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e78d7-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e78d7-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="e78d7-106">no Um ponteiro para um objeto ICorDebugProcess que representa o processo que foi anexado ou iniciado.</span><span class="sxs-lookup"><span data-stu-id="e78d7-106">[in] A pointer to an ICorDebugProcess object that represents the process that has been attached or started.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e78d7-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="e78d7-107">Remarks</span></span>  
 <span data-ttu-id="e78d7-108">Esse método não é chamado até que o Common Language Runtime seja inicializado.</span><span class="sxs-lookup"><span data-stu-id="e78d7-108">This method is not called until the common language runtime is initialized.</span></span> <span data-ttu-id="e78d7-109">A maioria dos métodos [ICorDebug](icordebug-interface.md) retornará CORDBG_E_NOTREADY antes do `CreateProcess` retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="e78d7-109">Most of the [ICorDebug](icordebug-interface.md) methods will return CORDBG_E_NOTREADY before the `CreateProcess` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e78d7-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e78d7-110">Requirements</span></span>  
 <span data-ttu-id="e78d7-111">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e78d7-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e78d7-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e78d7-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e78d7-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e78d7-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e78d7-114">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e78d7-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e78d7-115">Confira também</span><span class="sxs-lookup"><span data-stu-id="e78d7-115">See also</span></span>

- [<span data-ttu-id="e78d7-116">Interface ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="e78d7-116">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
