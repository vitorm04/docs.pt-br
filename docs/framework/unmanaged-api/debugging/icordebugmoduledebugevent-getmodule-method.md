---
title: Método ICorDebugModuleDebugEvent::GetModule
ms.date: 03/30/2017
ms.assetid: b1141c35-4253-4e34-b3e4-ed406a9dea4f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1ad20bdee5fee83b62d5da7f52c607835055616f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54672325"
---
# <a name="icordebugmoduledebugeventgetmodule-method"></a><span data-ttu-id="aff63-102">Método ICorDebugModuleDebugEvent::GetModule</span><span class="sxs-lookup"><span data-stu-id="aff63-102">ICorDebugModuleDebugEvent::GetModule Method</span></span>
<span data-ttu-id="aff63-103">Obtém o módulo mesclado que era apenas carregado ou descarregado.</span><span class="sxs-lookup"><span data-stu-id="aff63-103">Gets the merged module that was just loaded or unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aff63-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="aff63-104">Syntax</span></span>  
  
```  
HRESULT GetModule(  
   [out]ICorDebugModule **ppModule  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="aff63-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="aff63-105">Parameters</span></span>  
 `ppModule`  
 <span data-ttu-id="aff63-106">[out] Um ponteiro para o endereço de um objeto ICorDebugModule que representa o módulo mesclado que apenas foi carregado ou descarregado.</span><span class="sxs-lookup"><span data-stu-id="aff63-106">[out] A pointer to the address of an ICorDebugModule object that represents the merged module that was just loaded or unloaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="aff63-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="aff63-107">Remarks</span></span>  
 <span data-ttu-id="aff63-108">Você pode chamar o [GetEventKind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) método para determinar se o módulo foi carregado ou descarregado.</span><span class="sxs-lookup"><span data-stu-id="aff63-108">You can call the [GetEventKind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) method to determine whether the module was loaded or unloaded.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="aff63-109">Esse método só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="aff63-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aff63-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="aff63-110">Requirements</span></span>  
 <span data-ttu-id="aff63-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aff63-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aff63-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="aff63-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="aff63-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="aff63-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="aff63-114">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aff63-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aff63-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="aff63-115">See also</span></span>
- [<span data-ttu-id="aff63-116">Interface ICorDebugModuleDebugEvent</span><span class="sxs-lookup"><span data-stu-id="aff63-116">ICorDebugModuleDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduledebugevent-interface.md)
- [<span data-ttu-id="aff63-117">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="aff63-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
