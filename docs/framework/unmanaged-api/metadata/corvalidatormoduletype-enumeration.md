---
title: Enumeração CorValidatorModuleType
ms.date: 03/30/2017
api_name:
- CorValidatorModuleType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorValidatorModuleType
helpviewer_keywords:
- CorValidatorModuleType enumeration [.NET Framework metadata]
ms.assetid: 748f1ab2-fbcb-4f55-89ec-8d23d81ebc80
topic_type:
- apiref
ms.openlocfilehash: a8dc09ee9f0f0fd79060bb86c599ab40a285153b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448767"
---
# <a name="corvalidatormoduletype-enumeration"></a><span data-ttu-id="f86db-102">Enumeração CorValidatorModuleType</span><span class="sxs-lookup"><span data-stu-id="f86db-102">CorValidatorModuleType Enumeration</span></span>
<span data-ttu-id="f86db-103">Specifies the type of a module.</span><span class="sxs-lookup"><span data-stu-id="f86db-103">Specifies the type of a module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f86db-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f86db-104">Syntax</span></span>  
  
```cpp  
typedef enum  
{  
    ValidatorModuleTypeInvalid  = 0x0,  
    ValidatorModuleTypeMin      = 0x00000001,  
    ValidatorModuleTypePE       = 0x00000001,  
    ValidatorModuleTypeObj      = 0x00000002,  
    ValidatorModuleTypeEnc      = 0x00000003,  
    ValidatorModuleTypeIncr     = 0x00000004,  
    ValidatorModuleTypeMax      = 0x00000004  
} CorValidatorModuleType;  
```  
  
## <a name="members"></a><span data-ttu-id="f86db-105">Membros</span><span class="sxs-lookup"><span data-stu-id="f86db-105">Members</span></span>  
  
|<span data-ttu-id="f86db-106">Membro</span><span class="sxs-lookup"><span data-stu-id="f86db-106">Member</span></span>|<span data-ttu-id="f86db-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="f86db-107">Description</span></span>|  
|------------|-----------------|  
|`ValidatorModuleTypeInvalid`|<span data-ttu-id="f86db-108">The module is an invalid type.</span><span class="sxs-lookup"><span data-stu-id="f86db-108">The module is an invalid type.</span></span>|  
|`ValidatorModuleTypeMin`|<span data-ttu-id="f86db-109">The minimum value of the `CorValidatorModuleType` enum.</span><span class="sxs-lookup"><span data-stu-id="f86db-109">The minimum value of the `CorValidatorModuleType` enum.</span></span>|  
|`ValidatorModuleTypePE`|<span data-ttu-id="f86db-110">The module is a portable executable (PE) file.</span><span class="sxs-lookup"><span data-stu-id="f86db-110">The module is a portable executable (PE) file.</span></span>|  
|`ValidatorModuleTypeObj`|<span data-ttu-id="f86db-111">The module is a .obj file.</span><span class="sxs-lookup"><span data-stu-id="f86db-111">The module is a .obj file.</span></span>|  
|`ValidatorModuleTypeEnc`|<span data-ttu-id="f86db-112">The module is an edit-and-continue debugger session.</span><span class="sxs-lookup"><span data-stu-id="f86db-112">The module is an edit-and-continue debugger session.</span></span>|  
|`ValidatorModuleTypeIncr`|<span data-ttu-id="f86db-113">The module is one that has been incrementally built.</span><span class="sxs-lookup"><span data-stu-id="f86db-113">The module is one that has been incrementally built.</span></span>|  
|`ValidatorModuleTypeMax`|<span data-ttu-id="f86db-114">The maximum value of the `CorValidatorModuleType` enum.</span><span class="sxs-lookup"><span data-stu-id="f86db-114">The maximum value of the `CorValidatorModuleType` enum.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f86db-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f86db-115">Requirements</span></span>  
 <span data-ttu-id="f86db-116">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f86db-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f86db-117">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="f86db-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f86db-118">**Library:** Included as a resource in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f86db-118">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f86db-119">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f86db-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f86db-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f86db-120">See also</span></span>

- [<span data-ttu-id="f86db-121">Enumerações de metadados</span><span class="sxs-lookup"><span data-stu-id="f86db-121">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
