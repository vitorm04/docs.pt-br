---
title: 'Método ICorDebugModuleDebugEvent:: GetModule'
ms.date: 03/30/2017
ms.assetid: b1141c35-4253-4e34-b3e4-ed406a9dea4f
ms.openlocfilehash: 5dc26d0367d01bc8da957c3ce648c3e529dddb08
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73096933"
---
# <a name="icordebugmoduledebugeventgetmodule-method"></a><span data-ttu-id="b5ff5-102">Método ICorDebugModuleDebugEvent:: GetModule</span><span class="sxs-lookup"><span data-stu-id="b5ff5-102">ICorDebugModuleDebugEvent::GetModule Method</span></span>
<span data-ttu-id="b5ff5-103">Obtém o módulo mesclado que acabou de ser carregado ou descarregado.</span><span class="sxs-lookup"><span data-stu-id="b5ff5-103">Gets the merged module that was just loaded or unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b5ff5-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b5ff5-104">Syntax</span></span>  
  
```cpp  
HRESULT GetModule(  
   [out]ICorDebugModule **ppModule  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b5ff5-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b5ff5-105">Parameters</span></span>  
 `ppModule`  
 <span data-ttu-id="b5ff5-106">fora Um ponteiro para o endereço de um objeto ICorDebugModule que representa o módulo mesclado que acabou de ser carregado ou descarregado.</span><span class="sxs-lookup"><span data-stu-id="b5ff5-106">[out] A pointer to the address of an ICorDebugModule object that represents the merged module that was just loaded or unloaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b5ff5-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="b5ff5-107">Remarks</span></span>  
 <span data-ttu-id="b5ff5-108">Você pode chamar o método [GetEventKind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) para determinar se o módulo foi carregado ou descarregado.</span><span class="sxs-lookup"><span data-stu-id="b5ff5-108">You can call the [GetEventKind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) method to determine whether the module was loaded or unloaded.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b5ff5-109">Esse método está disponível somente com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="b5ff5-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b5ff5-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b5ff5-110">Requirements</span></span>  
 <span data-ttu-id="b5ff5-111">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b5ff5-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b5ff5-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b5ff5-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b5ff5-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b5ff5-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b5ff5-114">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b5ff5-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5ff5-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b5ff5-115">See also</span></span>

- [<span data-ttu-id="b5ff5-116">Interface ICorDebugModuleDebugEvent</span><span class="sxs-lookup"><span data-stu-id="b5ff5-116">ICorDebugModuleDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduledebugevent-interface.md)
- [<span data-ttu-id="b5ff5-117">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="b5ff5-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
