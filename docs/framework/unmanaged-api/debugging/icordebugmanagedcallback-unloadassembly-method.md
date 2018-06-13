---
title: Método ICorDebugManagedCallback::UnloadAssembly
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a892012e872dcf44512adbe0d6890812d84ed899
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33412588"
---
# <a name="icordebugmanagedcallbackunloadassembly-method"></a><span data-ttu-id="9d4ad-102">Método ICorDebugManagedCallback::UnloadAssembly</span><span class="sxs-lookup"><span data-stu-id="9d4ad-102">ICorDebugManagedCallback::UnloadAssembly Method</span></span>
<span data-ttu-id="9d4ad-103">Notifica o depurador que um assembly do common language runtime foi descarregado.</span><span class="sxs-lookup"><span data-stu-id="9d4ad-103">Notifies the debugger that a common language runtime assembly has been unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d4ad-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9d4ad-104">Syntax</span></span>  
  
```  
HRESULT UnloadAssembly (  
    [in] IcorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugAssembly   *pAssembly  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9d4ad-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="9d4ad-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="9d4ad-106">[in] Um ponteiro para um objeto ICorDebugAppDomain que representa o domínio de aplicativo que continha o assembly.</span><span class="sxs-lookup"><span data-stu-id="9d4ad-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that contained the assembly.</span></span>  
  
 `pAssembly`  
 <span data-ttu-id="9d4ad-107">[in] Um ponteiro para um objeto ICorDebugAssembly que representa o assembly.</span><span class="sxs-lookup"><span data-stu-id="9d4ad-107">[in] A pointer to an ICorDebugAssembly object that represents the assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9d4ad-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="9d4ad-108">Remarks</span></span>  
 <span data-ttu-id="9d4ad-109">O assembly não deve ser usado após esse retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="9d4ad-109">The assembly should not be used after this callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9d4ad-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9d4ad-110">Requirements</span></span>  
 <span data-ttu-id="9d4ad-111">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9d4ad-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9d4ad-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9d4ad-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9d4ad-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9d4ad-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9d4ad-114">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9d4ad-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d4ad-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9d4ad-115">See Also</span></span>  
 [<span data-ttu-id="9d4ad-116">Método LoadAssembly</span><span class="sxs-lookup"><span data-stu-id="9d4ad-116">LoadAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadassembly-method.md)  
 [<span data-ttu-id="9d4ad-117">Interface ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="9d4ad-117">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
