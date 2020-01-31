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
ms.openlocfilehash: ec33e55f840fe735091364ebc35cb7b7c165c10a
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76867173"
---
# <a name="cor_prf_gc_reason-enumeration"></a><span data-ttu-id="251b0-102">Enumeração COR_PRF_GC_REASON</span><span class="sxs-lookup"><span data-stu-id="251b0-102">COR_PRF_GC_REASON Enumeration</span></span>
<span data-ttu-id="251b0-103">Indica o motivo pelo qual essa coleta de lixo está ocorrendo.</span><span class="sxs-lookup"><span data-stu-id="251b0-103">Indicates the reason that garbage collection is occurring.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="251b0-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="251b0-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_GC_INDUCED = 1,  
    COR_PRF_GC_OTHER = 0  
} COR_PRF_GC_REASON;  
```  
  
## <a name="members"></a><span data-ttu-id="251b0-105">Membros</span><span class="sxs-lookup"><span data-stu-id="251b0-105">Members</span></span>  
  
|<span data-ttu-id="251b0-106">{1&gt;Membro&lt;1}</span><span class="sxs-lookup"><span data-stu-id="251b0-106">Member</span></span>|<span data-ttu-id="251b0-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="251b0-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_GC_INDUCED`|<span data-ttu-id="251b0-108">A coleta de lixo foi induzida por um método de <xref:System.GC.Collect%2A>.</span><span class="sxs-lookup"><span data-stu-id="251b0-108">The garbage collection was induced by a <xref:System.GC.Collect%2A> method.</span></span>|  
|`COR_PRF_GC_OTHER`|<span data-ttu-id="251b0-109">O motivo não foi especificado.</span><span class="sxs-lookup"><span data-stu-id="251b0-109">The reason is unspecified.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="251b0-110">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="251b0-110">Requirements</span></span>  
 <span data-ttu-id="251b0-111">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="251b0-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="251b0-112">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="251b0-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="251b0-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="251b0-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="251b0-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="251b0-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="251b0-115">Veja também</span><span class="sxs-lookup"><span data-stu-id="251b0-115">See also</span></span>

- [<span data-ttu-id="251b0-116">Criando perfil de enumerações</span><span class="sxs-lookup"><span data-stu-id="251b0-116">Profiling Enumerations</span></span>](profiling-enumerations.md)
