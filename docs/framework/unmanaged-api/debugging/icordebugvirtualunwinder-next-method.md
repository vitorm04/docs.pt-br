---
title: 'Método ICorDebugVirtualUnwinder:: Next'
ms.date: 03/30/2017
ms.assetid: 790e0426-e5cd-49fd-a792-f8c8635d72fe
ms.openlocfilehash: 06d5377ef123cc3f9c91fbfbcf0b0f17a14eb629
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790811"
---
# <a name="icordebugvirtualunwindernext-method"></a><span data-ttu-id="295f1-102">Método ICorDebugVirtualUnwinder:: Next</span><span class="sxs-lookup"><span data-stu-id="295f1-102">ICorDebugVirtualUnwinder::Next Method</span></span>
<span data-ttu-id="295f1-103">Avança para o contexto do chamador.</span><span class="sxs-lookup"><span data-stu-id="295f1-103">Advances to the caller's context.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="295f1-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="295f1-104">Syntax</span></span>  
  
```cpp  
HRESULT Next();  
```  
  
## <a name="parameters"></a><span data-ttu-id="295f1-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="295f1-105">Parameters</span></span>  
 <span data-ttu-id="295f1-106">Nenhuma.</span><span class="sxs-lookup"><span data-stu-id="295f1-106">None.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="295f1-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="295f1-107">Return Value</span></span>  
 <span data-ttu-id="295f1-108">`S_OK` se o desenrolar tiver ocorrido com êxito ou `CORDBG_S_AT_END_OF_STACK` se o desenrolamento não puder ser concluído porque não há mais quadros.</span><span class="sxs-lookup"><span data-stu-id="295f1-108">`S_OK` if the unwind occurred successfully, or `CORDBG_S_AT_END_OF_STACK` if the unwind cannot be completed because there are no more frames.</span></span>  
  
 <span data-ttu-id="295f1-109">Se um HRESULT com falha for retornado, as APIs ICorDebug retornarão `CORDBG_E_DATA_TARGET_ERROR`.</span><span class="sxs-lookup"><span data-stu-id="295f1-109">If a failing HRESULT is returned, ICorDebug APIs will return `CORDBG_E_DATA_TARGET_ERROR`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="295f1-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="295f1-110">Remarks</span></span>  
 <span data-ttu-id="295f1-111">O Stack Walker deve garantir que ele faça o andamento do encaminhamento, de modo que, eventualmente, uma chamada para `Next` retornará um HRESULT ou `CORDBG_S_AT_END_OF_STACK`com falha.</span><span class="sxs-lookup"><span data-stu-id="295f1-111">The stack walker should ensure that it makes forward progress, so that eventually a call to `Next` will return a failing HRESULT or `CORDBG_S_AT_END_OF_STACK`.</span></span> <span data-ttu-id="295f1-112">Retornar `S_OK` indefinidamente pode causar um loop infinito.</span><span class="sxs-lookup"><span data-stu-id="295f1-112">Returning `S_OK` indefinitely may cause an infinite loop.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="295f1-113">Esse método está disponível somente com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="295f1-113">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="295f1-114">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="295f1-114">Requirements</span></span>  
 <span data-ttu-id="295f1-115">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="295f1-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="295f1-116">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="295f1-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="295f1-117">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="295f1-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="295f1-118">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="295f1-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="295f1-119">Veja também</span><span class="sxs-lookup"><span data-stu-id="295f1-119">See also</span></span>

- [<span data-ttu-id="295f1-120">Interface ICorDebugMemoryBuffer</span><span class="sxs-lookup"><span data-stu-id="295f1-120">ICorDebugMemoryBuffer Interface</span></span>](icordebugmemorybuffer-interface.md)
- [<span data-ttu-id="295f1-121">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="295f1-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
