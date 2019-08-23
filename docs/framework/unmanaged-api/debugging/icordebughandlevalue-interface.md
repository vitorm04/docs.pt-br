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
ms.openlocfilehash: 3219554cf953b8de31e236b2f484478172673f7b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69915000"
---
# <a name="icordebughandlevalue-interface"></a><span data-ttu-id="84a66-102">Interface ICorDebugHandleValue</span><span class="sxs-lookup"><span data-stu-id="84a66-102">ICorDebugHandleValue Interface</span></span>

<span data-ttu-id="84a66-103">Uma subclasse de ICorDebugReferenceValue que representa um valor de referência para o qual o depurador criou um identificador para a coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="84a66-103">A subclass of ICorDebugReferenceValue that represents a reference value to which the debugger has created a handle for garbage collection.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="84a66-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="84a66-104">Methods</span></span>  
  
|<span data-ttu-id="84a66-105">Método</span><span class="sxs-lookup"><span data-stu-id="84a66-105">Method</span></span>|<span data-ttu-id="84a66-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="84a66-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="84a66-107">Método Dispose</span><span class="sxs-lookup"><span data-stu-id="84a66-107">Dispose Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebughandlevalue-dispose-method.md)|<span data-ttu-id="84a66-108">Libera o identificador referenciado por `ICorDebugHandleValue` este objeto sem liberar explicitamente o ponteiro de interface.</span><span class="sxs-lookup"><span data-stu-id="84a66-108">Releases the handle referenced by this `ICorDebugHandleValue` object without explicitly releasing the interface pointer.</span></span>|  
|[<span data-ttu-id="84a66-109">Método GetHandleType</span><span class="sxs-lookup"><span data-stu-id="84a66-109">GetHandleType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebughandlevalue-gethandletype-method.md)|<span data-ttu-id="84a66-110">Obtém um valor CorDebugHandleType que descreve o tipo de identificador referenciado por `ICorDebugHandleValue`isso.</span><span class="sxs-lookup"><span data-stu-id="84a66-110">Gets a CorDebugHandleType value that describes the kind of handle referenced by this `ICorDebugHandleValue`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="84a66-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="84a66-111">Remarks</span></span>  
 <span data-ttu-id="84a66-112">Um `ICorDebugReferenceValue` objeto é invalidado por uma interrupção na execução de código depurado.</span><span class="sxs-lookup"><span data-stu-id="84a66-112">An `ICorDebugReferenceValue` object is invalidated by a break in the execution of debugged code.</span></span> <span data-ttu-id="84a66-113">Um `ICorDebugHandleValue` mantém sua referência por meio de interrupções e continuações até que seja liberado explicitamente.</span><span class="sxs-lookup"><span data-stu-id="84a66-113">An `ICorDebugHandleValue` maintains its reference through breaks and continuations, until it is explicitly released.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="84a66-114">Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.</span><span class="sxs-lookup"><span data-stu-id="84a66-114">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="84a66-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="84a66-115">Requirements</span></span>  
 <span data-ttu-id="84a66-116">**Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="84a66-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="84a66-117">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="84a66-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="84a66-118">**Biblioteca** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="84a66-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="84a66-119">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="84a66-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84a66-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="84a66-120">See also</span></span>

- [<span data-ttu-id="84a66-121">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="84a66-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
