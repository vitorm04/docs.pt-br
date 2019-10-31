---
title: Método ICorDebugProcess6::ProcessStateChanged
ms.date: 03/30/2017
ms.assetid: fb6d30d9-54f3-462b-8ebf-ce0440791ad5
ms.openlocfilehash: 3927e57883ebe282b262cb03ececc3b2cd96fd46
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123424"
---
# <a name="icordebugprocess6processstatechanged-method"></a><span data-ttu-id="514c9-102">Método ICorDebugProcess6::ProcessStateChanged</span><span class="sxs-lookup"><span data-stu-id="514c9-102">ICorDebugProcess6::ProcessStateChanged Method</span></span>
<span data-ttu-id="514c9-103">Notifica o [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) de que o processo está em execução.</span><span class="sxs-lookup"><span data-stu-id="514c9-103">Notifies [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) that the process is running.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="514c9-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="514c9-104">Syntax</span></span>  
  
```cpp  
HRESULT ProcessStateChanged(   [in] CorDebugStateChange change);  
```  
  
## <a name="parameters"></a><span data-ttu-id="514c9-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="514c9-105">Parameters</span></span>  
 `change`  
 <span data-ttu-id="514c9-106">no Um membro da enumeração [ProcessStateChanged](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-processstatechanged-method.md)</span><span class="sxs-lookup"><span data-stu-id="514c9-106">[in] A member of the [ProcessStateChanged](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-processstatechanged-method.md) enumeration</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="514c9-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="514c9-107">Remarks</span></span>  
 <span data-ttu-id="514c9-108">O depurador chama esse método para notificar [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) que o processo está em execução.</span><span class="sxs-lookup"><span data-stu-id="514c9-108">The debugger calls this method to notify [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) that the process is running.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="514c9-109">Esse método está disponível somente com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="514c9-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="514c9-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="514c9-110">Requirements</span></span>  
 <span data-ttu-id="514c9-111">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="514c9-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="514c9-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="514c9-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="514c9-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="514c9-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="514c9-114">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="514c9-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="514c9-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="514c9-115">See also</span></span>

- [<span data-ttu-id="514c9-116">Interface ICorDebugProcess6</span><span class="sxs-lookup"><span data-stu-id="514c9-116">ICorDebugProcess6 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)
- [<span data-ttu-id="514c9-117">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="514c9-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
