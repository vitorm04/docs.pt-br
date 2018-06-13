---
title: Método ICorDebugProcess6::ProcessStateChanged
ms.date: 03/30/2017
ms.assetid: fb6d30d9-54f3-462b-8ebf-ce0440791ad5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bc5861762242412d7ab6f0c02f2b8f5c149f9453
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33420173"
---
# <a name="icordebugprocess6processstatechanged-method"></a><span data-ttu-id="55e43-102">Método ICorDebugProcess6::ProcessStateChanged</span><span class="sxs-lookup"><span data-stu-id="55e43-102">ICorDebugProcess6::ProcessStateChanged Method</span></span>
<span data-ttu-id="55e43-103">Notifica [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) que o processo está sendo executado.</span><span class="sxs-lookup"><span data-stu-id="55e43-103">Notifies [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) that the process is running.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="55e43-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="55e43-104">Syntax</span></span>  
  
```  
HRESULT ProcessStateChanged(   [in] CorDebugStateChange change);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="55e43-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="55e43-105">Parameters</span></span>  
 `change`  
 <span data-ttu-id="55e43-106">[in] Membro de [ProcessStateChanged](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-processstatechanged-method.md) enumeração</span><span class="sxs-lookup"><span data-stu-id="55e43-106">[in] A member of the [ProcessStateChanged](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-processstatechanged-method.md) enumeration</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="55e43-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="55e43-107">Remarks</span></span>  
 <span data-ttu-id="55e43-108">O depurador chama esse método para notificar [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) que o processo está sendo executado.</span><span class="sxs-lookup"><span data-stu-id="55e43-108">The debugger calls this method to notify [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) that the process is running.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="55e43-109">Esse método só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="55e43-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="55e43-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="55e43-110">Requirements</span></span>  
 <span data-ttu-id="55e43-111">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="55e43-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="55e43-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="55e43-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="55e43-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="55e43-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="55e43-114">**Versões do .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="55e43-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55e43-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="55e43-115">See Also</span></span>  
 [<span data-ttu-id="55e43-116">Interface ICorDebugProcess6</span><span class="sxs-lookup"><span data-stu-id="55e43-116">ICorDebugProcess6 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)  
 [<span data-ttu-id="55e43-117">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="55e43-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
