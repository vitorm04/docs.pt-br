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
ms.openlocfilehash: 81aef6beb9ee6d622519738d24fdd0a4d42a75b1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136557"
---
# <a name="ebindpolicylevels-enumeration"></a><span data-ttu-id="8a193-102">Enumeração EBindPolicyLevels</span><span class="sxs-lookup"><span data-stu-id="8a193-102">EBindPolicyLevels Enumeration</span></span>
<span data-ttu-id="8a193-103">Fornece sinalizadores para especificar o nível no qual aplicar ou modificar a política de assembly.</span><span class="sxs-lookup"><span data-stu-id="8a193-103">Provides flags to specify the level at which to apply or modify assembly policy.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8a193-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8a193-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="8a193-105">Membros</span><span class="sxs-lookup"><span data-stu-id="8a193-105">Members</span></span>  
  
|<span data-ttu-id="8a193-106">Membro</span><span class="sxs-lookup"><span data-stu-id="8a193-106">Member</span></span>|<span data-ttu-id="8a193-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="8a193-107">Description</span></span>|  
|------------|-----------------|  
|`ePolicyLevelAdmin`|<span data-ttu-id="8a193-108">Especifica que a política deve ser aplicada no nível de administrador.</span><span class="sxs-lookup"><span data-stu-id="8a193-108">Specifies that policy should be applied at the administrator level.</span></span>|  
|`ePolicyLevelApp`|<span data-ttu-id="8a193-109">Especifica que a política deve ser aplicada no nível do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8a193-109">Specifies that policy should be applied at the application level.</span></span>|  
|`ePolicyLevelHost`|<span data-ttu-id="8a193-110">Especifica que a política deve ser aplicada no nível do host.</span><span class="sxs-lookup"><span data-stu-id="8a193-110">Specifies that policy should be applied at the host level.</span></span>|  
|`ePolicyLevelNone`|<span data-ttu-id="8a193-111">Especifica nenhum sinalizador de nível de política.</span><span class="sxs-lookup"><span data-stu-id="8a193-111">Specifies no policy-level flags.</span></span>|  
|`ePolicyLevelPublisher`|<span data-ttu-id="8a193-112">Especifica que a política deve ser aplicada no nível do Publicador.</span><span class="sxs-lookup"><span data-stu-id="8a193-112">Specifies that policy should be applied at the publisher level.</span></span>|  
|`ePolicyLevelRetargetable`|<span data-ttu-id="8a193-113">Especifica que a política deve ser aplicável em níveis de variável.</span><span class="sxs-lookup"><span data-stu-id="8a193-113">Specifies that policy should be applicable at variable levels.</span></span>|  
|`ePolicyPortability`|<span data-ttu-id="8a193-114">Especifica que a política deve dar suporte à portabilidade entre as implementações de um assembly .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="8a193-114">Specifies that policy should support portability between implementations of a .NET Framework assembly.</span></span> <span data-ttu-id="8a193-115">Consulte o elemento arquivo de configuração [\<supportPortability >](../../../../docs/framework/configure-apps/file-schema/runtime/supportportability-element.md) .</span><span class="sxs-lookup"><span data-stu-id="8a193-115">See the [\<supportPortability>](../../../../docs/framework/configure-apps/file-schema/runtime/supportportability-element.md) configuration file element.</span></span>|  
|`ePolicyUnifiedToCLR`|<span data-ttu-id="8a193-116">Especifica que a política deve ser unificada para a do Common Language Runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="8a193-116">Specifies that policy should be unified to that of the common language runtime (CLR).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8a193-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="8a193-117">Remarks</span></span>  
 <span data-ttu-id="8a193-118">Essa enumeração é passada para métodos da interface [ICLRHostBindingPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md) para especificar alterações na política de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8a193-118">This enumeration is passed to methods of the [ICLRHostBindingPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md) interface to specify changes in application policy.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8a193-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8a193-119">Requirements</span></span>  
 <span data-ttu-id="8a193-120">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8a193-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8a193-121">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="8a193-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8a193-122">**Biblioteca:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="8a193-122">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8a193-123">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8a193-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a193-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8a193-124">See also</span></span>

- [<span data-ttu-id="8a193-125">Interface ICLRAssemblyIdentityManager</span><span class="sxs-lookup"><span data-stu-id="8a193-125">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="8a193-126">Enumerações de hospedagem</span><span class="sxs-lookup"><span data-stu-id="8a193-126">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
