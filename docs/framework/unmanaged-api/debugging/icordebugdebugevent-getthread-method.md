---
title: Método ICorDebugDebugEvent::GetThread
ms.date: 03/30/2017
ms.assetid: 4f2e9a2c-8369-4a07-a881-ad5422626353
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 51d674159b33cad1a77a82e39b9f11a38c98cbd3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54687395"
---
# <a name="icordebugdebugeventgetthread-method"></a><span data-ttu-id="21605-102">Método ICorDebugDebugEvent::GetThread</span><span class="sxs-lookup"><span data-stu-id="21605-102">ICorDebugDebugEvent::GetThread Method</span></span>
<span data-ttu-id="21605-103">Obtém o thread no qual o evento ocorreu.</span><span class="sxs-lookup"><span data-stu-id="21605-103">Gets the thread on which the event occurred.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21605-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="21605-104">Syntax</span></span>  
  
```  
HRESULT GetThread(  
        [out]ICorDebugThread **ppThread  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="21605-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="21605-105">Parameters</span></span>  
 <span data-ttu-id="21605-106">ppThread</span><span class="sxs-lookup"><span data-stu-id="21605-106">ppThread</span></span>  
 <span data-ttu-id="21605-107">[out] Um ponteiro para o endereço de um objeto de ICorDebugThread que representa o thread no qual o evento ocorreu.</span><span class="sxs-lookup"><span data-stu-id="21605-107">[out] A pointer to the address of an ICorDebugThread object that represents the thread on which the event occurred.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="21605-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="21605-108">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="21605-109">Esse método só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="21605-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="21605-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="21605-110">Requirements</span></span>  
 <span data-ttu-id="21605-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="21605-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="21605-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="21605-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="21605-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="21605-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="21605-114">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="21605-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21605-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="21605-115">See also</span></span>
- [<span data-ttu-id="21605-116">Interface ICorDebugDebugEvent</span><span class="sxs-lookup"><span data-stu-id="21605-116">ICorDebugDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md)
- [<span data-ttu-id="21605-117">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="21605-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
