---
title: Método ICorDebugManagedCallback::LoadClass
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 39ce3e8329c4ff32b55341127f68a800246677df
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61995209"
---
# <a name="icordebugmanagedcallbackloadclass-method"></a><span data-ttu-id="db737-102">Método ICorDebugManagedCallback::LoadClass</span><span class="sxs-lookup"><span data-stu-id="db737-102">ICorDebugManagedCallback::LoadClass Method</span></span>
<span data-ttu-id="db737-103">Notifica o depurador que uma classe foi carregada.</span><span class="sxs-lookup"><span data-stu-id="db737-103">Notifies the debugger that a class has been loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db737-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="db737-104">Syntax</span></span>  
  
```  
HRESULT LoadClass (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugClass     *c  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="db737-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="db737-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="db737-106">[in] Um ponteiro para um objeto ICorDebugAppDomain que representa o domínio de aplicativo no qual a classe foi carregada.</span><span class="sxs-lookup"><span data-stu-id="db737-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain into which the class has been loaded.</span></span>  
  
 `c`  
 <span data-ttu-id="db737-107">[in] Um ponteiro para um objeto ICorDebugClass que representa a classe.</span><span class="sxs-lookup"><span data-stu-id="db737-107">[in] A pointer to an ICorDebugClass object that represents the class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="db737-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="db737-108">Remarks</span></span>  
 <span data-ttu-id="db737-109">Esse retorno de chamada ocorre apenas se o carregamento de classe tiver sido habilitado para o módulo que contém a classe.</span><span class="sxs-lookup"><span data-stu-id="db737-109">This callback occurs only if class loading has been enabled for the module that contains the class.</span></span> <span data-ttu-id="db737-110">Carregamento de classe está sempre habilitado para módulos dinâmicos.</span><span class="sxs-lookup"><span data-stu-id="db737-110">Class loading is always enabled for dynamic modules.</span></span>  
  
 <span data-ttu-id="db737-111">O `LoadClass` retorno de chamada fornece um tempo apropriado para associar os pontos de interrupção para classes geradas recentemente em módulos dinâmicos.</span><span class="sxs-lookup"><span data-stu-id="db737-111">The `LoadClass` callback provides an appropriate time to bind breakpoints to newly generated classes in dynamic modules.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="db737-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="db737-112">Requirements</span></span>  
 <span data-ttu-id="db737-113">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="db737-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="db737-114">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="db737-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="db737-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="db737-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="db737-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="db737-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db737-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="db737-117">See also</span></span>

- [<span data-ttu-id="db737-118">Método UnloadClass</span><span class="sxs-lookup"><span data-stu-id="db737-118">UnloadClass Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md)
- [<span data-ttu-id="db737-119">Interface ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="db737-119">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
