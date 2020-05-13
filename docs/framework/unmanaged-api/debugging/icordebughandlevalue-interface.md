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
ms.openlocfilehash: c901e21521e941c51939958175a5316808890e9f
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83208610"
---
# <a name="icordebughandlevalue-interface"></a><span data-ttu-id="d43a6-102">Interface ICorDebugHandleValue</span><span class="sxs-lookup"><span data-stu-id="d43a6-102">ICorDebugHandleValue Interface</span></span>

<span data-ttu-id="d43a6-103">Uma subclasse de ICorDebugReferenceValue que representa um valor de referência para o qual o depurador criou um identificador para a coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="d43a6-103">A subclass of ICorDebugReferenceValue that represents a reference value to which the debugger has created a handle for garbage collection.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d43a6-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="d43a6-104">Methods</span></span>  
  
|<span data-ttu-id="d43a6-105">Método</span><span class="sxs-lookup"><span data-stu-id="d43a6-105">Method</span></span>|<span data-ttu-id="d43a6-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="d43a6-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d43a6-107">Método Dispose</span><span class="sxs-lookup"><span data-stu-id="d43a6-107">Dispose Method</span></span>](icordebughandlevalue-dispose-method.md)|<span data-ttu-id="d43a6-108">Libera o identificador referenciado por este `ICorDebugHandleValue` objeto sem liberar explicitamente o ponteiro de interface.</span><span class="sxs-lookup"><span data-stu-id="d43a6-108">Releases the handle referenced by this `ICorDebugHandleValue` object without explicitly releasing the interface pointer.</span></span>|  
|[<span data-ttu-id="d43a6-109">Método GetHandleType</span><span class="sxs-lookup"><span data-stu-id="d43a6-109">GetHandleType Method</span></span>](icordebughandlevalue-gethandletype-method.md)|<span data-ttu-id="d43a6-110">Obtém um valor CorDebugHandleType que descreve o tipo de identificador referenciado por isso `ICorDebugHandleValue` .</span><span class="sxs-lookup"><span data-stu-id="d43a6-110">Gets a CorDebugHandleType value that describes the kind of handle referenced by this `ICorDebugHandleValue`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d43a6-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="d43a6-111">Remarks</span></span>  
 <span data-ttu-id="d43a6-112">Um `ICorDebugReferenceValue` objeto é invalidado por uma interrupção na execução de código depurado.</span><span class="sxs-lookup"><span data-stu-id="d43a6-112">An `ICorDebugReferenceValue` object is invalidated by a break in the execution of debugged code.</span></span> <span data-ttu-id="d43a6-113">Um `ICorDebugHandleValue` mantém sua referência por meio de interrupções e continuações até que seja liberado explicitamente.</span><span class="sxs-lookup"><span data-stu-id="d43a6-113">An `ICorDebugHandleValue` maintains its reference through breaks and continuations, until it is explicitly released.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d43a6-114">Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.</span><span class="sxs-lookup"><span data-stu-id="d43a6-114">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d43a6-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d43a6-115">Requirements</span></span>  
 <span data-ttu-id="d43a6-116">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d43a6-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d43a6-117">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d43a6-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d43a6-118">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d43a6-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d43a6-119">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d43a6-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d43a6-120">Confira também</span><span class="sxs-lookup"><span data-stu-id="d43a6-120">See also</span></span>

- [<span data-ttu-id="d43a6-121">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="d43a6-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
