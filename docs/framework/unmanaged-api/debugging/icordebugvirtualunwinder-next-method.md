---
title: 'Método ICorDebugVirtualUnwinder:: Next'
ms.date: 03/30/2017
ms.assetid: 790e0426-e5cd-49fd-a792-f8c8635d72fe
ms.openlocfilehash: ed80b7a630f78002ded14a1bec206cc8712bd504
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121854"
---
# <a name="icordebugvirtualunwindernext-method"></a><span data-ttu-id="0d0b0-102">Método ICorDebugVirtualUnwinder:: Next</span><span class="sxs-lookup"><span data-stu-id="0d0b0-102">ICorDebugVirtualUnwinder::Next Method</span></span>
<span data-ttu-id="0d0b0-103">Avança para o contexto do chamador.</span><span class="sxs-lookup"><span data-stu-id="0d0b0-103">Advances to the caller's context.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d0b0-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0d0b0-104">Syntax</span></span>  
  
```cpp  
HRESULT Next();  
```  
  
## <a name="parameters"></a><span data-ttu-id="0d0b0-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0d0b0-105">Parameters</span></span>  
 <span data-ttu-id="0d0b0-106">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="0d0b0-106">None.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0d0b0-107">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="0d0b0-107">Return Value</span></span>  
 <span data-ttu-id="0d0b0-108">`S_OK` se o desenrolar tiver ocorrido com êxito ou `CORDBG_S_AT_END_OF_STACK` se o desenrolamento não puder ser concluído porque não há mais quadros.</span><span class="sxs-lookup"><span data-stu-id="0d0b0-108">`S_OK` if the unwind occurred successfully, or `CORDBG_S_AT_END_OF_STACK` if the unwind cannot be completed because there are no more frames.</span></span>  
  
 <span data-ttu-id="0d0b0-109">Se um HRESULT com falha for retornado, as APIs ICorDebug retornarão `CORDBG_E_DATA_TARGET_ERROR`.</span><span class="sxs-lookup"><span data-stu-id="0d0b0-109">If a failing HRESULT is returned, ICorDebug APIs will return `CORDBG_E_DATA_TARGET_ERROR`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0d0b0-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="0d0b0-110">Remarks</span></span>  
 <span data-ttu-id="0d0b0-111">O Stack Walker deve garantir que ele faça o andamento do encaminhamento, de modo que, eventualmente, uma chamada para `Next` retornará um HRESULT ou `CORDBG_S_AT_END_OF_STACK`com falha.</span><span class="sxs-lookup"><span data-stu-id="0d0b0-111">The stack walker should ensure that it makes forward progress, so that eventually a call to `Next` will return a failing HRESULT or `CORDBG_S_AT_END_OF_STACK`.</span></span> <span data-ttu-id="0d0b0-112">Retornar `S_OK` indefinidamente pode causar um loop infinito.</span><span class="sxs-lookup"><span data-stu-id="0d0b0-112">Returning `S_OK` indefinitely may cause an infinite loop.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0d0b0-113">Esse método está disponível somente com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="0d0b0-113">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0d0b0-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0d0b0-114">Requirements</span></span>  
 <span data-ttu-id="0d0b0-115">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0d0b0-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0d0b0-116">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0d0b0-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0d0b0-117">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0d0b0-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0d0b0-118">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0d0b0-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d0b0-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0d0b0-119">See also</span></span>

- [<span data-ttu-id="0d0b0-120">Interface ICorDebugMemoryBuffer</span><span class="sxs-lookup"><span data-stu-id="0d0b0-120">ICorDebugMemoryBuffer Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)
- [<span data-ttu-id="0d0b0-121">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="0d0b0-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
