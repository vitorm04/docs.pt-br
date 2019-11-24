---
title: Enumeração CeeSectionAttr
ms.date: 03/30/2017
api_name:
- CeeSectionAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CeeSectionAttr
helpviewer_keywords:
- CeeSectionAttr enumeration [.NET Framework metadata]
ms.assetid: 0db51881-b869-4677-a715-1726a9216489
topic_type:
- apiref
ms.openlocfilehash: 97b28c961f43388679615ac0d5b19c4c69df1e3d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74444254"
---
# <a name="ceesectionattr-enumeration"></a><span data-ttu-id="43c91-102">Enumeração CeeSectionAttr</span><span class="sxs-lookup"><span data-stu-id="43c91-102">CeeSectionAttr Enumeration</span></span>
<span data-ttu-id="43c91-103">Provides values that specify attributes of a section for use by the [ICeeGen](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="43c91-103">Provides values that specify attributes of a section for use by the [ICeeGen](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43c91-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="43c91-104">Syntax</span></span>  
  
```cpp  
typedef enum  {  
    sdNone      = 0,  
    sdReadOnly  = IMAGE_SCN_CNT_INITIALIZED_DATA |  
                  IMAGE_SCN_MEM_READ,  
    sdReadWrite = sdReadOnly | IMAGE_SCN_MEM_WRITE,  
    sdExecute   = IMAGE_SCN_MEM_READ | IMAGE_SCN_CNT_CODE |  
                  IMAGE_SCN_MEM_EXECUTE  
} CeeSectionAttr;  
```  
  
## <a name="members"></a><span data-ttu-id="43c91-105">Membros</span><span class="sxs-lookup"><span data-stu-id="43c91-105">Members</span></span>  
  
|<span data-ttu-id="43c91-106">Membro</span><span class="sxs-lookup"><span data-stu-id="43c91-106">Member</span></span>|<span data-ttu-id="43c91-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="43c91-107">Description</span></span>|  
|------------|-----------------|  
|`sdNone`|<span data-ttu-id="43c91-108">Section has no attributes.</span><span class="sxs-lookup"><span data-stu-id="43c91-108">Section has no attributes.</span></span>|  
|`sdReadOnly`|<span data-ttu-id="43c91-109">Section contains initialized data that can be only read, not updated.</span><span class="sxs-lookup"><span data-stu-id="43c91-109">Section contains initialized data that can be only read, not updated.</span></span>|  
|`sdReadWrite`|<span data-ttu-id="43c91-110">Section contains initialized data that can be read or updated.</span><span class="sxs-lookup"><span data-stu-id="43c91-110">Section contains initialized data that can be read or updated.</span></span>|  
|`sdExecute`|<span data-ttu-id="43c91-111">Section contains executable code that is allowed to be read and executed.</span><span class="sxs-lookup"><span data-stu-id="43c91-111">Section contains executable code that is allowed to be read and executed.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="43c91-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="43c91-112">Requirements</span></span>  
 <span data-ttu-id="43c91-113">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="43c91-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="43c91-114">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="43c91-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="43c91-115">**Library:** Included as a resource in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="43c91-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="43c91-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="43c91-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43c91-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="43c91-117">See also</span></span>

- [<span data-ttu-id="43c91-118">Enumerações de metadados</span><span class="sxs-lookup"><span data-stu-id="43c91-118">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
