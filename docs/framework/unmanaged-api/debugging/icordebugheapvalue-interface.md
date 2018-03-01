---
title: ICorDebugHeapValue Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugHeapValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapValue
helpviewer_keywords:
- ICorDebugHeapValue interface [.NET Framework debugging]
ms.assetid: 1bca66db-0359-4ae8-846e-e35f7e547e8b
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: d2ab132b73369526204f8fd811e1567b07b4a9b0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugheapvalue-interface1"></a><span data-ttu-id="4a14f-102">ICorDebugHeapValue Interface1</span><span class="sxs-lookup"><span data-stu-id="4a14f-102">ICorDebugHeapValue Interface1</span></span>
<span data-ttu-id="4a14f-103">Uma subclasse de "ICorDebugValue" que representa um objeto que foi coletado pelo coletor de lixo common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="4a14f-103">A subclass of "ICorDebugValue" that represents an object that has been collected by the common language runtime (CLR) garbage collector.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4a14f-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="4a14f-104">Methods</span></span>  
  
|<span data-ttu-id="4a14f-105">Método</span><span class="sxs-lookup"><span data-stu-id="4a14f-105">Method</span></span>|<span data-ttu-id="4a14f-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="4a14f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4a14f-107">Método CreateRelocBreakpoint</span><span class="sxs-lookup"><span data-stu-id="4a14f-107">CreateRelocBreakpoint Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue-createrelocbreakpoint-method.md)|<span data-ttu-id="4a14f-108">Não implementado.</span><span class="sxs-lookup"><span data-stu-id="4a14f-108">Not implemented.</span></span>|  
|[<span data-ttu-id="4a14f-109">Método IsValid</span><span class="sxs-lookup"><span data-stu-id="4a14f-109">IsValid Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue-isvalid-method.md)|<span data-ttu-id="4a14f-110">Obtém um valor que indica se o objeto representado por este `ICorDebugHeapValue` é válido ou tiver sido recuperada pelo coletor de lixo.</span><span class="sxs-lookup"><span data-stu-id="4a14f-110">Gets a value that indicates whether the object represented by this `ICorDebugHeapValue` is valid, or has been reclaimed by the garbage collector.</span></span> <span data-ttu-id="4a14f-111">Esse método foi preterido no .NET Framework versão 2.0.</span><span class="sxs-lookup"><span data-stu-id="4a14f-111">This method has been deprecated in the .NET Framework version 2.0.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4a14f-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="4a14f-112">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4a14f-113">Esta interface não dá suporte a que está sendo chamado remotamente, entre computadores ou entre processos.</span><span class="sxs-lookup"><span data-stu-id="4a14f-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4a14f-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4a14f-114">Requirements</span></span>  
 <span data-ttu-id="4a14f-115">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4a14f-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4a14f-116">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4a14f-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4a14f-117">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4a14f-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4a14f-118">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4a14f-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a14f-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4a14f-119">See Also</span></span>  
    
    
    
 [<span data-ttu-id="4a14f-120">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="4a14f-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
