---
title: Interface ICorDebugHandleValue
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9a9eb63e681b47f058901b0ff002015baffe6048
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61775655"
---
# <a name="icordebughandlevalue-interface"></a><span data-ttu-id="56381-102">Interface ICorDebugHandleValue</span><span class="sxs-lookup"><span data-stu-id="56381-102">ICorDebugHandleValue Interface</span></span>

<span data-ttu-id="56381-103">Uma subclasse de ICorDebugReferenceValue que representa um valor de referência para o qual o depurador criou um identificador para coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="56381-103">A subclass of ICorDebugReferenceValue that represents a reference value to which the debugger has created a handle for garbage collection.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="56381-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="56381-104">Methods</span></span>  
  
|<span data-ttu-id="56381-105">Método</span><span class="sxs-lookup"><span data-stu-id="56381-105">Method</span></span>|<span data-ttu-id="56381-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="56381-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="56381-107">Método Dispose</span><span class="sxs-lookup"><span data-stu-id="56381-107">Dispose Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebughandlevalue-dispose-method.md)|<span data-ttu-id="56381-108">Libera o identificador referenciado por este `ICorDebugHandleValue` objeto sem liberar explicitamente o ponteiro de interface.</span><span class="sxs-lookup"><span data-stu-id="56381-108">Releases the handle referenced by this `ICorDebugHandleValue` object without explicitly releasing the interface pointer.</span></span>|  
|[<span data-ttu-id="56381-109">Método GetHandleType</span><span class="sxs-lookup"><span data-stu-id="56381-109">GetHandleType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebughandlevalue-gethandletype-method.md)|<span data-ttu-id="56381-110">Obtém um valor de CorDebugHandleType que descreve o tipo de identificador referenciada por este `ICorDebugHandleValue`.</span><span class="sxs-lookup"><span data-stu-id="56381-110">Gets a CorDebugHandleType value that describes the kind of handle referenced by this `ICorDebugHandleValue`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="56381-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="56381-111">Remarks</span></span>  
 <span data-ttu-id="56381-112">Um `ICorDebugReferenceValue` objeto é invalidado por uma interrupção na execução do código depurado.</span><span class="sxs-lookup"><span data-stu-id="56381-112">An `ICorDebugReferenceValue` object is invalidated by a break in the execution of debugged code.</span></span> <span data-ttu-id="56381-113">Um `ICorDebugHandleValue` mantém sua referência por meio de quebras e continuações, até que ele é liberado explicitamente.</span><span class="sxs-lookup"><span data-stu-id="56381-113">An `ICorDebugHandleValue` maintains its reference through breaks and continuations, until it is explicitly released.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="56381-114">Essa interface não dá suporte a ser chamada remotamente, entre computadores ou entre processos.</span><span class="sxs-lookup"><span data-stu-id="56381-114">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="56381-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="56381-115">Requirements</span></span>  
 <span data-ttu-id="56381-116">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="56381-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="56381-117">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="56381-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="56381-118">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="56381-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="56381-119">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="56381-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56381-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="56381-120">See also</span></span>

- [<span data-ttu-id="56381-121">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="56381-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
