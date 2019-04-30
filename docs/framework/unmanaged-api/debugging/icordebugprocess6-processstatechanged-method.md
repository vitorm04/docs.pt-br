---
title: Método ICorDebugProcess6::ProcessStateChanged
ms.date: 03/30/2017
ms.assetid: fb6d30d9-54f3-462b-8ebf-ce0440791ad5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a4dcee3b396d9533f3169db1ea54a6cdc6086c8c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61948584"
---
# <a name="icordebugprocess6processstatechanged-method"></a><span data-ttu-id="cb72d-102">Método ICorDebugProcess6::ProcessStateChanged</span><span class="sxs-lookup"><span data-stu-id="cb72d-102">ICorDebugProcess6::ProcessStateChanged Method</span></span>
<span data-ttu-id="cb72d-103">Notifica [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) que o processo está em execução.</span><span class="sxs-lookup"><span data-stu-id="cb72d-103">Notifies [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) that the process is running.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb72d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cb72d-104">Syntax</span></span>  
  
```  
HRESULT ProcessStateChanged(   [in] CorDebugStateChange change);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cb72d-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="cb72d-105">Parameters</span></span>  
 `change`  
 <span data-ttu-id="cb72d-106">[in] Um membro do [ProcessStateChanged](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-processstatechanged-method.md) enumeração</span><span class="sxs-lookup"><span data-stu-id="cb72d-106">[in] A member of the [ProcessStateChanged](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-processstatechanged-method.md) enumeration</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cb72d-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="cb72d-107">Remarks</span></span>  
 <span data-ttu-id="cb72d-108">O depurador chama esse método para notificar [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) que o processo está em execução.</span><span class="sxs-lookup"><span data-stu-id="cb72d-108">The debugger calls this method to notify [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) that the process is running.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cb72d-109">Esse método só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="cb72d-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cb72d-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="cb72d-110">Requirements</span></span>  
 <span data-ttu-id="cb72d-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cb72d-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cb72d-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cb72d-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cb72d-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cb72d-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cb72d-114">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cb72d-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb72d-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cb72d-115">See also</span></span>

- [<span data-ttu-id="cb72d-116">Interface ICorDebugProcess6</span><span class="sxs-lookup"><span data-stu-id="cb72d-116">ICorDebugProcess6 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)
- [<span data-ttu-id="cb72d-117">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="cb72d-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
