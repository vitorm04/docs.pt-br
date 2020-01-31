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
ms.openlocfilehash: 30008d6cc98f7d0d0501d67e18703ed5a344d43a
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794359"
---
# <a name="icordebugilcode2-interface"></a><span data-ttu-id="b4836-102">Interface ICorDebugILCode2</span><span class="sxs-lookup"><span data-stu-id="b4836-102">ICorDebugILCode2 Interface</span></span>
<span data-ttu-id="b4836-103">[Com suporte no .NET Framework 4.5.2 e versões posteriores]</span><span class="sxs-lookup"><span data-stu-id="b4836-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="b4836-104">Estende logicamente a interface [ICorDebugILCode](icordebugilcode-interface.md) para fornecer métodos que retornam o token para a assinatura de variável local de uma função e que mapeiam os deslocamentos de Il (linguagem intermediária instrumentada) de um criador de perfil para os deslocamentos de Il do método original.</span><span class="sxs-lookup"><span data-stu-id="b4836-104">Logically extends the [ICorDebugILCode](icordebugilcode-interface.md) interface to provide methods that return the token for a function's local variable signature, and that map a profiler's instrumented intermediate language (IL) offsets to original method IL offsets.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b4836-105">{1&gt;Métodos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="b4836-105">Methods</span></span>  
  
|<span data-ttu-id="b4836-106">Método</span><span class="sxs-lookup"><span data-stu-id="b4836-106">Method</span></span>|<span data-ttu-id="b4836-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="b4836-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b4836-108">Método GetInstrumentedILMap</span><span class="sxs-lookup"><span data-stu-id="b4836-108">GetInstrumentedILMap Method</span></span>](icordebugilcode2-getinstrumentedilmap-method.md)|<span data-ttu-id="b4836-109">Retorna um mapa de deslocamentos da IL instrumentada do criador de perfil para os deslocamentos da IL do método original para esta instância.</span><span class="sxs-lookup"><span data-stu-id="b4836-109">Returns a map from profiler instrumented IL offsets to original method IL offsets for this instance.</span></span>|  
|[<span data-ttu-id="b4836-110">Método GetLocalVarSigToken</span><span class="sxs-lookup"><span data-stu-id="b4836-110">GetLocalVarSigToken Method</span></span>](icordebugilcode2-getlocalvarsigtoken-method.md)|<span data-ttu-id="b4836-111">Obtém o token de metadados para a assinatura de variável local para a função que é representada por esta instância.</span><span class="sxs-lookup"><span data-stu-id="b4836-111">Gets the metadata token for the local variable signature for the function that is represented by this instance.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b4836-112">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="b4836-112">Requirements</span></span>  
 <span data-ttu-id="b4836-113">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b4836-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b4836-114">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b4836-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b4836-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b4836-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b4836-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b4836-116">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4836-117">Veja também</span><span class="sxs-lookup"><span data-stu-id="b4836-117">See also</span></span>

- [<span data-ttu-id="b4836-118">Interface ICorDebugILCode</span><span class="sxs-lookup"><span data-stu-id="b4836-118">ICorDebugILCode Interface</span></span>](icordebugilcode-interface.md)
- [<span data-ttu-id="b4836-119">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="b4836-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="b4836-120">Depuração</span><span class="sxs-lookup"><span data-stu-id="b4836-120">Debugging</span></span>](index.md)
