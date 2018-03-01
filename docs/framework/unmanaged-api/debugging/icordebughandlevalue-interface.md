---
title: ICorDebugHandleValue Interface1
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
- ICorDebugHandleValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHandleValue
helpviewer_keywords:
- ICorDebugHandleValue interface [.NET Framework debugging]
ms.assetid: 66fcd2b8-ac66-414b-83a8-75a925e17772
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b8df7b46bf22fa1a3a8633cbad7ad1a6582b4860
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebughandlevalue-interface1"></a><span data-ttu-id="19518-102">ICorDebugHandleValue Interface1</span><span class="sxs-lookup"><span data-stu-id="19518-102">ICorDebugHandleValue Interface1</span></span>
<span data-ttu-id="19518-103">Uma subclasse de ICorDebugReferenceValue que representa um valor de referência para o qual o depurador criou um identificador para a coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="19518-103">A subclass of ICorDebugReferenceValue that represents a reference value to which the debugger has created a handle for garbage collection.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="19518-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="19518-104">Methods</span></span>  
  
|<span data-ttu-id="19518-105">Método</span><span class="sxs-lookup"><span data-stu-id="19518-105">Method</span></span>|<span data-ttu-id="19518-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="19518-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="19518-107">Método Dispose</span><span class="sxs-lookup"><span data-stu-id="19518-107">Dispose Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebughandlevalue-dispose-method.md)|<span data-ttu-id="19518-108">Libera o identificador referenciado por este `ICorDebugHandleValue` objeto sem liberar explicitamente o ponteiro de interface.</span><span class="sxs-lookup"><span data-stu-id="19518-108">Releases the handle referenced by this `ICorDebugHandleValue` object without explicitly releasing the interface pointer.</span></span>|  
|[<span data-ttu-id="19518-109">Método GetHandleType</span><span class="sxs-lookup"><span data-stu-id="19518-109">GetHandleType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebughandlevalue-gethandletype-method.md)|<span data-ttu-id="19518-110">Obtém um valor de CorDebugHandleType que descreve o tipo de identificador referenciada por este `ICorDebugHandleValue`.</span><span class="sxs-lookup"><span data-stu-id="19518-110">Gets a CorDebugHandleType value that describes the kind of handle referenced by this `ICorDebugHandleValue`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="19518-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="19518-111">Remarks</span></span>  
 <span data-ttu-id="19518-112">Um `ICorDebugReferenceValue` objeto é invalidado por uma quebra na execução de código depurado.</span><span class="sxs-lookup"><span data-stu-id="19518-112">An `ICorDebugReferenceValue` object is invalidated by a break in the execution of debugged code.</span></span> <span data-ttu-id="19518-113">Um `ICorDebugHandleValue` mantém sua referência por meio de quebras e continuação, até que ele seja liberado explicitamente.</span><span class="sxs-lookup"><span data-stu-id="19518-113">An `ICorDebugHandleValue` maintains its reference through breaks and continuations, until it is explicitly released.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="19518-114">Esta interface não dá suporte a que está sendo chamado remotamente, entre computadores ou entre processos.</span><span class="sxs-lookup"><span data-stu-id="19518-114">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="19518-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="19518-115">Requirements</span></span>  
 <span data-ttu-id="19518-116">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="19518-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="19518-117">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="19518-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="19518-118">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="19518-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="19518-119">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="19518-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19518-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="19518-120">See Also</span></span>  
 [<span data-ttu-id="19518-121">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="19518-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
