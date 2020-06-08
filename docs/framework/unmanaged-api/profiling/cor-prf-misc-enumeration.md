---
title: Enumeração COR_PRF_MISC
ms.date: 03/30/2017
api_name:
- COR_PRF_MISC
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_MISC
helpviewer_keywords:
- COR_PRF_MISC enumeration [.NET Framework profiling]
ms.assetid: 619bb5de-e309-48b6-a3af-32d935a0ff46
topic_type:
- apiref
ms.openlocfilehash: 7b8f2845589a8372f62c95ef1a82eae3ed602c1f
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500826"
---
# <a name="cor_prf_misc-enumeration"></a><span data-ttu-id="4fef2-102">Enumeração COR_PRF_MISC</span><span class="sxs-lookup"><span data-stu-id="4fef2-102">COR_PRF_MISC Enumeration</span></span>
<span data-ttu-id="4fef2-103">Contém valores constantes que especificam identificadores especiais.</span><span class="sxs-lookup"><span data-stu-id="4fef2-103">Contains constant values that specify special identifiers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4fef2-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4fef2-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    PROFILER_PARENT_UNKNOWN = 0xFFFFFFFD,  
    PROFILER_GLOBAL_CLASS   = 0xFFFFFFFE,  
    PROFILER_GLOBAL_MODULE  = 0xFFFFFFFF  
} COR_PRF_MISC;  
```  
  
## <a name="members"></a><span data-ttu-id="4fef2-105">Membros</span><span class="sxs-lookup"><span data-stu-id="4fef2-105">Members</span></span>  
  
|<span data-ttu-id="4fef2-106">Membro</span><span class="sxs-lookup"><span data-stu-id="4fef2-106">Member</span></span>|<span data-ttu-id="4fef2-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="4fef2-107">Description</span></span>|  
|------------|-----------------|  
|`PROFILER_PARENT_UNKNOWN`|<span data-ttu-id="4fef2-108">O identificador padrão usado por [ICorProfilerInfo:: GetModuleInfo](icorprofilerinfo-getmoduleinfo-method.md) para um módulo que ainda não foi anexado a um assembly.</span><span class="sxs-lookup"><span data-stu-id="4fef2-108">The default identifier used by [ICorProfilerInfo::GetModuleInfo](icorprofilerinfo-getmoduleinfo-method.md) for a module that has not yet been attached to an assembly.</span></span>|  
|`PROFILER_GLOBAL_CLASS`|<span data-ttu-id="4fef2-109">O identificador de classe padrão para constantes globais que não pertencem a uma classe.</span><span class="sxs-lookup"><span data-stu-id="4fef2-109">The default class identifier for global constants that do not belong to a class.</span></span>|  
|`PROFILER_GLOBAL_MODULE`|<span data-ttu-id="4fef2-110">O identificador de módulo padrão para objetos globais que não pertencem a um módulo.</span><span class="sxs-lookup"><span data-stu-id="4fef2-110">The default module identifier for global objects that do not belong to a module.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4fef2-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4fef2-111">Requirements</span></span>  
 <span data-ttu-id="4fef2-112">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4fef2-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4fef2-113">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="4fef2-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4fef2-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4fef2-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4fef2-115">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4fef2-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4fef2-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="4fef2-116">See also</span></span>

- [<span data-ttu-id="4fef2-117">Criando perfil de enumerações</span><span class="sxs-lookup"><span data-stu-id="4fef2-117">Profiling Enumerations</span></span>](profiling-enumerations.md)
