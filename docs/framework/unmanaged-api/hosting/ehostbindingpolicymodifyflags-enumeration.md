---
title: Enumeração EHostBindingPolicyModifyFlags
ms.date: 03/30/2017
api_name:
- EHostBindingPolicyModifyFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EHostBindingPolicyModifyFlags
helpviewer_keywords:
- EHostBindingPolicyModifyFlags enumeration [.NET Framework hosting]
ms.assetid: 0339af16-ee1d-48ec-837d-a79d9a9c89f8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0e8357d20edba993f5a7682f31c04afea4362afd
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59080209"
---
# <a name="ehostbindingpolicymodifyflags-enumeration"></a><span data-ttu-id="29ac3-102">Enumeração EHostBindingPolicyModifyFlags</span><span class="sxs-lookup"><span data-stu-id="29ac3-102">EHostBindingPolicyModifyFlags Enumeration</span></span>
<span data-ttu-id="29ac3-103">Permite que o host especificar o tipo de redirecionamento, que o common language runtime (CLR) deve executar ao aplicar as modificações de política de um assembly de origem para um assembly de destino.</span><span class="sxs-lookup"><span data-stu-id="29ac3-103">Allows the host to specify the type of redirection the common language runtime (CLR) should perform when applying policy modifications from a source assembly to a target assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29ac3-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="29ac3-104">Syntax</span></span>  
  
```  
typedef enum _hostBindingPolicyModifyFlags {  
    HOST_BINDING_POLICY_MODIFY_DEFAULT  = 0,  
    HOST_BINDING_POLICY_MODIFY_CHAIN    = 1,  
    HOST_BINDING_POLICY_MODIFY_REMOVE   = 2,  
    HOST_BINDING_POLICY_MODIFY_MAX      = 3  
} EHostBindingPolicyModifyFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="29ac3-105">Membros</span><span class="sxs-lookup"><span data-stu-id="29ac3-105">Members</span></span>  
  
|<span data-ttu-id="29ac3-106">Membro</span><span class="sxs-lookup"><span data-stu-id="29ac3-106">Member</span></span>|<span data-ttu-id="29ac3-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="29ac3-107">Description</span></span>|  
|------------|-----------------|  
|`HOST_BINDING_POLICY_MODIFY_CHAIN`|<span data-ttu-id="29ac3-108">Especifica que o CLR será encadear os valores da política do assembly de origem para as do assembly de destino.</span><span class="sxs-lookup"><span data-stu-id="29ac3-108">Specifies that the CLR will chain policy values of the source assembly onto those of the target assembly.</span></span>|  
|`HOST_BINDING_POLICY_MODIFY_DEFAULT`|<span data-ttu-id="29ac3-109">Especifica que o CLR executará a ação padrão.</span><span class="sxs-lookup"><span data-stu-id="29ac3-109">Specifies that the CLR will perform the default action.</span></span>|  
|`HOST_BINDING_POLICY_MODIFY_MAX`|<span data-ttu-id="29ac3-110">Especifica que o CLR definirá os valores da política do assembly de destino para os valores máximos.</span><span class="sxs-lookup"><span data-stu-id="29ac3-110">Specifies that the CLR will set the policy values of the target assembly to the maximum values.</span></span>|  
|`HOST_BINDING_POLICY_MODIFY_REMOVE`|<span data-ttu-id="29ac3-111">Especifica que o CLR substituirá os valores da diretiva de assembly de destino com as do assembly de código-fonte.</span><span class="sxs-lookup"><span data-stu-id="29ac3-111">Specifies that the CLR will replace policy values of the target assembly with those of the source assembly.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="29ac3-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="29ac3-112">Remarks</span></span>  
 <span data-ttu-id="29ac3-113">O [iclrhostbindingpolicymanager:: Modifyapplicationpolicy](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-modifyapplicationpolicy-method.md) método utiliza um parâmetro de tipo `EHostBindingPolicyModifyFlags`.</span><span class="sxs-lookup"><span data-stu-id="29ac3-113">The [ICLRHostBindingPolicyManager::ModifyApplicationPolicy](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-modifyapplicationpolicy-method.md) method takes a parameter of type `EHostBindingPolicyModifyFlags`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="29ac3-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="29ac3-114">Requirements</span></span>  
 <span data-ttu-id="29ac3-115">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="29ac3-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="29ac3-116">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="29ac3-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="29ac3-117">**Biblioteca:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="29ac3-117">**Library:** MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="29ac3-118">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="29ac3-118">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="29ac3-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="29ac3-119">See also</span></span>

- [<span data-ttu-id="29ac3-120">Interface ICLRHostBindingPolicyManager</span><span class="sxs-lookup"><span data-stu-id="29ac3-120">ICLRHostBindingPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)
- [<span data-ttu-id="29ac3-121">Hospedando enumerações</span><span class="sxs-lookup"><span data-stu-id="29ac3-121">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
