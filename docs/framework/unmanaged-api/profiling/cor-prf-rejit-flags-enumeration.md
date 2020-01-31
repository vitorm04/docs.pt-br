---
title: Enumeração COR_PRF_REJIT_FLAGS
ms.date: 08/06/2019
api_name:
- COR_PRF_REJIT_FLAGS Enumeration
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_REJIT_FLAGS
helpviewer_keywords:
- COR_PRF_REJIT_FLAGS enumeration [.NET Framework profiling]
topic_type:
- apiref
author: davmason
ms.author: davmason
ms.openlocfilehash: fabbcd497dc2f321da90188cebbac6ed4e147492
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76867081"
---
# <a name="cor_prf_rejit_flags-enumeration"></a><span data-ttu-id="92c0a-102">Enumeração COR_PRF_REJIT_FLAGS</span><span class="sxs-lookup"><span data-stu-id="92c0a-102">COR_PRF_REJIT_FLAGS Enumeration</span></span>
<span data-ttu-id="92c0a-103">Contém valores que indicam como a API [ICorProfilerInfo10:: RequestReJITWithInliners](icorprofilerinfo10-requestrejitwithinliners-method.md) deve se comportar.</span><span class="sxs-lookup"><span data-stu-id="92c0a-103">Contains values that indicate how the [ICorProfilerInfo10::RequestReJITWithInliners](icorprofilerinfo10-requestrejitwithinliners-method.md) API should behave.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92c0a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="92c0a-104">Syntax</span></span>  
  
```cpp  
typedef enum  
{      
    COR_PRF_REJIT_BLOCK_INLINING = 0x1,
    COR_PRF_REJIT_INLINING_CALLBACKS    = 0x2
} COR_PRF_REJIT_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="92c0a-105">Membros</span><span class="sxs-lookup"><span data-stu-id="92c0a-105">Members</span></span>  
  
|<span data-ttu-id="92c0a-106">{1&gt;Membro&lt;1}</span><span class="sxs-lookup"><span data-stu-id="92c0a-106">Member</span></span>|<span data-ttu-id="92c0a-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="92c0a-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_REJIT_BLOCK_INLINING`| <span data-ttu-id="92c0a-108">Os métodos ReJITted serão impedidos de serem embutidos em outros métodos.</span><span class="sxs-lookup"><span data-stu-id="92c0a-108">ReJITted methods will be blocked from being inlined in other methods.</span></span> |  
|`COR_PRF_REJIT_INLINING_CALLBACKS`| <span data-ttu-id="92c0a-109">Receba `GetFunctionParameters` retornos de chamada para os métodos que embutiram os métodos solicitados a serem ReJITteddos.</span><span class="sxs-lookup"><span data-stu-id="92c0a-109">Receive `GetFunctionParameters` callbacks for any methods that inline the methods requested to be ReJITted.</span></span> |  

## <a name="requirements"></a><span data-ttu-id="92c0a-110">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="92c0a-110">Requirements</span></span>  
 <span data-ttu-id="92c0a-111">**Plataformas:** Consulte [sistemas operacionais com suporte do .NET Core](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="92c0a-111">**Platforms:** See [.NET Core supported operating systems](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows).</span></span>  
  
 <span data-ttu-id="92c0a-112">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="92c0a-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="92c0a-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="92c0a-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="92c0a-114">**Versões do .NET Framework:** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]</span><span class="sxs-lookup"><span data-stu-id="92c0a-114">**.NET Framework Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]</span></span> 
  
## <a name="see-also"></a><span data-ttu-id="92c0a-115">Veja também</span><span class="sxs-lookup"><span data-stu-id="92c0a-115">See also</span></span>

- [<span data-ttu-id="92c0a-116">Criando perfil de enumerações</span><span class="sxs-lookup"><span data-stu-id="92c0a-116">Profiling Enumerations</span></span>](profiling-enumerations.md)
