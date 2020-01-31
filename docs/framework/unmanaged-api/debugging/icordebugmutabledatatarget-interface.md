---
title: Interface ICorDebugMutableDataTarget
ms.date: 03/30/2017
ms.assetid: 14aad5b3-84ab-4bbc-94e3-1eb92e258d10
ms.openlocfilehash: e4601c24194404f943c8de8f320bf704efcc553e
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792850"
---
# <a name="icordebugmutabledatatarget-interface"></a><span data-ttu-id="a651e-102">Interface ICorDebugMutableDataTarget</span><span class="sxs-lookup"><span data-stu-id="a651e-102">ICorDebugMutableDataTarget Interface</span></span>
<span data-ttu-id="a651e-103">Estende a interface [ICorDebugDataTarget](icordebugdatatarget-interface.md) para dar suporte a destinos de dados mutáveis.</span><span class="sxs-lookup"><span data-stu-id="a651e-103">Extends the [ICorDebugDataTarget](icordebugdatatarget-interface.md) interface to support mutable data targets.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a651e-104">{1&gt;Métodos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="a651e-104">Methods</span></span>  
  
|<span data-ttu-id="a651e-105">Método</span><span class="sxs-lookup"><span data-stu-id="a651e-105">Method</span></span>|<span data-ttu-id="a651e-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="a651e-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a651e-107">Método ContinueStatusChanged</span><span class="sxs-lookup"><span data-stu-id="a651e-107">ContinueStatusChanged Method</span></span>](icordebugmutabledatatarget-continuestatuschanged-method.md)|<span data-ttu-id="a651e-108">Altera o status de continuação para o evento de depuração pendente no thread especificado.</span><span class="sxs-lookup"><span data-stu-id="a651e-108">Changes the continuation status for the outstanding debug event on the specified thread.</span></span>|  
|[<span data-ttu-id="a651e-109">Método SetThreadContext</span><span class="sxs-lookup"><span data-stu-id="a651e-109">SetThreadContext Method</span></span>](icordebugmutabledatatarget-setthreadcontext-method.md)|<span data-ttu-id="a651e-110">Define o contexto (valores de registro) para um thread.</span><span class="sxs-lookup"><span data-stu-id="a651e-110">Sets the context (register values) for a thread.</span></span>|  
|[<span data-ttu-id="a651e-111">Método WriteVirtual</span><span class="sxs-lookup"><span data-stu-id="a651e-111">WriteVirtual Method</span></span>](icordebugmutabledatatarget-writevirtual-method.md)|<span data-ttu-id="a651e-112">Grava a memória no espaço de endereço do processo de destino.</span><span class="sxs-lookup"><span data-stu-id="a651e-112">Writes memory into the target process address space.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a651e-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="a651e-113">Remarks</span></span>  
 <span data-ttu-id="a651e-114">Essa extensão para a interface [ICorDebugDataTarget](icordebugdatatarget-interface.md) pode ser implementada por ferramentas de depuração que desejam modificar o processo de destino (por exemplo, para executar a depuração de invasor ao vivo).</span><span class="sxs-lookup"><span data-stu-id="a651e-114">This extension to the [ICorDebugDataTarget](icordebugdatatarget-interface.md) interface can be implemented by debugging tools that wish to modify the target process (for example, to perform live invasive debugging).</span></span>  
  
 <span data-ttu-id="a651e-115">Todos esses métodos são opcionais no sentido de que nenhuma funcionalidade de depuração baseada em inspeção principal é perdida não implementando essa interface ou pela falha de chamadas para esses métodos.</span><span class="sxs-lookup"><span data-stu-id="a651e-115">All of these methods are optional in the sense that no core inspection-based debugging functionality is lost by not implementing this interface or by the failure of calls to these methods.</span></span>  <span data-ttu-id="a651e-116">Qualquer falha `HRESULT` desses métodos será propagada como o `HRESULT` da chamada do método ICorDebug.</span><span class="sxs-lookup"><span data-stu-id="a651e-116">Any failure `HRESULT` from these methods will propagate out as the `HRESULT` from the ICorDebug method call.</span></span>  
  
 <span data-ttu-id="a651e-117">Observe que uma única chamada de método ICorDebug pode resultar em várias mutações e que não há nenhum mecanismo para garantir que as mutações relacionadas sejam aplicadas transacionalmente (All-ou-None).</span><span class="sxs-lookup"><span data-stu-id="a651e-117">Note that a single ICorDebug method call may result in multiple mutations, and that there is no mechanism for ensuring related mutations are applied transactionally (all-or-none).</span></span>  <span data-ttu-id="a651e-118">Isso significa que, se uma mutação falhar depois que outras (para a mesma chamada ICorDebug) tiverem sido bem-sucedidas, o processo de destino poderá ser deixado em um estado inconsistente e a depuração poderá se tornar não confiável.</span><span class="sxs-lookup"><span data-stu-id="a651e-118">This means that if a mutation fails after others (for the same ICorDebug call) have succeeded, the target process may be left in an inconsistent state and debugging may become unreliable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a651e-119">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="a651e-119">Requirements</span></span>  
 <span data-ttu-id="a651e-120">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a651e-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a651e-121">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a651e-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a651e-122">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a651e-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a651e-123">**Versões do .NET Framework:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a651e-123">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a651e-124">Veja também</span><span class="sxs-lookup"><span data-stu-id="a651e-124">See also</span></span>

- [<span data-ttu-id="a651e-125">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="a651e-125">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="a651e-126">Depuração</span><span class="sxs-lookup"><span data-stu-id="a651e-126">Debugging</span></span>](index.md)
