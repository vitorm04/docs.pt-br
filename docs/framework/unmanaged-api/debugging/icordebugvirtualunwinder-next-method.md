---
title: "Método ICorDebugVirtualUnwinder::Next"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 790e0426-e5cd-49fd-a792-f8c8635d72fe
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 61f7e5afc65019f1817b15ae84ca3f7b42e3ece9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugvirtualunwindernext-method"></a><span data-ttu-id="74951-102">Método ICorDebugVirtualUnwinder::Next</span><span class="sxs-lookup"><span data-stu-id="74951-102">ICorDebugVirtualUnwinder::Next Method</span></span>
<span data-ttu-id="74951-103">Avança para o contexto do chamador.</span><span class="sxs-lookup"><span data-stu-id="74951-103">Advances to the caller's context.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74951-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="74951-104">Syntax</span></span>  
  
```  
HRESULT Next();  
```  
  
#### <a name="parameters"></a><span data-ttu-id="74951-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="74951-105">Parameters</span></span>  
 <span data-ttu-id="74951-106">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="74951-106">None.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="74951-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="74951-107">Return Value</span></span>  
 <span data-ttu-id="74951-108">`S_OK`Se o desenrolamento ocorreu com êxito, ou `CORDBG_S_AT_END_OF_STACK` se o desenrolamento não pode ser concluído porque não há nenhum quadro mais.</span><span class="sxs-lookup"><span data-stu-id="74951-108">`S_OK` if the unwind occurred successfully, or `CORDBG_S_AT_END_OF_STACK` if the unwind cannot be completed because there are no more frames.</span></span>  
  
 <span data-ttu-id="74951-109">Se uma falha de HRESULT é retornado, ICorDebug APIs retornarão `CORDBG_E_DATA_TARGET_ERROR`.</span><span class="sxs-lookup"><span data-stu-id="74951-109">If a failing HRESULT is returned, ICorDebug APIs will return `CORDBG_E_DATA_TARGET_ERROR`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="74951-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="74951-110">Remarks</span></span>  
 <span data-ttu-id="74951-111">O movimentador de pilha deve garantir que ele faz assim que eventualmente progresso, uma chamada para `Next` retornará uma falha HRESULT ou `CORDBG_S_AT_END_OF_STACK`.</span><span class="sxs-lookup"><span data-stu-id="74951-111">The stack walker should ensure that it makes forward progress, so that eventually a call to `Next` will return a failing HRESULT or `CORDBG_S_AT_END_OF_STACK`.</span></span> <span data-ttu-id="74951-112">Retornando `S_OK` indefinidamente pode causar um loop infinito.</span><span class="sxs-lookup"><span data-stu-id="74951-112">Returning `S_OK` indefinitely may cause an infinite loop.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="74951-113">Esse método só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="74951-113">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="74951-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="74951-114">Requirements</span></span>  
 <span data-ttu-id="74951-115">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="74951-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="74951-116">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="74951-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="74951-117">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="74951-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="74951-118">**Versões do .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="74951-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74951-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="74951-119">See Also</span></span>  
 [<span data-ttu-id="74951-120">Interface ICorDebugMemoryBuffer</span><span class="sxs-lookup"><span data-stu-id="74951-120">ICorDebugMemoryBuffer Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)  
 [<span data-ttu-id="74951-121">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="74951-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
