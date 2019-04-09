---
title: Método ICorDebugManagedCallback::UnloadClass
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.UnloadClass
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::UnloadClass
helpviewer_keywords:
- ICorDebugManagedCallback::UnloadClass method [.NET Framework debugging]
- UnloadClass method [.NET Framework debugging]
ms.assetid: 66a59b18-ce9a-41f4-b23b-4dd6753d6d36
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b3eb8bf59ee2a91c62a6ff74b1903d92607a9ffe
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59197849"
---
# <a name="icordebugmanagedcallbackunloadclass-method"></a><span data-ttu-id="3751c-102">Método ICorDebugManagedCallback::UnloadClass</span><span class="sxs-lookup"><span data-stu-id="3751c-102">ICorDebugManagedCallback::UnloadClass Method</span></span>
<span data-ttu-id="3751c-103">Notifica o depurador que uma classe está sendo descarregada.</span><span class="sxs-lookup"><span data-stu-id="3751c-103">Notifies the debugger that a class is being unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3751c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3751c-104">Syntax</span></span>  
  
```  
HRESULT UnloadClass (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugClass      *c  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3751c-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="3751c-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="3751c-106">[in] Um ponteiro para um objeto ICorDebugAppDomain que representa o domínio de aplicativo que contém a classe.</span><span class="sxs-lookup"><span data-stu-id="3751c-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the class.</span></span>  
  
 `c`  
 <span data-ttu-id="3751c-107">[in] Um ponteiro para um objeto ICorDebugClass que representa a classe.</span><span class="sxs-lookup"><span data-stu-id="3751c-107">[in] A pointer to an ICorDebugClass object that represents the class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3751c-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="3751c-108">Remarks</span></span>  
 <span data-ttu-id="3751c-109">A classe não deve ser referenciada após esta chamada.</span><span class="sxs-lookup"><span data-stu-id="3751c-109">The class should not be referenced after this call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3751c-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3751c-110">Requirements</span></span>  
 <span data-ttu-id="3751c-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3751c-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3751c-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3751c-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3751c-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3751c-113">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="3751c-114">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="3751c-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="3751c-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3751c-115">See also</span></span>

- [<span data-ttu-id="3751c-116">Método LoadClass</span><span class="sxs-lookup"><span data-stu-id="3751c-116">LoadClass Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md)
- [<span data-ttu-id="3751c-117">Interface ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="3751c-117">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
