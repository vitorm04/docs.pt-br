---
title: Interface ICorDebugMutableDataTarget
ms.date: 03/30/2017
ms.assetid: 14aad5b3-84ab-4bbc-94e3-1eb92e258d10
ms.openlocfilehash: 682e927388d3392d970338314f97d46c9e57e760
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139330"
---
# <a name="icordebugmutabledatatarget-interface"></a><span data-ttu-id="1ef76-102">Interface ICorDebugMutableDataTarget</span><span class="sxs-lookup"><span data-stu-id="1ef76-102">ICorDebugMutableDataTarget Interface</span></span>
<span data-ttu-id="1ef76-103">Estende a interface [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) para dar suporte a destinos de dados mutáveis.</span><span class="sxs-lookup"><span data-stu-id="1ef76-103">Extends the [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interface to support mutable data targets.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1ef76-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="1ef76-104">Methods</span></span>  
  
|<span data-ttu-id="1ef76-105">Método</span><span class="sxs-lookup"><span data-stu-id="1ef76-105">Method</span></span>|<span data-ttu-id="1ef76-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="1ef76-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1ef76-107">Método ContinueStatusChanged</span><span class="sxs-lookup"><span data-stu-id="1ef76-107">ContinueStatusChanged Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-continuestatuschanged-method.md)|<span data-ttu-id="1ef76-108">Altera o status de continuação para o evento de depuração pendente no thread especificado.</span><span class="sxs-lookup"><span data-stu-id="1ef76-108">Changes the continuation status for the outstanding debug event on the specified thread.</span></span>|  
|[<span data-ttu-id="1ef76-109">Método SetThreadContext</span><span class="sxs-lookup"><span data-stu-id="1ef76-109">SetThreadContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-setthreadcontext-method.md)|<span data-ttu-id="1ef76-110">Define o contexto (valores de registro) para um thread.</span><span class="sxs-lookup"><span data-stu-id="1ef76-110">Sets the context (register values) for a thread.</span></span>|  
|[<span data-ttu-id="1ef76-111">Método WriteVirtual</span><span class="sxs-lookup"><span data-stu-id="1ef76-111">WriteVirtual Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-writevirtual-method.md)|<span data-ttu-id="1ef76-112">Grava a memória no espaço de endereço do processo de destino.</span><span class="sxs-lookup"><span data-stu-id="1ef76-112">Writes memory into the target process address space.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1ef76-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="1ef76-113">Remarks</span></span>  
 <span data-ttu-id="1ef76-114">Essa extensão para a interface [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) pode ser implementada por ferramentas de depuração que desejam modificar o processo de destino (por exemplo, para executar a depuração de invasor ao vivo).</span><span class="sxs-lookup"><span data-stu-id="1ef76-114">This extension to the [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interface can be implemented by debugging tools that wish to modify the target process (for example, to perform live invasive debugging).</span></span>  
  
 <span data-ttu-id="1ef76-115">Todos esses métodos são opcionais no sentido de que nenhuma funcionalidade de depuração baseada em inspeção principal é perdida não implementando essa interface ou pela falha de chamadas para esses métodos.</span><span class="sxs-lookup"><span data-stu-id="1ef76-115">All of these methods are optional in the sense that no core inspection-based debugging functionality is lost by not implementing this interface or by the failure of calls to these methods.</span></span>  <span data-ttu-id="1ef76-116">Qualquer falha `HRESULT` desses métodos será propagada como o `HRESULT` da chamada do método ICorDebug.</span><span class="sxs-lookup"><span data-stu-id="1ef76-116">Any failure `HRESULT` from these methods will propagate out as the `HRESULT` from the ICorDebug method call.</span></span>  
  
 <span data-ttu-id="1ef76-117">Observe que uma única chamada de método ICorDebug pode resultar em várias mutações e que não há nenhum mecanismo para garantir que as mutações relacionadas sejam aplicadas transacionalmente (All-ou-None).</span><span class="sxs-lookup"><span data-stu-id="1ef76-117">Note that a single ICorDebug method call may result in multiple mutations, and that there is no mechanism for ensuring related mutations are applied transactionally (all-or-none).</span></span>  <span data-ttu-id="1ef76-118">Isso significa que, se uma mutação falhar depois que outras (para a mesma chamada ICorDebug) tiverem sido bem-sucedidas, o processo de destino poderá ser deixado em um estado inconsistente e a depuração poderá se tornar não confiável.</span><span class="sxs-lookup"><span data-stu-id="1ef76-118">This means that if a mutation fails after others (for the same ICorDebug call) have succeeded, the target process may be left in an inconsistent state and debugging may become unreliable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1ef76-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1ef76-119">Requirements</span></span>  
 <span data-ttu-id="1ef76-120">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1ef76-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1ef76-121">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1ef76-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1ef76-122">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1ef76-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1ef76-123">**Versões do .NET Framework:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1ef76-123">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ef76-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1ef76-124">See also</span></span>

- [<span data-ttu-id="1ef76-125">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="1ef76-125">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="1ef76-126">Depuração</span><span class="sxs-lookup"><span data-stu-id="1ef76-126">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
