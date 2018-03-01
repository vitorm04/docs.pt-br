---
title: "Método ICorDebugManagedCallback::UnloadAssembly"
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
- ICorDebugManagedCallback.UnloadAssembly
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::UnloadAssembly
helpviewer_keywords:
- ICorDebugManagedCallback::UnloadAssembly method [.NET Framework debugging]
- UnloadAssembly method [.NET Framework debugging]
ms.assetid: 6734321c-c8a9-401f-a558-cad715ec4a77
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 731615729f680bae4c4b8517de4a3e522d4acae2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmanagedcallbackunloadassembly-method"></a><span data-ttu-id="86a3b-102">Método ICorDebugManagedCallback::UnloadAssembly</span><span class="sxs-lookup"><span data-stu-id="86a3b-102">ICorDebugManagedCallback::UnloadAssembly Method</span></span>
<span data-ttu-id="86a3b-103">Notifica o depurador que um assembly do common language runtime foi descarregado.</span><span class="sxs-lookup"><span data-stu-id="86a3b-103">Notifies the debugger that a common language runtime assembly has been unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86a3b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="86a3b-104">Syntax</span></span>  
  
```  
HRESULT UnloadAssembly (  
    [in] IcorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugAssembly   *pAssembly  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="86a3b-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="86a3b-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="86a3b-106">[in] Um ponteiro para um objeto ICorDebugAppDomain que representa o domínio de aplicativo que continha o assembly.</span><span class="sxs-lookup"><span data-stu-id="86a3b-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that contained the assembly.</span></span>  
  
 `pAssembly`  
 <span data-ttu-id="86a3b-107">[in] Um ponteiro para um objeto ICorDebugAssembly que representa o assembly.</span><span class="sxs-lookup"><span data-stu-id="86a3b-107">[in] A pointer to an ICorDebugAssembly object that represents the assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="86a3b-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="86a3b-108">Remarks</span></span>  
 <span data-ttu-id="86a3b-109">O assembly não deve ser usado após esse retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="86a3b-109">The assembly should not be used after this callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="86a3b-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="86a3b-110">Requirements</span></span>  
 <span data-ttu-id="86a3b-111">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="86a3b-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="86a3b-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="86a3b-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="86a3b-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="86a3b-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="86a3b-114">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="86a3b-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86a3b-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="86a3b-115">See Also</span></span>  
 [<span data-ttu-id="86a3b-116">Método LoadAssembly</span><span class="sxs-lookup"><span data-stu-id="86a3b-116">LoadAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadassembly-method.md)  
 [<span data-ttu-id="86a3b-117">Interface ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="86a3b-117">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
