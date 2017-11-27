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
ms.openlocfilehash: 13b950545c2c8c8b54d24b932351d80280e1dac0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugdebugeventgetthread-method"></a><span data-ttu-id="0b620-102">Método ICorDebugDebugEvent::GetThread</span><span class="sxs-lookup"><span data-stu-id="0b620-102">ICorDebugDebugEvent::GetThread Method</span></span>
<span data-ttu-id="0b620-103">Obtém o thread no qual o evento ocorreu.</span><span class="sxs-lookup"><span data-stu-id="0b620-103">Gets the thread on which the event occurred.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b620-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0b620-104">Syntax</span></span>  
  
```  
HRESULT GetThread(  
        [out]ICorDebugThread **ppThread  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0b620-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0b620-105">Parameters</span></span>  
 <span data-ttu-id="0b620-106">ppThread</span><span class="sxs-lookup"><span data-stu-id="0b620-106">ppThread</span></span>  
 <span data-ttu-id="0b620-107">[out] Um ponteiro para o endereço de um objeto ICorDebugThread que representa o thread no qual o evento ocorreu.</span><span class="sxs-lookup"><span data-stu-id="0b620-107">[out] A pointer to the address of an ICorDebugThread object that represents the thread on which the event occurred.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0b620-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="0b620-108">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0b620-109">Esse método só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="0b620-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0b620-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0b620-110">Requirements</span></span>  
 <span data-ttu-id="0b620-111">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0b620-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0b620-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0b620-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0b620-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0b620-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0b620-114">**Versões do .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0b620-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b620-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0b620-115">See Also</span></span>  
 [<span data-ttu-id="0b620-116">Interface ICorDebugDebugEvent</span><span class="sxs-lookup"><span data-stu-id="0b620-116">ICorDebugDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md)  
 [<span data-ttu-id="0b620-117">Interfaces de depuração</span><span class="sxs-lookup"><span data-stu-id="0b620-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
