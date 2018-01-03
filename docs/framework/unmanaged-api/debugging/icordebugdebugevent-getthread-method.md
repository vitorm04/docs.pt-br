---
title: "Método ICorDebugDebugEvent::GetThread"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 4f2e9a2c-8369-4a07-a881-ad5422626353
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: faf1ace6c65f38e9a1d5b958b633c95dbcd3dcf8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugdebugeventgetthread-method"></a><span data-ttu-id="1da1d-102">Método ICorDebugDebugEvent::GetThread</span><span class="sxs-lookup"><span data-stu-id="1da1d-102">ICorDebugDebugEvent::GetThread Method</span></span>
<span data-ttu-id="1da1d-103">Obtém o thread no qual o evento ocorreu.</span><span class="sxs-lookup"><span data-stu-id="1da1d-103">Gets the thread on which the event occurred.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1da1d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1da1d-104">Syntax</span></span>  
  
```  
HRESULT GetThread(  
        [out]ICorDebugThread **ppThread  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1da1d-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="1da1d-105">Parameters</span></span>  
 <span data-ttu-id="1da1d-106">ppThread</span><span class="sxs-lookup"><span data-stu-id="1da1d-106">ppThread</span></span>  
 <span data-ttu-id="1da1d-107">[out] Um ponteiro para o endereço de um objeto ICorDebugThread que representa o thread no qual o evento ocorreu.</span><span class="sxs-lookup"><span data-stu-id="1da1d-107">[out] A pointer to the address of an ICorDebugThread object that represents the thread on which the event occurred.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1da1d-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="1da1d-108">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1da1d-109">Esse método só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="1da1d-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1da1d-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1da1d-110">Requirements</span></span>  
 <span data-ttu-id="1da1d-111">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1da1d-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1da1d-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1da1d-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1da1d-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1da1d-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1da1d-114">**Versões do .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1da1d-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1da1d-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1da1d-115">See Also</span></span>  
 [<span data-ttu-id="1da1d-116">Interface ICorDebugDebugEvent</span><span class="sxs-lookup"><span data-stu-id="1da1d-116">ICorDebugDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md)  
 [<span data-ttu-id="1da1d-117">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="1da1d-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
