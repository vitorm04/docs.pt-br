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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3b40ac5f49288f7b30018e0c8c727e3ce6b73ae8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59199474"
---
# <a name="corprfmisc-enumeration"></a><span data-ttu-id="b1bdd-102">Enumeração COR_PRF_MISC</span><span class="sxs-lookup"><span data-stu-id="b1bdd-102">COR_PRF_MISC Enumeration</span></span>
<span data-ttu-id="b1bdd-103">Contém valores constantes que especificam identificadores especiais.</span><span class="sxs-lookup"><span data-stu-id="b1bdd-103">Contains constant values that specify special identifiers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1bdd-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b1bdd-104">Syntax</span></span>  
  
```  
typedef enum {  
    PROFILER_PARENT_UNKNOWN = 0xFFFFFFFD,  
    PROFILER_GLOBAL_CLASS   = 0xFFFFFFFE,  
    PROFILER_GLOBAL_MODULE  = 0xFFFFFFFF  
} COR_PRF_MISC;  
```  
  
## <a name="members"></a><span data-ttu-id="b1bdd-105">Membros</span><span class="sxs-lookup"><span data-stu-id="b1bdd-105">Members</span></span>  
  
|<span data-ttu-id="b1bdd-106">Membro</span><span class="sxs-lookup"><span data-stu-id="b1bdd-106">Member</span></span>|<span data-ttu-id="b1bdd-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="b1bdd-107">Description</span></span>|  
|------------|-----------------|  
|`PROFILER_PARENT_UNKNOWN`|<span data-ttu-id="b1bdd-108">O identificador do padrão usado pelo [ICorProfilerInfo:: Getmoduleinfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmoduleinfo-method.md) para um módulo que ainda não foi anexado a um assembly.</span><span class="sxs-lookup"><span data-stu-id="b1bdd-108">The default identifier used by [ICorProfilerInfo::GetModuleInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmoduleinfo-method.md) for a module that has not yet been attached to an assembly.</span></span>|  
|`PROFILER_GLOBAL_CLASS`|<span data-ttu-id="b1bdd-109">O identificador de classe padrão para constantes globais que não pertencem a uma classe.</span><span class="sxs-lookup"><span data-stu-id="b1bdd-109">The default class identifier for global constants that do not belong to a class.</span></span>|  
|`PROFILER_GLOBAL_MODULE`|<span data-ttu-id="b1bdd-110">O identificador de módulo padrão para objetos globais que não pertencem a um módulo.</span><span class="sxs-lookup"><span data-stu-id="b1bdd-110">The default module identifier for global objects that do not belong to a module.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b1bdd-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b1bdd-111">Requirements</span></span>  
 <span data-ttu-id="b1bdd-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b1bdd-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b1bdd-113">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b1bdd-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b1bdd-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b1bdd-114">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="b1bdd-115">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="b1bdd-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="b1bdd-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b1bdd-116">See also</span></span>

- [<span data-ttu-id="b1bdd-117">Criando perfil de enumerações</span><span class="sxs-lookup"><span data-stu-id="b1bdd-117">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
