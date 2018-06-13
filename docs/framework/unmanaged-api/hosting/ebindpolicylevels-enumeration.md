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
ms.openlocfilehash: 1da1d368725ab0a2334080c1caa7d4e25f5f3bab
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33431117"
---
# <a name="ebindpolicylevels-enumeration"></a><span data-ttu-id="208bb-102">Enumeração EBindPolicyLevels</span><span class="sxs-lookup"><span data-stu-id="208bb-102">EBindPolicyLevels Enumeration</span></span>
<span data-ttu-id="208bb-103">Fornece os sinalizadores para especificar o nível no qual aplicar ou modificar a diretiva de assembly.</span><span class="sxs-lookup"><span data-stu-id="208bb-103">Provides flags to specify the level at which to apply or modify assembly policy.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="208bb-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="208bb-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="208bb-105">Membros</span><span class="sxs-lookup"><span data-stu-id="208bb-105">Members</span></span>  
  
|<span data-ttu-id="208bb-106">Membro</span><span class="sxs-lookup"><span data-stu-id="208bb-106">Member</span></span>|<span data-ttu-id="208bb-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="208bb-107">Description</span></span>|  
|------------|-----------------|  
|`ePolicyLevelAdmin`|<span data-ttu-id="208bb-108">Especifica que a política deve ser aplicada no nível de administrador.</span><span class="sxs-lookup"><span data-stu-id="208bb-108">Specifies that policy should be applied at the administrator level.</span></span>|  
|`ePolicyLevelApp`|<span data-ttu-id="208bb-109">Especifica que a política deve ser aplicada no nível do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="208bb-109">Specifies that policy should be applied at the application level.</span></span>|  
|`ePolicyLevelHost`|<span data-ttu-id="208bb-110">Especifica que a política deve ser aplicada no nível do host.</span><span class="sxs-lookup"><span data-stu-id="208bb-110">Specifies that policy should be applied at the host level.</span></span>|  
|`ePolicyLevelNone`|<span data-ttu-id="208bb-111">Não especifica os sinalizadores nenhum nível de política.</span><span class="sxs-lookup"><span data-stu-id="208bb-111">Specifies no policy-level flags.</span></span>|  
|`ePolicyLevelPublisher`|<span data-ttu-id="208bb-112">Especifica que a política deve ser aplicada no nível do publicador.</span><span class="sxs-lookup"><span data-stu-id="208bb-112">Specifies that policy should be applied at the publisher level.</span></span>|  
|`ePolicyLevelRetargetable`|<span data-ttu-id="208bb-113">Especifica que política deve ser aplicável em níveis de variável.</span><span class="sxs-lookup"><span data-stu-id="208bb-113">Specifies that policy should be applicable at variable levels.</span></span>|  
|`ePolicyPortability`|<span data-ttu-id="208bb-114">Especifica que a política deve oferecer suporte portabilidade entre implementações de um assembly do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="208bb-114">Specifies that policy should support portability between implementations of a .NET Framework assembly.</span></span> <span data-ttu-id="208bb-115">Consulte o [ \<supportPortability >](../../../../docs/framework/configure-apps/file-schema/runtime/supportportability-element.md) elemento do arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="208bb-115">See the [\<supportPortability>](../../../../docs/framework/configure-apps/file-schema/runtime/supportportability-element.md) configuration file element.</span></span>|  
|`ePolicyUnifiedToCLR`|<span data-ttu-id="208bb-116">Especifica que deve ser unificada política para que o common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="208bb-116">Specifies that policy should be unified to that of the common language runtime (CLR).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="208bb-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="208bb-117">Remarks</span></span>  
 <span data-ttu-id="208bb-118">Essa enumeração é passada para métodos do [ICLRHostBindingPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md) interface para especificar as alterações na política de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="208bb-118">This enumeration is passed to methods of the [ICLRHostBindingPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md) interface to specify changes in application policy.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="208bb-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="208bb-119">Requirements</span></span>  
 <span data-ttu-id="208bb-120">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="208bb-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="208bb-121">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="208bb-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="208bb-122">**Biblioteca:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="208bb-122">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="208bb-123">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="208bb-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="208bb-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="208bb-124">See Also</span></span>  
 [<span data-ttu-id="208bb-125">Interface ICLRAssemblyIdentityManager</span><span class="sxs-lookup"><span data-stu-id="208bb-125">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 [<span data-ttu-id="208bb-126">Enumerações de hospedagem</span><span class="sxs-lookup"><span data-stu-id="208bb-126">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
