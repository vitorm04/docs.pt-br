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
ms.openlocfilehash: 63f6ea4a348b3035a1f0b1d3e00f61f689915fa2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33450093"
---
# <a name="corprfgcreason-enumeration"></a><span data-ttu-id="65d68-102">Enumeração COR_PRF_GC_REASON</span><span class="sxs-lookup"><span data-stu-id="65d68-102">COR_PRF_GC_REASON Enumeration</span></span>
<span data-ttu-id="65d68-103">Indica o motivo pelo qual essa coleta de lixo está ocorrendo.</span><span class="sxs-lookup"><span data-stu-id="65d68-103">Indicates the reason that garbage collection is occurring.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65d68-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="65d68-104">Syntax</span></span>  
  
```  
typedef enum {  
    COR_PRF_GC_INDUCED = 1,  
    COR_PRF_GC_OTHER = 0  
} COR_PRF_GC_REASON;  
```  
  
## <a name="members"></a><span data-ttu-id="65d68-105">Membros</span><span class="sxs-lookup"><span data-stu-id="65d68-105">Members</span></span>  
  
|<span data-ttu-id="65d68-106">Membro</span><span class="sxs-lookup"><span data-stu-id="65d68-106">Member</span></span>|<span data-ttu-id="65d68-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="65d68-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_GC_INDUCED`|<span data-ttu-id="65d68-108">A coleta de lixo foi induzida por um <xref:System.GC.Collect%2A> método.</span><span class="sxs-lookup"><span data-stu-id="65d68-108">The garbage collection was induced by a <xref:System.GC.Collect%2A> method.</span></span>|  
|`COR_PRF_GC_OTHER`|<span data-ttu-id="65d68-109">O motivo não está especificado.</span><span class="sxs-lookup"><span data-stu-id="65d68-109">The reason is unspecified.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="65d68-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="65d68-110">Requirements</span></span>  
 <span data-ttu-id="65d68-111">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="65d68-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="65d68-112">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="65d68-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="65d68-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="65d68-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="65d68-114">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="65d68-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65d68-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="65d68-115">See Also</span></span>  
 [<span data-ttu-id="65d68-116">Criando perfil de enumerações</span><span class="sxs-lookup"><span data-stu-id="65d68-116">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
