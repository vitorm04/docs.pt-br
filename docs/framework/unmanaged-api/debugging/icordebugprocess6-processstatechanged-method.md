---
title: Método ICorDebugProcess6::ProcessStateChanged
ms.date: 03/30/2017
ms.assetid: fb6d30d9-54f3-462b-8ebf-ce0440791ad5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6f25e25f94dae1a959cbb813a44a7f4f09eaa69c
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57474586"
---
# <a name="icordebugprocess6processstatechanged-method"></a><span data-ttu-id="df1f4-102">Método ICorDebugProcess6::ProcessStateChanged</span><span class="sxs-lookup"><span data-stu-id="df1f4-102">ICorDebugProcess6::ProcessStateChanged Method</span></span>
<span data-ttu-id="df1f4-103">Notifica [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) que o processo está em execução.</span><span class="sxs-lookup"><span data-stu-id="df1f4-103">Notifies [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) that the process is running.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="df1f4-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="df1f4-104">Syntax</span></span>  
  
```  
HRESULT ProcessStateChanged(   [in] CorDebugStateChange change);  
```  
  
## <a name="parameters"></a><span data-ttu-id="df1f4-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="df1f4-105">Parameters</span></span>  
 `change`  
 <span data-ttu-id="df1f4-106">[in] Um membro do [ProcessStateChanged](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-processstatechanged-method.md) enumeração</span><span class="sxs-lookup"><span data-stu-id="df1f4-106">[in] A member of the [ProcessStateChanged](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-processstatechanged-method.md) enumeration</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="df1f4-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="df1f4-107">Remarks</span></span>  
 <span data-ttu-id="df1f4-108">O depurador chama esse método para notificar [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) que o processo está em execução.</span><span class="sxs-lookup"><span data-stu-id="df1f4-108">The debugger calls this method to notify [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) that the process is running.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="df1f4-109">Esse método só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="df1f4-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="df1f4-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="df1f4-110">Requirements</span></span>  
 <span data-ttu-id="df1f4-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="df1f4-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="df1f4-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="df1f4-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="df1f4-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="df1f4-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="df1f4-114">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="df1f4-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df1f4-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="df1f4-115">See also</span></span>
- [<span data-ttu-id="df1f4-116">Interface ICorDebugProcess6</span><span class="sxs-lookup"><span data-stu-id="df1f4-116">ICorDebugProcess6 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)
- [<span data-ttu-id="df1f4-117">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="df1f4-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
