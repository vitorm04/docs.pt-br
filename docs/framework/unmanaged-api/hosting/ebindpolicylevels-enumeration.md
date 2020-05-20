---
title: Enumeração EBindPolicyLevels
ms.date: 03/30/2017
api_name:
- EBindPolicyLevels
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EBindPolicyLevels
helpviewer_keywords:
- EBindPolicyLevels enumeration [.NET Framework hosting]
ms.assetid: a9e00b4f-b6d0-4257-bd88-4fe9af97b8fa
topic_type:
- apiref
ms.openlocfilehash: 94d2ec12309249afbecdc4130f8fe20c927b0a9b
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616366"
---
# <a name="ebindpolicylevels-enumeration"></a><span data-ttu-id="c8327-102">Enumeração EBindPolicyLevels</span><span class="sxs-lookup"><span data-stu-id="c8327-102">EBindPolicyLevels Enumeration</span></span>
<span data-ttu-id="c8327-103">Fornece sinalizadores para especificar o nível no qual aplicar ou modificar a política de assembly.</span><span class="sxs-lookup"><span data-stu-id="c8327-103">Provides flags to specify the level at which to apply or modify assembly policy.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c8327-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c8327-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    ePolicyLevelNone         = 0x0,  
    ePolicyLevelRetargetable = 0x1,  
    ePolicyUnifiedToCLR      = 0x2,  
    ePolicyLevelApp          = 0x4,  
    ePolicyLevelPublisher    = 0x8,  
    ePolicyLevelHost         = 0x10,  
    ePolicyLevelAdmin        = 0x20  
    ePolicyPortability       = 0x40  
} EBindPolicyLevels;  
```  
  
## <a name="members"></a><span data-ttu-id="c8327-105">Membros</span><span class="sxs-lookup"><span data-stu-id="c8327-105">Members</span></span>  
  
|<span data-ttu-id="c8327-106">Membro</span><span class="sxs-lookup"><span data-stu-id="c8327-106">Member</span></span>|<span data-ttu-id="c8327-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="c8327-107">Description</span></span>|  
|------------|-----------------|  
|`ePolicyLevelAdmin`|<span data-ttu-id="c8327-108">Especifica que a política deve ser aplicada no nível de administrador.</span><span class="sxs-lookup"><span data-stu-id="c8327-108">Specifies that policy should be applied at the administrator level.</span></span>|  
|`ePolicyLevelApp`|<span data-ttu-id="c8327-109">Especifica que a política deve ser aplicada no nível do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c8327-109">Specifies that policy should be applied at the application level.</span></span>|  
|`ePolicyLevelHost`|<span data-ttu-id="c8327-110">Especifica que a política deve ser aplicada no nível do host.</span><span class="sxs-lookup"><span data-stu-id="c8327-110">Specifies that policy should be applied at the host level.</span></span>|  
|`ePolicyLevelNone`|<span data-ttu-id="c8327-111">Especifica nenhum sinalizador de nível de política.</span><span class="sxs-lookup"><span data-stu-id="c8327-111">Specifies no policy-level flags.</span></span>|  
|`ePolicyLevelPublisher`|<span data-ttu-id="c8327-112">Especifica que a política deve ser aplicada no nível do Publicador.</span><span class="sxs-lookup"><span data-stu-id="c8327-112">Specifies that policy should be applied at the publisher level.</span></span>|  
|`ePolicyLevelRetargetable`|<span data-ttu-id="c8327-113">Especifica que a política deve ser aplicável em níveis de variável.</span><span class="sxs-lookup"><span data-stu-id="c8327-113">Specifies that policy should be applicable at variable levels.</span></span>|  
|`ePolicyPortability`|<span data-ttu-id="c8327-114">Especifica que a política deve dar suporte à portabilidade entre as implementações de um assembly .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c8327-114">Specifies that policy should support portability between implementations of a .NET Framework assembly.</span></span> <span data-ttu-id="c8327-115">Consulte o elemento arquivo de configuração do [ \< supportPortability>](../../configure-apps/file-schema/runtime/supportportability-element.md) .</span><span class="sxs-lookup"><span data-stu-id="c8327-115">See the [\<supportPortability>](../../configure-apps/file-schema/runtime/supportportability-element.md) configuration file element.</span></span>|  
|`ePolicyUnifiedToCLR`|<span data-ttu-id="c8327-116">Especifica que a política deve ser unificada para a do Common Language Runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="c8327-116">Specifies that policy should be unified to that of the common language runtime (CLR).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c8327-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="c8327-117">Remarks</span></span>  
 <span data-ttu-id="c8327-118">Essa enumeração é passada para métodos da interface [ICLRHostBindingPolicyManager](iclrhostbindingpolicymanager-interface.md) para especificar alterações na política de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c8327-118">This enumeration is passed to methods of the [ICLRHostBindingPolicyManager](iclrhostbindingpolicymanager-interface.md) interface to specify changes in application policy.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c8327-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c8327-119">Requirements</span></span>  
 <span data-ttu-id="c8327-120">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c8327-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c8327-121">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="c8327-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c8327-122">**Biblioteca:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="c8327-122">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c8327-123">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c8327-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8327-124">Veja também</span><span class="sxs-lookup"><span data-stu-id="c8327-124">See also</span></span>

- [<span data-ttu-id="c8327-125">Interface ICLRAssemblyIdentityManager</span><span class="sxs-lookup"><span data-stu-id="c8327-125">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="c8327-126">Hospedando enumerações</span><span class="sxs-lookup"><span data-stu-id="c8327-126">Hosting Enumerations</span></span>](hosting-enumerations.md)
