---
title: Interface ICorDebugMutableDataTarget
ms.date: 03/30/2017
ms.assetid: 14aad5b3-84ab-4bbc-94e3-1eb92e258d10
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 677db647320ff4014b791502b7ac1b261378c8dd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33419524"
---
# <a name="icordebugmutabledatatarget-interface"></a><span data-ttu-id="e48cc-102">Interface ICorDebugMutableDataTarget</span><span class="sxs-lookup"><span data-stu-id="e48cc-102">ICorDebugMutableDataTarget Interface</span></span>
<span data-ttu-id="e48cc-103">Estende o [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interface para oferecer suporte a destinos de dados mutável.</span><span class="sxs-lookup"><span data-stu-id="e48cc-103">Extends the [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interface to support mutable data targets.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e48cc-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="e48cc-104">Methods</span></span>  
  
|<span data-ttu-id="e48cc-105">Método</span><span class="sxs-lookup"><span data-stu-id="e48cc-105">Method</span></span>|<span data-ttu-id="e48cc-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="e48cc-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e48cc-107">Método ContinueStatusChanged</span><span class="sxs-lookup"><span data-stu-id="e48cc-107">ContinueStatusChanged Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-continuestatuschanged-method.md)|<span data-ttu-id="e48cc-108">Altera o status de continuação para o evento de depuração pendentes no thread especificado.</span><span class="sxs-lookup"><span data-stu-id="e48cc-108">Changes the continuation status for the outstanding debug event on the specified thread.</span></span>|  
|[<span data-ttu-id="e48cc-109">Método SetThreadContext</span><span class="sxs-lookup"><span data-stu-id="e48cc-109">SetThreadContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-setthreadcontext-method.md)|<span data-ttu-id="e48cc-110">Define o contexto (valores do registro) de um thread.</span><span class="sxs-lookup"><span data-stu-id="e48cc-110">Sets the context (register values) for a thread.</span></span>|  
|[<span data-ttu-id="e48cc-111">Método WriteVirtual</span><span class="sxs-lookup"><span data-stu-id="e48cc-111">WriteVirtual Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-writevirtual-method.md)|<span data-ttu-id="e48cc-112">Grava a memória no espaço de endereço de processo de destino.</span><span class="sxs-lookup"><span data-stu-id="e48cc-112">Writes memory into the target process address space.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e48cc-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="e48cc-113">Remarks</span></span>  
 <span data-ttu-id="e48cc-114">Essa extensão para o [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interface pode ser implementada pelas ferramentas de depuração que deseja modificar o processo de destino (por exemplo, para realizar a depuração invasivo ao vivo).</span><span class="sxs-lookup"><span data-stu-id="e48cc-114">This extension to the [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interface can be implemented by debugging tools that wish to modify the target process (for example, to perform live invasive debugging).</span></span>  
  
 <span data-ttu-id="e48cc-115">Todos esses métodos são opcionais no sentido de que nenhuma funcionalidade de depuração com base em inspeção principal é perdida por não implementa esta interface ou a falha de chamadas para esses métodos.</span><span class="sxs-lookup"><span data-stu-id="e48cc-115">All of these methods are optional in the sense that no core inspection-based debugging functionality is lost by not implementing this interface or by the failure of calls to these methods.</span></span>  <span data-ttu-id="e48cc-116">Qualquer falha `HRESULT` entre esses métodos serão propagadas como o `HRESULT` na chamada de método ICorDebug.</span><span class="sxs-lookup"><span data-stu-id="e48cc-116">Any failure `HRESULT` from these methods will propagate out as the `HRESULT` from the ICorDebug method call.</span></span>  
  
 <span data-ttu-id="e48cc-117">Observe que uma única chamada de método ICorDebug pode resultar em várias mutações e que não há nenhum mecanismo para garantir relacionados mutações são aplicadas de forma transacional (AON).</span><span class="sxs-lookup"><span data-stu-id="e48cc-117">Note that a single ICorDebug method call may result in multiple mutations, and that there is no mechanism for ensuring related mutations are applied transactionally (all-or-none).</span></span>  <span data-ttu-id="e48cc-118">Isso significa que, se uma mutação falhar depois que outras pessoas (para a mesma chamada ICorDebug) tiveram êxito, o processo de destino poderão ser deixado em um estado inconsistente e depuração pode se tornar não confiável.</span><span class="sxs-lookup"><span data-stu-id="e48cc-118">This means that if a mutation fails after others (for the same ICorDebug call) have succeeded, the target process may be left in an inconsistent state and debugging may become unreliable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e48cc-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e48cc-119">Requirements</span></span>  
 <span data-ttu-id="e48cc-120">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e48cc-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e48cc-121">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e48cc-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e48cc-122">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e48cc-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e48cc-123">**Versões do .NET framework:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e48cc-123">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e48cc-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e48cc-124">See Also</span></span>  
 [<span data-ttu-id="e48cc-125">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="e48cc-125">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="e48cc-126">Depuração</span><span class="sxs-lookup"><span data-stu-id="e48cc-126">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
