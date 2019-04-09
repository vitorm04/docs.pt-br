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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b8f2b08662e719a3308a62ab5b60f5dc490f2a6a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59142201"
---
# <a name="ebindpolicylevels-enumeration"></a><span data-ttu-id="973f9-102">Enumeração EBindPolicyLevels</span><span class="sxs-lookup"><span data-stu-id="973f9-102">EBindPolicyLevels Enumeration</span></span>
<span data-ttu-id="973f9-103">Fornece sinalizadores para especificar o nível no qual aplicar ou modificar a diretiva de assembly.</span><span class="sxs-lookup"><span data-stu-id="973f9-103">Provides flags to specify the level at which to apply or modify assembly policy.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="973f9-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="973f9-104">Syntax</span></span>  
  
```  
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
  
## <a name="members"></a><span data-ttu-id="973f9-105">Membros</span><span class="sxs-lookup"><span data-stu-id="973f9-105">Members</span></span>  
  
|<span data-ttu-id="973f9-106">Membro</span><span class="sxs-lookup"><span data-stu-id="973f9-106">Member</span></span>|<span data-ttu-id="973f9-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="973f9-107">Description</span></span>|  
|------------|-----------------|  
|`ePolicyLevelAdmin`|<span data-ttu-id="973f9-108">Especifica que a política deve ser aplicada no nível de administrador.</span><span class="sxs-lookup"><span data-stu-id="973f9-108">Specifies that policy should be applied at the administrator level.</span></span>|  
|`ePolicyLevelApp`|<span data-ttu-id="973f9-109">Especifica que a política deve ser aplicada no nível do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="973f9-109">Specifies that policy should be applied at the application level.</span></span>|  
|`ePolicyLevelHost`|<span data-ttu-id="973f9-110">Especifica que a política deve ser aplicada no nível do host.</span><span class="sxs-lookup"><span data-stu-id="973f9-110">Specifies that policy should be applied at the host level.</span></span>|  
|`ePolicyLevelNone`|<span data-ttu-id="973f9-111">Não especifica que nenhum sinalizador de nível de política.</span><span class="sxs-lookup"><span data-stu-id="973f9-111">Specifies no policy-level flags.</span></span>|  
|`ePolicyLevelPublisher`|<span data-ttu-id="973f9-112">Especifica que a política deve ser aplicada no nível do publicador.</span><span class="sxs-lookup"><span data-stu-id="973f9-112">Specifies that policy should be applied at the publisher level.</span></span>|  
|`ePolicyLevelRetargetable`|<span data-ttu-id="973f9-113">Especifica que política deve ser aplicável em níveis de variável.</span><span class="sxs-lookup"><span data-stu-id="973f9-113">Specifies that policy should be applicable at variable levels.</span></span>|  
|`ePolicyPortability`|<span data-ttu-id="973f9-114">Especifica que a política deve oferecer suporte a portabilidade entre implementações de um assembly do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="973f9-114">Specifies that policy should support portability between implementations of a .NET Framework assembly.</span></span> <span data-ttu-id="973f9-115">Consulte a [ \<supportPortability >](../../../../docs/framework/configure-apps/file-schema/runtime/supportportability-element.md) elemento do arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="973f9-115">See the [\<supportPortability>](../../../../docs/framework/configure-apps/file-schema/runtime/supportportability-element.md) configuration file element.</span></span>|  
|`ePolicyUnifiedToCLR`|<span data-ttu-id="973f9-116">Especifica que política deve ser unificada do common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="973f9-116">Specifies that policy should be unified to that of the common language runtime (CLR).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="973f9-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="973f9-117">Remarks</span></span>  
 <span data-ttu-id="973f9-118">Essa enumeração é passada para métodos do [ICLRHostBindingPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md) interface para especificar as alterações na política de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="973f9-118">This enumeration is passed to methods of the [ICLRHostBindingPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md) interface to specify changes in application policy.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="973f9-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="973f9-119">Requirements</span></span>  
 <span data-ttu-id="973f9-120">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="973f9-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="973f9-121">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="973f9-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="973f9-122">**Biblioteca:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="973f9-122">**Library:** MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="973f9-123">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="973f9-123">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="973f9-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="973f9-124">See also</span></span>

- [<span data-ttu-id="973f9-125">Interface ICLRAssemblyIdentityManager</span><span class="sxs-lookup"><span data-stu-id="973f9-125">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="973f9-126">Hospedando enumerações</span><span class="sxs-lookup"><span data-stu-id="973f9-126">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
