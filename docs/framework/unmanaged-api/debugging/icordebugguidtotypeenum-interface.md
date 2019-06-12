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
ms.openlocfilehash: 22cd08154268bdf1e819a0ec0067b05a81d60b22
ms.sourcegitcommit: 5bc85ad81d96b8dc2a90ce53bada475ee5662c44
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/12/2019
ms.locfileid: "67025829"
---
# <a name="icordebugguidtotypeenum-interface"></a><span data-ttu-id="2154e-102">Interface ICorDebugGuidToTypeEnum</span><span class="sxs-lookup"><span data-stu-id="2154e-102">ICorDebugGuidToTypeEnum Interface</span></span>
<span data-ttu-id="2154e-103">Fornece um enumerador que define o mapeamento entre um conjunto de GUIDs e seus tipos correspondentes, que são representados por instâncias do ICorDebugType.</span><span class="sxs-lookup"><span data-stu-id="2154e-103">Provides an enumerator that defines the mapping between a set of GUIDs and their corresponding types, which are represented by ICorDebugType instances.</span></span> <span data-ttu-id="2154e-104">Essa interface herda os métodos da interface ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="2154e-104">This interface inherits the methods from the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2154e-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="2154e-105">Methods</span></span>  
  
|<span data-ttu-id="2154e-106">Método</span><span class="sxs-lookup"><span data-stu-id="2154e-106">Method</span></span>|<span data-ttu-id="2154e-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="2154e-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2154e-108">ICorDebugGuidToTypeEnum::Next</span><span class="sxs-lookup"><span data-stu-id="2154e-108">ICorDebugGuidToTypeEnum::Next</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-next-method.md)|<span data-ttu-id="2154e-109">Obtém o número especificado de [CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) instâncias que mapeiam as GUIDs para informações de tipo.</span><span class="sxs-lookup"><span data-stu-id="2154e-109">Gets the specified number of [CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) instances that map GUIDs to type information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2154e-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="2154e-110">Remarks</span></span>  
 <span data-ttu-id="2154e-111">Uma `ICorDebugGuidToTypeEnum` o objeto de interface pode ser recuperado chamando o [ICorDebugAppDomain3::GetCachedWinRTTypes](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="2154e-111">An `ICorDebugGuidToTypeEnum` interface object can be retrieved by calling the [ICorDebugAppDomain3::GetCachedWinRTTypes](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md) method.</span></span> <span data-ttu-id="2154e-112">Um depurador pode chamar essa interface [próxima](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-next-method.md) método para recuperar [CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) objetos que representam os mapeamentos das representações gerenciadas dos tipos de tempo de execução do Windows carregados no domínio de aplicativo usado para a chamada para o [ICorDebugAppDomain3::GetCachedWinRTTypes](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="2154e-112">A debugger can call this interface's [Next](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-next-method.md) method to retrieve [CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) objects that represent mappings of managed representations of Windows Runtime types loaded in the application domain used for the call to the [ICorDebugAppDomain3::GetCachedWinRTTypes](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2154e-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2154e-113">Requirements</span></span>  
 <span data-ttu-id="2154e-114">**Plataformas:** Tempo de Execução do Windows</span><span class="sxs-lookup"><span data-stu-id="2154e-114">**Platforms:** Windows Runtime</span></span>  
  
 <span data-ttu-id="2154e-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2154e-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2154e-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2154e-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2154e-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2154e-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2154e-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2154e-118">See also</span></span>

- [<span data-ttu-id="2154e-119">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="2154e-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
