---
title: Método ICorDebugVirtualUnwinder::Next
ms.date: 03/30/2017
ms.assetid: 790e0426-e5cd-49fd-a792-f8c8635d72fe
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b6b6b7078db058150ec39bcf82e6984a1949e7cd
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54507129"
---
# <a name="icordebugvirtualunwindernext-method"></a><span data-ttu-id="76703-102">Método ICorDebugVirtualUnwinder::Next</span><span class="sxs-lookup"><span data-stu-id="76703-102">ICorDebugVirtualUnwinder::Next Method</span></span>
<span data-ttu-id="76703-103">Avança para o contexto do chamador.</span><span class="sxs-lookup"><span data-stu-id="76703-103">Advances to the caller's context.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="76703-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="76703-104">Syntax</span></span>  
  
```  
HRESULT Next();  
```  
  
#### <a name="parameters"></a><span data-ttu-id="76703-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="76703-105">Parameters</span></span>  
 <span data-ttu-id="76703-106">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="76703-106">None.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="76703-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="76703-107">Return Value</span></span>  
 <span data-ttu-id="76703-108">`S_OK` Se o desenrolamento ocorreu com êxito, ou `CORDBG_S_AT_END_OF_STACK` se o desenrolamento não pode ser concluído porque não há nenhum quadro mais.</span><span class="sxs-lookup"><span data-stu-id="76703-108">`S_OK` if the unwind occurred successfully, or `CORDBG_S_AT_END_OF_STACK` if the unwind cannot be completed because there are no more frames.</span></span>  
  
 <span data-ttu-id="76703-109">Se uma falha HRESULT é retornada, ICorDebug APIs retornarão `CORDBG_E_DATA_TARGET_ERROR`.</span><span class="sxs-lookup"><span data-stu-id="76703-109">If a failing HRESULT is returned, ICorDebug APIs will return `CORDBG_E_DATA_TARGET_ERROR`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="76703-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="76703-110">Remarks</span></span>  
 <span data-ttu-id="76703-111">O caminhador de pilha deve garantir que ele faz acelerar o andamento, portanto, que, eventualmente, uma chamada para `Next` retornará uma falha HRESULT ou `CORDBG_S_AT_END_OF_STACK`.</span><span class="sxs-lookup"><span data-stu-id="76703-111">The stack walker should ensure that it makes forward progress, so that eventually a call to `Next` will return a failing HRESULT or `CORDBG_S_AT_END_OF_STACK`.</span></span> <span data-ttu-id="76703-112">Retornando `S_OK` indefinidamente pode causar um loop infinito.</span><span class="sxs-lookup"><span data-stu-id="76703-112">Returning `S_OK` indefinitely may cause an infinite loop.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="76703-113">Esse método só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="76703-113">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="76703-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="76703-114">Requirements</span></span>  
 <span data-ttu-id="76703-115">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="76703-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="76703-116">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="76703-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="76703-117">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="76703-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="76703-118">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="76703-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76703-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="76703-119">See also</span></span>
- [<span data-ttu-id="76703-120">Interface ICorDebugMemoryBuffer</span><span class="sxs-lookup"><span data-stu-id="76703-120">ICorDebugMemoryBuffer Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)
- [<span data-ttu-id="76703-121">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="76703-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
