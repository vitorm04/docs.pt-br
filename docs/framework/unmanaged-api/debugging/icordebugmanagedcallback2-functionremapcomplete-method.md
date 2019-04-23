---
title: Método ICorDebugManagedCallback2::FunctionRemapComplete
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2.FunctionRemapComplete
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2::FunctionRemapComplete
helpviewer_keywords:
- FunctionRemapComplete method [.NET Framework debugging]
- ICorDebugManagedCallback2::FunctionRemapComplete method [.NET Framework debugging]
ms.assetid: 5396c4c3-4ec3-4e3a-a38d-d65b21f0a2fc
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 515d434e8d8f1c99cf5052ef9a2f1e098f6021b2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59140550"
---
# <a name="icordebugmanagedcallback2functionremapcomplete-method"></a><span data-ttu-id="2198a-102">Método ICorDebugManagedCallback2::FunctionRemapComplete</span><span class="sxs-lookup"><span data-stu-id="2198a-102">ICorDebugManagedCallback2::FunctionRemapComplete Method</span></span>
<span data-ttu-id="2198a-103">Notifica o depurador para que a execução de código mudou para uma nova versão de uma função editada.</span><span class="sxs-lookup"><span data-stu-id="2198a-103">Notifies the debugger that code execution has switched to a new version of an edited function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2198a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2198a-104">Syntax</span></span>  
  
```  
HRESULT FunctionRemapComplete (  
    [in] ICorDebugAppDomain   *pAppDomain,  
    [in] ICorDebugThread      *pThread,  
    [in] ICorDebugFunction    *pFunction  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2198a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2198a-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="2198a-106">[in] Um ponteiro para um objeto ICorDebugAppDomain que representa o domínio de aplicativo que contém a função editada.</span><span class="sxs-lookup"><span data-stu-id="2198a-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the edited function.</span></span>  
  
 `pThread`  
 <span data-ttu-id="2198a-107">[in] Um ponteiro para um objeto de ICorDebugThread que representa o thread no qual o remapeamento de ponto de interrupção foi encontrado.</span><span class="sxs-lookup"><span data-stu-id="2198a-107">[in] A pointer to an ICorDebugThread object that represents the thread on which the remap breakpoint was encountered.</span></span>  
  
 `pFunction`  
 <span data-ttu-id="2198a-108">[in] Um ponteiro para um objeto ICorDebugFunction que representa a versão da função atualmente em execução no thread.</span><span class="sxs-lookup"><span data-stu-id="2198a-108">[in] A pointer to an ICorDebugFunction object that represents the version of the function currently running on the thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2198a-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="2198a-109">Remarks</span></span>  
 <span data-ttu-id="2198a-110">Esse retorno de chamada o depurador uma oportunidade para recriar qualquer steppers que existia anteriormente.</span><span class="sxs-lookup"><span data-stu-id="2198a-110">This callback gives the debugger an opportunity to recreate any steppers that previously existed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2198a-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2198a-111">Requirements</span></span>  
 <span data-ttu-id="2198a-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2198a-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2198a-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2198a-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2198a-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2198a-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2198a-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2198a-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2198a-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2198a-116">See also</span></span>

- [<span data-ttu-id="2198a-117">Interface ICorDebugManagedCallback2</span><span class="sxs-lookup"><span data-stu-id="2198a-117">ICorDebugManagedCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="2198a-118">Interface ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="2198a-118">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
