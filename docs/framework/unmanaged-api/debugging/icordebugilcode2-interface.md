---
title: Interface ICorDebugILCode2
ms.date: 03/30/2017
api_name:
- ICorDebugILCode2
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: f9dc2afd-df8a-464d-bdbf-5af0a1d4bf85
topic_type:
- apiref
ms.openlocfilehash: 65995e8386b3bc686178b79d4fbb21a7c71bed3e
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83210326"
---
# <a name="icordebugilcode2-interface"></a><span data-ttu-id="f48e5-102">Interface ICorDebugILCode2</span><span class="sxs-lookup"><span data-stu-id="f48e5-102">ICorDebugILCode2 Interface</span></span>
<span data-ttu-id="f48e5-103">[Com suporte no .NET Framework 4.5.2 e versões posteriores]</span><span class="sxs-lookup"><span data-stu-id="f48e5-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="f48e5-104">Estende logicamente a interface [ICorDebugILCode](icordebugilcode-interface.md) para fornecer métodos que retornam o token para a assinatura de variável local de uma função e que mapeiam os deslocamentos de Il (linguagem intermediária instrumentada) de um criador de perfil para os deslocamentos de Il do método original.</span><span class="sxs-lookup"><span data-stu-id="f48e5-104">Logically extends the [ICorDebugILCode](icordebugilcode-interface.md) interface to provide methods that return the token for a function's local variable signature, and that map a profiler's instrumented intermediate language (IL) offsets to original method IL offsets.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f48e5-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="f48e5-105">Methods</span></span>  
  
|<span data-ttu-id="f48e5-106">Método</span><span class="sxs-lookup"><span data-stu-id="f48e5-106">Method</span></span>|<span data-ttu-id="f48e5-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="f48e5-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f48e5-108">Método GetInstrumentedILMap</span><span class="sxs-lookup"><span data-stu-id="f48e5-108">GetInstrumentedILMap Method</span></span>](icordebugilcode2-getinstrumentedilmap-method.md)|<span data-ttu-id="f48e5-109">Retorna um mapa de deslocamentos da IL instrumentada do criador de perfil para os deslocamentos da IL do método original para esta instância.</span><span class="sxs-lookup"><span data-stu-id="f48e5-109">Returns a map from profiler instrumented IL offsets to original method IL offsets for this instance.</span></span>|  
|[<span data-ttu-id="f48e5-110">Método GetLocalVarSigToken</span><span class="sxs-lookup"><span data-stu-id="f48e5-110">GetLocalVarSigToken Method</span></span>](icordebugilcode2-getlocalvarsigtoken-method.md)|<span data-ttu-id="f48e5-111">Obtém o token de metadados para a assinatura de variável local para a função que é representada por esta instância.</span><span class="sxs-lookup"><span data-stu-id="f48e5-111">Gets the metadata token for the local variable signature for the function that is represented by this instance.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f48e5-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f48e5-112">Requirements</span></span>  
 <span data-ttu-id="f48e5-113">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f48e5-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f48e5-114">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f48e5-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f48e5-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f48e5-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f48e5-116">**.NET Framework versões:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f48e5-116">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f48e5-117">Confira também</span><span class="sxs-lookup"><span data-stu-id="f48e5-117">See also</span></span>

- [<span data-ttu-id="f48e5-118">Interface ICorDebugILCode</span><span class="sxs-lookup"><span data-stu-id="f48e5-118">ICorDebugILCode Interface</span></span>](icordebugilcode-interface.md)
- [<span data-ttu-id="f48e5-119">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="f48e5-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="f48e5-120">Depuração</span><span class="sxs-lookup"><span data-stu-id="f48e5-120">Debugging</span></span>](index.md)
