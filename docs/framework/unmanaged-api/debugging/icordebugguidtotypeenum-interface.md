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
ms.openlocfilehash: da921644c4d967efb0d88060ada0332c5eb63965
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138524"
---
# <a name="icordebugguidtotypeenum-interface"></a><span data-ttu-id="a5a88-102">Interface ICorDebugGuidToTypeEnum</span><span class="sxs-lookup"><span data-stu-id="a5a88-102">ICorDebugGuidToTypeEnum Interface</span></span>
<span data-ttu-id="a5a88-103">Fornece um enumerador que define o mapeamento entre um conjunto de GUIDs e seus tipos correspondentes, que são representados por instâncias de ICorDebugType.</span><span class="sxs-lookup"><span data-stu-id="a5a88-103">Provides an enumerator that defines the mapping between a set of GUIDs and their corresponding types, which are represented by ICorDebugType instances.</span></span> <span data-ttu-id="a5a88-104">Essa interface herda os métodos da interface ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="a5a88-104">This interface inherits the methods from the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a5a88-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="a5a88-105">Methods</span></span>  
  
|<span data-ttu-id="a5a88-106">Método</span><span class="sxs-lookup"><span data-stu-id="a5a88-106">Method</span></span>|<span data-ttu-id="a5a88-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="a5a88-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a5a88-108">ICorDebugGuidToTypeEnum:: Next</span><span class="sxs-lookup"><span data-stu-id="a5a88-108">ICorDebugGuidToTypeEnum::Next</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-next-method.md)|<span data-ttu-id="a5a88-109">Obtém o número especificado de instâncias de [CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) que MAPEIAm GUIDs para informações de tipo.</span><span class="sxs-lookup"><span data-stu-id="a5a88-109">Gets the specified number of [CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) instances that map GUIDs to type information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a5a88-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="a5a88-110">Remarks</span></span>  
 <span data-ttu-id="a5a88-111">Um objeto de interface `ICorDebugGuidToTypeEnum` pode ser recuperado chamando o método [ICorDebugAppDomain3:: GetCachedWinRTTypes](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md) .</span><span class="sxs-lookup"><span data-stu-id="a5a88-111">An `ICorDebugGuidToTypeEnum` interface object can be retrieved by calling the [ICorDebugAppDomain3::GetCachedWinRTTypes](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md) method.</span></span> <span data-ttu-id="a5a88-112">Um depurador pode chamar o [próximo](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-next-method.md) método da interface para recuperar objetos [CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) que representam mapeamentos de representações gerenciadas de tipos de Windows Runtime carregados no domínio de aplicativo usado para a chamada para o [ Método ICorDebugAppDomain3:: GetCachedWinRTTypes](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md) .</span><span class="sxs-lookup"><span data-stu-id="a5a88-112">A debugger can call this interface's [Next](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-next-method.md) method to retrieve [CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) objects that represent mappings of managed representations of Windows Runtime types loaded in the application domain used for the call to the [ICorDebugAppDomain3::GetCachedWinRTTypes](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a5a88-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a5a88-113">Requirements</span></span>  
 <span data-ttu-id="a5a88-114">**Plataformas:** Windows Runtime</span><span class="sxs-lookup"><span data-stu-id="a5a88-114">**Platforms:** Windows Runtime</span></span>  
  
 <span data-ttu-id="a5a88-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a5a88-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a5a88-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a5a88-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a5a88-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a5a88-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5a88-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a5a88-118">See also</span></span>

- [<span data-ttu-id="a5a88-119">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="a5a88-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
