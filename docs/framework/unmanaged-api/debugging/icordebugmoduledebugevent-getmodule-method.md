---
title: Método ICorDebugModuleDebugEvent::GetModule
ms.date: 03/30/2017
ms.assetid: b1141c35-4253-4e34-b3e4-ed406a9dea4f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e99477bd8750f79ae711d47f295b6b39b90c92c3
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57492121"
---
# <a name="icordebugmoduledebugeventgetmodule-method"></a><span data-ttu-id="29ceb-102">Método ICorDebugModuleDebugEvent::GetModule</span><span class="sxs-lookup"><span data-stu-id="29ceb-102">ICorDebugModuleDebugEvent::GetModule Method</span></span>
<span data-ttu-id="29ceb-103">Obtém o módulo mesclado que era apenas carregado ou descarregado.</span><span class="sxs-lookup"><span data-stu-id="29ceb-103">Gets the merged module that was just loaded or unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29ceb-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="29ceb-104">Syntax</span></span>  
  
```  
HRESULT GetModule(  
   [out]ICorDebugModule **ppModule  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="29ceb-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="29ceb-105">Parameters</span></span>  
 `ppModule`  
 <span data-ttu-id="29ceb-106">[out] Um ponteiro para o endereço de um objeto ICorDebugModule que representa o módulo mesclado que apenas foi carregado ou descarregado.</span><span class="sxs-lookup"><span data-stu-id="29ceb-106">[out] A pointer to the address of an ICorDebugModule object that represents the merged module that was just loaded or unloaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="29ceb-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="29ceb-107">Remarks</span></span>  
 <span data-ttu-id="29ceb-108">Você pode chamar o [GetEventKind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) método para determinar se o módulo foi carregado ou descarregado.</span><span class="sxs-lookup"><span data-stu-id="29ceb-108">You can call the [GetEventKind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) method to determine whether the module was loaded or unloaded.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="29ceb-109">Esse método só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="29ceb-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="29ceb-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="29ceb-110">Requirements</span></span>  
 <span data-ttu-id="29ceb-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="29ceb-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="29ceb-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="29ceb-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="29ceb-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="29ceb-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="29ceb-114">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="29ceb-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29ceb-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="29ceb-115">See also</span></span>
- [<span data-ttu-id="29ceb-116">Interface ICorDebugModuleDebugEvent</span><span class="sxs-lookup"><span data-stu-id="29ceb-116">ICorDebugModuleDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduledebugevent-interface.md)
- [<span data-ttu-id="29ceb-117">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="29ceb-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
