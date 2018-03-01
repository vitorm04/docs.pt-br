---
title: "Método ICorDebugManagedCallback2::FunctionRemapComplete"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 52c7ead9091754d4355880befe6a8a11b3cc5eaf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmanagedcallback2functionremapcomplete-method"></a><span data-ttu-id="a6b31-102">Método ICorDebugManagedCallback2::FunctionRemapComplete</span><span class="sxs-lookup"><span data-stu-id="a6b31-102">ICorDebugManagedCallback2::FunctionRemapComplete Method</span></span>
<span data-ttu-id="a6b31-103">Notifica o depurador que a execução de código alternou para uma nova versão de uma função editada.</span><span class="sxs-lookup"><span data-stu-id="a6b31-103">Notifies the debugger that code execution has switched to a new version of an edited function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6b31-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a6b31-104">Syntax</span></span>  
  
```  
HRESULT FunctionRemapComplete (  
    [in] ICorDebugAppDomain   *pAppDomain,  
    [in] ICorDebugThread      *pThread,  
    [in] ICorDebugFunction    *pFunction  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a6b31-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a6b31-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="a6b31-106">[in] Um ponteiro para um objeto ICorDebugAppDomain que representa o domínio de aplicativo que contém a função editada.</span><span class="sxs-lookup"><span data-stu-id="a6b31-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the edited function.</span></span>  
  
 `pThread`  
 <span data-ttu-id="a6b31-107">[in] Um ponteiro para um objeto ICorDebugThread que representa o thread em que o ponto de interrupção remapear foi encontrado.</span><span class="sxs-lookup"><span data-stu-id="a6b31-107">[in] A pointer to an ICorDebugThread object that represents the thread on which the remap breakpoint was encountered.</span></span>  
  
 `pFunction`  
 <span data-ttu-id="a6b31-108">[in] Um ponteiro para um objeto ICorDebugFunction que representa a versão da função atualmente em execução no thread.</span><span class="sxs-lookup"><span data-stu-id="a6b31-108">[in] A pointer to an ICorDebugFunction object that represents the version of the function currently running on the thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a6b31-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="a6b31-109">Remarks</span></span>  
 <span data-ttu-id="a6b31-110">Esse retorno de chamada de depurador uma oportunidade para recriar a qualquer steppers que existia anteriormente.</span><span class="sxs-lookup"><span data-stu-id="a6b31-110">This callback gives the debugger an opportunity to recreate any steppers that previously existed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a6b31-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a6b31-111">Requirements</span></span>  
 <span data-ttu-id="a6b31-112">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a6b31-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a6b31-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a6b31-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a6b31-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a6b31-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a6b31-115">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a6b31-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6b31-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a6b31-116">See Also</span></span>  
 [<span data-ttu-id="a6b31-117">Interface ICorDebugManagedCallback2</span><span class="sxs-lookup"><span data-stu-id="a6b31-117">ICorDebugManagedCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)  
 [<span data-ttu-id="a6b31-118">Interface ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="a6b31-118">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
