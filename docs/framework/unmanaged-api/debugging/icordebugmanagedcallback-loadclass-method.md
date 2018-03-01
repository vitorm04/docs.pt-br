---
title: "Método ICorDebugManagedCallback::LoadClass"
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
- ICorDebugManagedCallback.LoadClass
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::LoadClass
helpviewer_keywords:
- ICorDebugManagedCallback::LoadClass method [.NET Framework debugging]
- LoadClass method [.NET Framework debugging]
ms.assetid: e58dac7b-85c3-41ca-b9aa-3a7fc9ae6680
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f3e732b418398e9c917085d22507c9304981b06a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmanagedcallbackloadclass-method"></a><span data-ttu-id="d793e-102">Método ICorDebugManagedCallback::LoadClass</span><span class="sxs-lookup"><span data-stu-id="d793e-102">ICorDebugManagedCallback::LoadClass Method</span></span>
<span data-ttu-id="d793e-103">Notifica o depurador que uma classe foi carregada.</span><span class="sxs-lookup"><span data-stu-id="d793e-103">Notifies the debugger that a class has been loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d793e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d793e-104">Syntax</span></span>  
  
```  
HRESULT LoadClass (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugClass     *c  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d793e-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d793e-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="d793e-106">[in] Um ponteiro para um objeto ICorDebugAppDomain que representa o domínio de aplicativo no qual a classe foi carregada.</span><span class="sxs-lookup"><span data-stu-id="d793e-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain into which the class has been loaded.</span></span>  
  
 `c`  
 <span data-ttu-id="d793e-107">[in] Um ponteiro para um objeto ICorDebugClass que representa a classe.</span><span class="sxs-lookup"><span data-stu-id="d793e-107">[in] A pointer to an ICorDebugClass object that represents the class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d793e-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="d793e-108">Remarks</span></span>  
 <span data-ttu-id="d793e-109">Esse retorno de chamada ocorre apenas se o carregamento de classe tiver sido habilitado para o módulo que contém a classe.</span><span class="sxs-lookup"><span data-stu-id="d793e-109">This callback occurs only if class loading has been enabled for the module that contains the class.</span></span> <span data-ttu-id="d793e-110">Carregamento de classe está sempre habilitado para módulos dinâmicos.</span><span class="sxs-lookup"><span data-stu-id="d793e-110">Class loading is always enabled for dynamic modules.</span></span>  
  
 <span data-ttu-id="d793e-111">O `LoadClass` retorno de chamada oferece um momento apropriado para associar os pontos de interrupção para as classes recém-gerado em módulos dinâmicos.</span><span class="sxs-lookup"><span data-stu-id="d793e-111">The `LoadClass` callback provides an appropriate time to bind breakpoints to newly generated classes in dynamic modules.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d793e-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d793e-112">Requirements</span></span>  
 <span data-ttu-id="d793e-113">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d793e-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d793e-114">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d793e-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d793e-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d793e-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d793e-116">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d793e-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d793e-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d793e-117">See Also</span></span>  
 [<span data-ttu-id="d793e-118">Método UnloadClass</span><span class="sxs-lookup"><span data-stu-id="d793e-118">UnloadClass Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md)  
 [<span data-ttu-id="d793e-119">Interface ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="d793e-119">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
