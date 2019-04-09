---
title: Interface ICorDebugGuidToTypeEnum
ms.date: 03/30/2017
api_name:
- ICorDebugGuidToTypeEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugGuidToTypeEnum
helpviewer_keywords:
- ICorDebugGuidToTypeEnum interface [.NET Framework debugging]
ms.assetid: aa32b12b-05fc-4ea8-a904-adae25034269
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f2ea67c6e4d860d41cfe67aaab73babb51f3ce45
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59210653"
---
# <a name="icordebugguidtotypeenum-interface"></a><span data-ttu-id="f8193-102">Interface ICorDebugGuidToTypeEnum</span><span class="sxs-lookup"><span data-stu-id="f8193-102">ICorDebugGuidToTypeEnum Interface</span></span>
<span data-ttu-id="f8193-103">Fornece um enumerador que define o mapeamento entre um conjunto de GUIDs e seus tipos correspondentes, que são representados por instâncias do ICorDebugType.</span><span class="sxs-lookup"><span data-stu-id="f8193-103">Provides an enumerator that defines the mapping between a set of GUIDs and their corresponding types, which are represented by ICorDebugType instances.</span></span> <span data-ttu-id="f8193-104">Essa interface herda os métodos da interface ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="f8193-104">This interface inherits the methods from the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f8193-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="f8193-105">Methods</span></span>  
  
|<span data-ttu-id="f8193-106">Método</span><span class="sxs-lookup"><span data-stu-id="f8193-106">Method</span></span>|<span data-ttu-id="f8193-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="f8193-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f8193-108">ICorDebugGuidToTypeEnum::Next</span><span class="sxs-lookup"><span data-stu-id="f8193-108">ICorDebugGuidToTypeEnum::Next</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-next-method.md)|<span data-ttu-id="f8193-109">Obtém o número especificado de [CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) instâncias que mapeiam as GUIDs para informações de tipo.</span><span class="sxs-lookup"><span data-stu-id="f8193-109">Gets the specified number of [CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) instances that map GUIDs to type information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f8193-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="f8193-110">Remarks</span></span>  
 <span data-ttu-id="f8193-111">Uma `ICorDebugGuidToTypeEnum` o objeto de interface pode ser recuperado chamando o [ICorDebugAppDomain3::GetCachedWinRTTypes](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="f8193-111">An `ICorDebugGuidToTypeEnum` interface object can be retrieved by calling the [ICorDebugAppDomain3::GetCachedWinRTTypes](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md) method.</span></span> <span data-ttu-id="f8193-112">Um depurador pode chamar essa interface [próxima](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-next-method.md) método para recuperar [CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) gerenciada de objetos que representam os mapeamentos de representações de [!INCLUDE[wrt](../../../../includes/wrt-md.md)] tipos carregados no domínio de aplicativo usado para a chamada para o [ICorDebugAppDomain3::GetCachedWinRTTypes](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="f8193-112">A debugger can call this interface's [Next](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-next-method.md) method to retrieve [CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) objects that represent mappings of managed representations of [!INCLUDE[wrt](../../../../includes/wrt-md.md)] types loaded in the application domain used for the call to the [ICorDebugAppDomain3::GetCachedWinRTTypes](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f8193-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f8193-113">Requirements</span></span>  
 **<span data-ttu-id="f8193-114">Plataformas:</span><span class="sxs-lookup"><span data-stu-id="f8193-114">Platforms:</span></span>** [!INCLUDE[wrt](../../../../includes/wrt-md.md)]  
  
 <span data-ttu-id="f8193-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f8193-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f8193-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f8193-116">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="f8193-117">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="f8193-117">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="f8193-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f8193-118">See also</span></span>

- [<span data-ttu-id="f8193-119">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="f8193-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
