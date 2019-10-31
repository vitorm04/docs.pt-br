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
ms.openlocfilehash: a2faf22b48dd0b809d6c3668a37f2119733a9b18
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129443"
---
# <a name="ehostbindingpolicymodifyflags-enumeration"></a><span data-ttu-id="a5374-102">Enumeração EHostBindingPolicyModifyFlags</span><span class="sxs-lookup"><span data-stu-id="a5374-102">EHostBindingPolicyModifyFlags Enumeration</span></span>
<span data-ttu-id="a5374-103">Permite que o host especifique o tipo de redirecionamento que o Common Language Runtime (CLR) deve executar ao aplicar as modificações de política de um assembly de origem a um assembly de destino.</span><span class="sxs-lookup"><span data-stu-id="a5374-103">Allows the host to specify the type of redirection the common language runtime (CLR) should perform when applying policy modifications from a source assembly to a target assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a5374-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a5374-104">Syntax</span></span>  
  
```cpp  
typedef enum _hostBindingPolicyModifyFlags {  
    HOST_BINDING_POLICY_MODIFY_DEFAULT  = 0,  
    HOST_BINDING_POLICY_MODIFY_CHAIN    = 1,  
    HOST_BINDING_POLICY_MODIFY_REMOVE   = 2,  
    HOST_BINDING_POLICY_MODIFY_MAX      = 3  
} EHostBindingPolicyModifyFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="a5374-105">Membros</span><span class="sxs-lookup"><span data-stu-id="a5374-105">Members</span></span>  
  
|<span data-ttu-id="a5374-106">Membro</span><span class="sxs-lookup"><span data-stu-id="a5374-106">Member</span></span>|<span data-ttu-id="a5374-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="a5374-107">Description</span></span>|  
|------------|-----------------|  
|`HOST_BINDING_POLICY_MODIFY_CHAIN`|<span data-ttu-id="a5374-108">Especifica que o CLR encadeará os valores de política do assembly de origem para aqueles do assembly de destino.</span><span class="sxs-lookup"><span data-stu-id="a5374-108">Specifies that the CLR will chain policy values of the source assembly onto those of the target assembly.</span></span>|  
|`HOST_BINDING_POLICY_MODIFY_DEFAULT`|<span data-ttu-id="a5374-109">Especifica que o CLR executará a ação padrão.</span><span class="sxs-lookup"><span data-stu-id="a5374-109">Specifies that the CLR will perform the default action.</span></span>|  
|`HOST_BINDING_POLICY_MODIFY_MAX`|<span data-ttu-id="a5374-110">Especifica que o CLR definirá os valores de política do assembly de destino para os valores máximos.</span><span class="sxs-lookup"><span data-stu-id="a5374-110">Specifies that the CLR will set the policy values of the target assembly to the maximum values.</span></span>|  
|`HOST_BINDING_POLICY_MODIFY_REMOVE`|<span data-ttu-id="a5374-111">Especifica que o CLR substituirá os valores de política do assembly de destino pelos do assembly de origem.</span><span class="sxs-lookup"><span data-stu-id="a5374-111">Specifies that the CLR will replace policy values of the target assembly with those of the source assembly.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a5374-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="a5374-112">Remarks</span></span>  
 <span data-ttu-id="a5374-113">O método [ICLRHostBindingPolicyManager:: ModifyApplicationPolicy](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-modifyapplicationpolicy-method.md) usa um parâmetro do tipo `EHostBindingPolicyModifyFlags`.</span><span class="sxs-lookup"><span data-stu-id="a5374-113">The [ICLRHostBindingPolicyManager::ModifyApplicationPolicy](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-modifyapplicationpolicy-method.md) method takes a parameter of type `EHostBindingPolicyModifyFlags`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a5374-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a5374-114">Requirements</span></span>  
 <span data-ttu-id="a5374-115">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a5374-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a5374-116">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="a5374-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a5374-117">**Biblioteca:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="a5374-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a5374-118">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a5374-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5374-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a5374-119">See also</span></span>

- [<span data-ttu-id="a5374-120">Interface ICLRHostBindingPolicyManager</span><span class="sxs-lookup"><span data-stu-id="a5374-120">ICLRHostBindingPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)
- [<span data-ttu-id="a5374-121">Enumerações de hospedagem</span><span class="sxs-lookup"><span data-stu-id="a5374-121">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
