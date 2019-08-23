---
title: Método ICorDebugDebugEvent::GetThread
ms.date: 03/30/2017
ms.assetid: 4f2e9a2c-8369-4a07-a881-ad5422626353
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4f85dccd5b59610c52adcf685828984c9344fd49
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69911279"
---
# <a name="icordebugdebugeventgetthread-method"></a><span data-ttu-id="6e30e-102">Método ICorDebugDebugEvent::GetThread</span><span class="sxs-lookup"><span data-stu-id="6e30e-102">ICorDebugDebugEvent::GetThread Method</span></span>
<span data-ttu-id="6e30e-103">Obtém o thread no qual o evento ocorreu.</span><span class="sxs-lookup"><span data-stu-id="6e30e-103">Gets the thread on which the event occurred.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6e30e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6e30e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThread(  
        [out]ICorDebugThread **ppThread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6e30e-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6e30e-105">Parameters</span></span>  
 <span data-ttu-id="6e30e-106">ppThread</span><span class="sxs-lookup"><span data-stu-id="6e30e-106">ppThread</span></span>  
 <span data-ttu-id="6e30e-107">fora Um ponteiro para o endereço de um objeto ICorDebugThread que representa o thread no qual o evento ocorreu.</span><span class="sxs-lookup"><span data-stu-id="6e30e-107">[out] A pointer to the address of an ICorDebugThread object that represents the thread on which the event occurred.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6e30e-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="6e30e-108">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6e30e-109">Esse método está disponível somente com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="6e30e-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6e30e-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6e30e-110">Requirements</span></span>  
 <span data-ttu-id="6e30e-111">**Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6e30e-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6e30e-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6e30e-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6e30e-113">**Biblioteca** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6e30e-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6e30e-114">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6e30e-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e30e-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6e30e-115">See also</span></span>

- [<span data-ttu-id="6e30e-116">Interface ICorDebugDebugEvent</span><span class="sxs-lookup"><span data-stu-id="6e30e-116">ICorDebugDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md)
- [<span data-ttu-id="6e30e-117">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="6e30e-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
