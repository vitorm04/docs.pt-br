---
title: Enumeração COR_PRF_GC_REASON
ms.date: 03/30/2017
api_name:
- COR_PRF_GC_REASON
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_GC_REASON
helpviewer_keywords:
- COR_PRF_GC_REASON enumeration [.NET Framework profiling]
ms.assetid: 72822b95-a7fb-485e-9d55-1cb016d9a458
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: daf97f25b1adc30b173fcd81812a4b197915cdd1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59196938"
---
# <a name="corprfgcreason-enumeration"></a><span data-ttu-id="72110-102">Enumeração COR_PRF_GC_REASON</span><span class="sxs-lookup"><span data-stu-id="72110-102">COR_PRF_GC_REASON Enumeration</span></span>
<span data-ttu-id="72110-103">Indica o motivo pelo qual essa coleta de lixo está ocorrendo.</span><span class="sxs-lookup"><span data-stu-id="72110-103">Indicates the reason that garbage collection is occurring.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72110-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="72110-104">Syntax</span></span>  
  
```  
typedef enum {  
    COR_PRF_GC_INDUCED = 1,  
    COR_PRF_GC_OTHER = 0  
} COR_PRF_GC_REASON;  
```  
  
## <a name="members"></a><span data-ttu-id="72110-105">Membros</span><span class="sxs-lookup"><span data-stu-id="72110-105">Members</span></span>  
  
|<span data-ttu-id="72110-106">Membro</span><span class="sxs-lookup"><span data-stu-id="72110-106">Member</span></span>|<span data-ttu-id="72110-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="72110-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_GC_INDUCED`|<span data-ttu-id="72110-108">A coleta de lixo foi induzida por um <xref:System.GC.Collect%2A> método.</span><span class="sxs-lookup"><span data-stu-id="72110-108">The garbage collection was induced by a <xref:System.GC.Collect%2A> method.</span></span>|  
|`COR_PRF_GC_OTHER`|<span data-ttu-id="72110-109">O motivo pelo qual não é especificado.</span><span class="sxs-lookup"><span data-stu-id="72110-109">The reason is unspecified.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="72110-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="72110-110">Requirements</span></span>  
 <span data-ttu-id="72110-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="72110-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="72110-112">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="72110-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="72110-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="72110-113">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="72110-114">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="72110-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="72110-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="72110-115">See also</span></span>

- [<span data-ttu-id="72110-116">Criando perfil de enumerações</span><span class="sxs-lookup"><span data-stu-id="72110-116">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
