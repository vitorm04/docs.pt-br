---
title: Interface ICorDebugGuidToTypeEnum
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugGuidToTypeEnum
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugGuidToTypeEnum
helpviewer_keywords: ICorDebugGuidToTypeEnum interface [.NET Framework debugging]
ms.assetid: aa32b12b-05fc-4ea8-a904-adae25034269
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9993a5aaaef3d5b83d21e3641029af12119188da
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugguidtotypeenum-interface"></a><span data-ttu-id="1dfb4-102">Interface ICorDebugGuidToTypeEnum</span><span class="sxs-lookup"><span data-stu-id="1dfb4-102">ICorDebugGuidToTypeEnum Interface</span></span>
<span data-ttu-id="1dfb4-103">Fornece um enumerador que define o mapeamento entre um conjunto de GUIDs e seus tipos correspondentes, são representados por instâncias de ICorDebugType.</span><span class="sxs-lookup"><span data-stu-id="1dfb4-103">Provides an enumerator that defines the mapping between a set of GUIDs and their corresponding types, which are represented by ICorDebugType instances.</span></span> <span data-ttu-id="1dfb4-104">Esta interface herda os métodos da interface ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="1dfb4-104">This interface inherits the methods from the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1dfb4-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="1dfb4-105">Methods</span></span>  
  
|<span data-ttu-id="1dfb4-106">Método</span><span class="sxs-lookup"><span data-stu-id="1dfb4-106">Method</span></span>|<span data-ttu-id="1dfb4-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="1dfb4-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1dfb4-108">Icordebugguidtotypeenum</span><span class="sxs-lookup"><span data-stu-id="1dfb4-108">ICorDebugGuidToTypeEnum::Next</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-next-method.md)|<span data-ttu-id="1dfb4-109">Obtém o número especificado de [CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) instâncias que mapeiam os GUIDs para informações de tipo.</span><span class="sxs-lookup"><span data-stu-id="1dfb4-109">Gets the specified number of [CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) instances that map GUIDs to type information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1dfb4-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="1dfb4-110">Remarks</span></span>  
 <span data-ttu-id="1dfb4-111">Um `ICorDebugGuidToTypeEnum` objeto de interface pode ser recuperado chamando o [Icordebugappdomain3](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="1dfb4-111">An `ICorDebugGuidToTypeEnum` interface object can be retrieved by calling the [ICorDebugAppDomain3::GetCachedWinRTTypes](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md) method.</span></span> <span data-ttu-id="1dfb4-112">Um depurador pode chamar essa interface [próximo](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-next-method.md) método para recuperar [CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) gerenciados de objetos que representam os mapeamentos de representações de [!INCLUDE[wrt](../../../../includes/wrt-md.md)] tipos carregados do domínio do aplicativo usado para a chamada a [Icordebugappdomain3](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="1dfb4-112">A debugger can call this interface's [Next](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-next-method.md) method to retrieve [CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) objects that represent mappings of managed representations of [!INCLUDE[wrt](../../../../includes/wrt-md.md)] types loaded in the application domain used for the call to the [ICorDebugAppDomain3::GetCachedWinRTTypes](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1dfb4-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1dfb4-113">Requirements</span></span>  
 <span data-ttu-id="1dfb4-114">**Plataformas:**[!INCLUDE[wrt](../../../../includes/wrt-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1dfb4-114">**Platforms:** [!INCLUDE[wrt](../../../../includes/wrt-md.md)]</span></span>  
  
 <span data-ttu-id="1dfb4-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1dfb4-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1dfb4-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1dfb4-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1dfb4-117">**Versões do .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1dfb4-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1dfb4-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1dfb4-118">See Also</span></span>  
 [<span data-ttu-id="1dfb4-119">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="1dfb4-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
