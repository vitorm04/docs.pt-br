---
title: "Enumeração EBindPolicyLevels"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 52e4d4522c7401aba198deed7853ccca71752d83
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ebindpolicylevels-enumeration"></a><span data-ttu-id="d7042-102">Enumeração EBindPolicyLevels</span><span class="sxs-lookup"><span data-stu-id="d7042-102">EBindPolicyLevels Enumeration</span></span>
<span data-ttu-id="d7042-103">Fornece os sinalizadores para especificar o nível no qual aplicar ou modificar a diretiva de assembly.</span><span class="sxs-lookup"><span data-stu-id="d7042-103">Provides flags to specify the level at which to apply or modify assembly policy.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7042-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d7042-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="d7042-105">Membros</span><span class="sxs-lookup"><span data-stu-id="d7042-105">Members</span></span>  
  
|<span data-ttu-id="d7042-106">Membro</span><span class="sxs-lookup"><span data-stu-id="d7042-106">Member</span></span>|<span data-ttu-id="d7042-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="d7042-107">Description</span></span>|  
|------------|-----------------|  
|`ePolicyLevelAdmin`|<span data-ttu-id="d7042-108">Especifica que a política deve ser aplicada no nível de administrador.</span><span class="sxs-lookup"><span data-stu-id="d7042-108">Specifies that policy should be applied at the administrator level.</span></span>|  
|`ePolicyLevelApp`|<span data-ttu-id="d7042-109">Especifica que a política deve ser aplicada no nível do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d7042-109">Specifies that policy should be applied at the application level.</span></span>|  
|`ePolicyLevelHost`|<span data-ttu-id="d7042-110">Especifica que a política deve ser aplicada no nível do host.</span><span class="sxs-lookup"><span data-stu-id="d7042-110">Specifies that policy should be applied at the host level.</span></span>|  
|`ePolicyLevelNone`|<span data-ttu-id="d7042-111">Não especifica os sinalizadores nenhum nível de política.</span><span class="sxs-lookup"><span data-stu-id="d7042-111">Specifies no policy-level flags.</span></span>|  
|`ePolicyLevelPublisher`|<span data-ttu-id="d7042-112">Especifica que a política deve ser aplicada no nível do publicador.</span><span class="sxs-lookup"><span data-stu-id="d7042-112">Specifies that policy should be applied at the publisher level.</span></span>|  
|`ePolicyLevelRetargetable`|<span data-ttu-id="d7042-113">Especifica que política deve ser aplicável em níveis de variável.</span><span class="sxs-lookup"><span data-stu-id="d7042-113">Specifies that policy should be applicable at variable levels.</span></span>|  
|`ePolicyPortability`|<span data-ttu-id="d7042-114">Especifica que a política deve oferecer suporte portabilidade entre implementações de um assembly do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d7042-114">Specifies that policy should support portability between implementations of a .NET Framework assembly.</span></span> <span data-ttu-id="d7042-115">Consulte o [ \<supportPortability >](../../../../docs/framework/configure-apps/file-schema/runtime/supportportability-element.md) elemento do arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="d7042-115">See the [\<supportPortability>](../../../../docs/framework/configure-apps/file-schema/runtime/supportportability-element.md) configuration file element.</span></span>|  
|`ePolicyUnifiedToCLR`|<span data-ttu-id="d7042-116">Especifica que deve ser unificada política para que o common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="d7042-116">Specifies that policy should be unified to that of the common language runtime (CLR).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d7042-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="d7042-117">Remarks</span></span>  
 <span data-ttu-id="d7042-118">Essa enumeração é passada para métodos do [ICLRHostBindingPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md) interface para especificar as alterações na política de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d7042-118">This enumeration is passed to methods of the [ICLRHostBindingPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md) interface to specify changes in application policy.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d7042-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d7042-119">Requirements</span></span>  
 <span data-ttu-id="d7042-120">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d7042-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d7042-121">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d7042-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d7042-122">**Biblioteca:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d7042-122">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d7042-123">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d7042-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7042-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d7042-124">See Also</span></span>  
 [<span data-ttu-id="d7042-125">Interface ICLRAssemblyIdentityManager</span><span class="sxs-lookup"><span data-stu-id="d7042-125">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 [<span data-ttu-id="d7042-126">Enumerações de hospedagem</span><span class="sxs-lookup"><span data-stu-id="d7042-126">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
