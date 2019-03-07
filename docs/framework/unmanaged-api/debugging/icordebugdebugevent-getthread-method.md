---
title: Método ICorDebugDebugEvent::GetThread
ms.date: 03/30/2017
ms.assetid: 4f2e9a2c-8369-4a07-a881-ad5422626353
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 403caa136f85904937bd5077a618e5aed788c86a
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57472298"
---
# <a name="icordebugdebugeventgetthread-method"></a><span data-ttu-id="f06a1-102">Método ICorDebugDebugEvent::GetThread</span><span class="sxs-lookup"><span data-stu-id="f06a1-102">ICorDebugDebugEvent::GetThread Method</span></span>
<span data-ttu-id="f06a1-103">Obtém o thread no qual o evento ocorreu.</span><span class="sxs-lookup"><span data-stu-id="f06a1-103">Gets the thread on which the event occurred.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f06a1-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f06a1-104">Syntax</span></span>  
  
```  
HRESULT GetThread(  
        [out]ICorDebugThread **ppThread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f06a1-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f06a1-105">Parameters</span></span>  
 <span data-ttu-id="f06a1-106">ppThread</span><span class="sxs-lookup"><span data-stu-id="f06a1-106">ppThread</span></span>  
 <span data-ttu-id="f06a1-107">[out] Um ponteiro para o endereço de um objeto de ICorDebugThread que representa o thread no qual o evento ocorreu.</span><span class="sxs-lookup"><span data-stu-id="f06a1-107">[out] A pointer to the address of an ICorDebugThread object that represents the thread on which the event occurred.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f06a1-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="f06a1-108">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f06a1-109">Esse método só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="f06a1-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f06a1-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f06a1-110">Requirements</span></span>  
 <span data-ttu-id="f06a1-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f06a1-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f06a1-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f06a1-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f06a1-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f06a1-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f06a1-114">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f06a1-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f06a1-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f06a1-115">See also</span></span>
- [<span data-ttu-id="f06a1-116">Interface ICorDebugDebugEvent</span><span class="sxs-lookup"><span data-stu-id="f06a1-116">ICorDebugDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md)
- [<span data-ttu-id="f06a1-117">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="f06a1-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
