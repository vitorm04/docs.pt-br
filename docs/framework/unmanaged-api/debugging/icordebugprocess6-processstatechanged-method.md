---
title: Método ICorDebugProcess6::ProcessStateChanged
ms.date: 03/30/2017
ms.assetid: fb6d30d9-54f3-462b-8ebf-ce0440791ad5
ms.openlocfilehash: b6665df550a2d07a3fa84c3f2b6bf07f459cd713
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792212"
---
# <a name="icordebugprocess6processstatechanged-method"></a><span data-ttu-id="fadfe-102">Método ICorDebugProcess6::ProcessStateChanged</span><span class="sxs-lookup"><span data-stu-id="fadfe-102">ICorDebugProcess6::ProcessStateChanged Method</span></span>
<span data-ttu-id="fadfe-103">Notifica o [ICorDebug](icordebug-interface.md) de que o processo está em execução.</span><span class="sxs-lookup"><span data-stu-id="fadfe-103">Notifies [ICorDebug](icordebug-interface.md) that the process is running.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fadfe-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fadfe-104">Syntax</span></span>  
  
```cpp  
HRESULT ProcessStateChanged(   [in] CorDebugStateChange change);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fadfe-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="fadfe-105">Parameters</span></span>  
 `change`  
 <span data-ttu-id="fadfe-106">no Um membro da enumeração [ProcessStateChanged](icordebugprocess6-processstatechanged-method.md)</span><span class="sxs-lookup"><span data-stu-id="fadfe-106">[in] A member of the [ProcessStateChanged](icordebugprocess6-processstatechanged-method.md) enumeration</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fadfe-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="fadfe-107">Remarks</span></span>  
 <span data-ttu-id="fadfe-108">O depurador chama esse método para notificar [ICorDebug](icordebug-interface.md) que o processo está em execução.</span><span class="sxs-lookup"><span data-stu-id="fadfe-108">The debugger calls this method to notify [ICorDebug](icordebug-interface.md) that the process is running.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fadfe-109">Esse método está disponível somente com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="fadfe-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fadfe-110">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="fadfe-110">Requirements</span></span>  
 <span data-ttu-id="fadfe-111">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fadfe-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fadfe-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fadfe-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fadfe-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fadfe-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fadfe-114">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fadfe-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fadfe-115">Veja também</span><span class="sxs-lookup"><span data-stu-id="fadfe-115">See also</span></span>

- [<span data-ttu-id="fadfe-116">Interface ICorDebugProcess6</span><span class="sxs-lookup"><span data-stu-id="fadfe-116">ICorDebugProcess6 Interface</span></span>](icordebugprocess6-interface.md)
- [<span data-ttu-id="fadfe-117">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="fadfe-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
