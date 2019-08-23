---
title: 'Método ICorDebugVirtualUnwinder:: Next'
ms.date: 03/30/2017
ms.assetid: 790e0426-e5cd-49fd-a792-f8c8635d72fe
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 20a3d4bac42731bc94ecef7a0756392c8c0882fc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69967930"
---
# <a name="icordebugvirtualunwindernext-method"></a><span data-ttu-id="97b7d-102">Método ICorDebugVirtualUnwinder:: Next</span><span class="sxs-lookup"><span data-stu-id="97b7d-102">ICorDebugVirtualUnwinder::Next Method</span></span>
<span data-ttu-id="97b7d-103">Avança para o contexto do chamador.</span><span class="sxs-lookup"><span data-stu-id="97b7d-103">Advances to the caller's context.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="97b7d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="97b7d-104">Syntax</span></span>  
  
```cpp  
HRESULT Next();  
```  
  
## <a name="parameters"></a><span data-ttu-id="97b7d-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="97b7d-105">Parameters</span></span>  
 <span data-ttu-id="97b7d-106">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="97b7d-106">None.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="97b7d-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="97b7d-107">Return Value</span></span>  
 <span data-ttu-id="97b7d-108">`S_OK`Se o desenrolar tiver ocorrido com `CORDBG_S_AT_END_OF_STACK` êxito ou se o desenrolamento não puder ser concluído porque não há mais quadros.</span><span class="sxs-lookup"><span data-stu-id="97b7d-108">`S_OK` if the unwind occurred successfully, or `CORDBG_S_AT_END_OF_STACK` if the unwind cannot be completed because there are no more frames.</span></span>  
  
 <span data-ttu-id="97b7d-109">Se um HRESULT com falha for retornado, as APIs do `CORDBG_E_DATA_TARGET_ERROR`ICorDebug serão retornadas.</span><span class="sxs-lookup"><span data-stu-id="97b7d-109">If a failing HRESULT is returned, ICorDebug APIs will return `CORDBG_E_DATA_TARGET_ERROR`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="97b7d-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="97b7d-110">Remarks</span></span>  
 <span data-ttu-id="97b7d-111">O Stack Walker deve garantir que ele faça o andamento do encaminhamento, de modo que `Next` , eventualmente, uma chamada para `CORDBG_S_AT_END_OF_STACK`retornará um HRESULT com falha ou.</span><span class="sxs-lookup"><span data-stu-id="97b7d-111">The stack walker should ensure that it makes forward progress, so that eventually a call to `Next` will return a failing HRESULT or `CORDBG_S_AT_END_OF_STACK`.</span></span> <span data-ttu-id="97b7d-112">Retornar `S_OK` indefinidamente pode causar um loop infinito.</span><span class="sxs-lookup"><span data-stu-id="97b7d-112">Returning `S_OK` indefinitely may cause an infinite loop.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="97b7d-113">Esse método está disponível somente com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="97b7d-113">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="97b7d-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="97b7d-114">Requirements</span></span>  
 <span data-ttu-id="97b7d-115">**Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="97b7d-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="97b7d-116">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="97b7d-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="97b7d-117">**Biblioteca** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="97b7d-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="97b7d-118">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="97b7d-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97b7d-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="97b7d-119">See also</span></span>

- [<span data-ttu-id="97b7d-120">Interface ICorDebugMemoryBuffer</span><span class="sxs-lookup"><span data-stu-id="97b7d-120">ICorDebugMemoryBuffer Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)
- [<span data-ttu-id="97b7d-121">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="97b7d-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
