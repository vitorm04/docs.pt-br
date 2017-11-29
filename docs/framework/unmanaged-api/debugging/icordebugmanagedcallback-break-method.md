---
title: "Método ICorDebugManagedCallback::Break"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugManagedCallback.Break
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugManagedCallback::Break
helpviewer_keywords:
- Break method [.NET Framework debugging]
- ICorDebugManagedCallback::Break method [.NET Framework debugging]
ms.assetid: 7d78a301-82b3-43b2-9d65-3cda3285ae97
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ce51ed25ecd5570ce3c5d9acc1ec3750b289f095
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugmanagedcallbackbreak-method"></a><span data-ttu-id="583b1-102">Método ICorDebugManagedCallback::Break</span><span class="sxs-lookup"><span data-stu-id="583b1-102">ICorDebugManagedCallback::Break Method</span></span>
<span data-ttu-id="583b1-103">Notifica o depurador quando um <xref:System.Reflection.Emit.OpCodes.Break> instrução no fluxo de código é executada.</span><span class="sxs-lookup"><span data-stu-id="583b1-103">Notifies the debugger when a <xref:System.Reflection.Emit.OpCodes.Break> instruction in the code stream is executed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="583b1-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="583b1-104">Syntax</span></span>  
  
```  
HRESULT Break (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *thread  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="583b1-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="583b1-105">Parameters</span></span>  
 `pAppDOmain`  
 <span data-ttu-id="583b1-106">[in] Um ponteiro para um objeto ICorDebugAppDomain que representa o domínio de aplicativo que contém a instrução break.</span><span class="sxs-lookup"><span data-stu-id="583b1-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that contains the break instruction.</span></span>  
  
 `thread`  
 <span data-ttu-id="583b1-107">[in] Um ponteiro para um objeto ICorDebugThread que representa o segmento que contém a instrução break.</span><span class="sxs-lookup"><span data-stu-id="583b1-107">[in] A pointer to an ICorDebugThread object that represents the thread that contains the break instruction.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="583b1-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="583b1-108">Requirements</span></span>  
 <span data-ttu-id="583b1-109">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="583b1-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="583b1-110">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="583b1-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="583b1-111">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="583b1-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="583b1-112">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="583b1-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="583b1-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="583b1-113">See Also</span></span>  
 [<span data-ttu-id="583b1-114">Interface ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="583b1-114">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
