---
title: "Enumeração COR_PRF_STATIC_TYPE"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_PRF_STATIC_TYPE
api_location: mscorwks.dll
api_type: COM
f1_keywords: COR_PRF_STATIC_TYPE
helpviewer_keywords: COR_PRF_STATIC_TYPE enumeration [.NET Framework profiling]
ms.assetid: 441d7809-5b65-41a5-ba64-2910a8008315
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 446967cc157962a1ec4a87193bbf84b1a356efa6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="corprfstatictype-enumeration"></a><span data-ttu-id="310af-102">Enumeração COR_PRF_STATIC_TYPE</span><span class="sxs-lookup"><span data-stu-id="310af-102">COR_PRF_STATIC_TYPE Enumeration</span></span>
<span data-ttu-id="310af-103">Indica se um campo é estático e, em caso positivo, a qualidade estática aplicada ao campo.</span><span class="sxs-lookup"><span data-stu-id="310af-103">Indicates whether a field is static and, if so, the static quality that applies to the field.</span></span> <span data-ttu-id="310af-104">Esses valores podem ser combinados usando a operação OR bit a bit para indicar que o campo tem várias qualidades estáticas diferentes.</span><span class="sxs-lookup"><span data-stu-id="310af-104">These values can be combined using the bitwise OR operation to indicate that the field has multiple, different static qualities.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="310af-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="310af-105">Syntax</span></span>  
  
```  
typedef enum {  
    COR_PRF_FIELD_NOT_A_STATIC = 0x0,  
    COR_PRF_FIELD_APP_DOMAIN_STATIC = 0x1,  
    COR_PRF_FIELD_THREAD_STATIC = 0x2,  
    COR_PRF_FIELD_CONTEXT_STATIC = 0x4,  
    COR_PRF_FIELD_RVA_STATIC = 0x8  
} COR_PRF_STATIC_TYPE;  
```  
  
## <a name="members"></a><span data-ttu-id="310af-106">Membros</span><span class="sxs-lookup"><span data-stu-id="310af-106">Members</span></span>  
  
|<span data-ttu-id="310af-107">Membro</span><span class="sxs-lookup"><span data-stu-id="310af-107">Member</span></span>|<span data-ttu-id="310af-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="310af-108">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_FIELD_NOT_A_STATIC`|<span data-ttu-id="310af-109">O campo não é estático.</span><span class="sxs-lookup"><span data-stu-id="310af-109">The field is not static.</span></span>|  
|`COR_PRF_FIELD_APP_DOMAIN_STATIC`|<span data-ttu-id="310af-110">O campo é estático de domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="310af-110">The field is application domain-static.</span></span>|  
|`COR_PRF_FIELD_THREAD_STATIC`|<span data-ttu-id="310af-111">O campo é de thread estático.</span><span class="sxs-lookup"><span data-stu-id="310af-111">The field is thread-static.</span></span>|  
|`COR_PRF_FIELD_CONTEXT_STATIC`|<span data-ttu-id="310af-112">O campo é o contexto estático.</span><span class="sxs-lookup"><span data-stu-id="310af-112">The field is context-static.</span></span>|  
|`COR_PRF_FIELD_RVA_STATIC`|<span data-ttu-id="310af-113">O campo é o endereço virtual relativo (RVA)-estático.</span><span class="sxs-lookup"><span data-stu-id="310af-113">The field is relative virtual address (RVA)-static.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="310af-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="310af-114">Requirements</span></span>  
 <span data-ttu-id="310af-115">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="310af-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="310af-116">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="310af-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="310af-117">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="310af-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="310af-118">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="310af-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="310af-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="310af-119">See Also</span></span>  
 [<span data-ttu-id="310af-120">Enumerações de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="310af-120">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
