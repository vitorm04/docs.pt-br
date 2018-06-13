---
title: Enumeração METAHOST_CONFIG_FLAGS
ms.date: 03/30/2017
api_name:
- METAHOST_CONFIG_FLAGS
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- METAHOST_CONFIG_FLAGS
helpviewer_keywords:
- METAHOST_CONFIG_FLAGS enumeration [.NET Framework hosting]
ms.assetid: 6f1e389f-ed99-4d6a-a0ba-72d7d869a01d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a13897f71bb675b982a84d57d310b799989c41aa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33442924"
---
# <a name="metahostconfigflags-enumeration"></a><span data-ttu-id="366f6-102">Enumeração METAHOST_CONFIG_FLAGS</span><span class="sxs-lookup"><span data-stu-id="366f6-102">METAHOST_CONFIG_FLAGS Enumeration</span></span>
<span data-ttu-id="366f6-103">Descreve os possíveis sinalizadores retornados no `pdwConfigFlags` parâmetro do [Iclrmetahostpolicy](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) método, que indica a presença e a configuração do `useLegacyV2RuntimeActivationPolicy` atributo no [ \<inicialização > elemento](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) do arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="366f6-103">Describes the possible flags returned in the `pdwConfigFlags` parameter of the [ICLRMetaHostPolicy::GetRequestedRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) method, indicating the presence and setting of the `useLegacyV2RuntimeActivationPolicy` attribute in the [\<startup> element](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) of the configuration file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="366f6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="366f6-104">Syntax</span></span>  
  
```  
typedef enum {  
    METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_UNSET  = 0x00,  
    METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_TRUE   = 0x01,  
    METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_FALSE  = 0x02,  
    METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_MASK   = 0x03  
} METAHOST_CONFIG_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="366f6-105">Membros</span><span class="sxs-lookup"><span data-stu-id="366f6-105">Members</span></span>  
  
|<span data-ttu-id="366f6-106">Membro</span><span class="sxs-lookup"><span data-stu-id="366f6-106">Member</span></span>|<span data-ttu-id="366f6-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="366f6-107">Description</span></span>|  
|------------|-----------------|  
|`METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_UNSET`|<span data-ttu-id="366f6-108">O `useLegacyV2RuntimeActivationPolicy` atributo não estava presente no [ \<inicialização > elemento](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md).</span><span class="sxs-lookup"><span data-stu-id="366f6-108">The `useLegacyV2RuntimeActivationPolicy` attribute was not present in the [\<startup> Element](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md).</span></span>|  
|`METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_TRUE`|<span data-ttu-id="366f6-109">O `useLegacyV2RuntimeActivationPolicy` atributo estava presente e definida para `true`.</span><span class="sxs-lookup"><span data-stu-id="366f6-109">The `useLegacyV2RuntimeActivationPolicy` attribute was present and set to `true`.</span></span>|  
|`METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_FALSE`|<span data-ttu-id="366f6-110">O `useLegacyV2RuntimeActivationPolicy` atributo estava presente e definida para `false`.</span><span class="sxs-lookup"><span data-stu-id="366f6-110">The `useLegacyV2RuntimeActivationPolicy` attribute was present and set to `false`.</span></span>|  
|`METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_MASK`|<span data-ttu-id="366f6-111">Aplicar essa máscara para o valor retornado em `pdwConfigFlags` para obter os valores relevantes para `useLegacyV2RuntimeActivationPolicy`.</span><span class="sxs-lookup"><span data-stu-id="366f6-111">Apply this mask to the value returned in `pdwConfigFlags` to get the values relevant to `useLegacyV2RuntimeActivationPolicy`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="366f6-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="366f6-112">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="366f6-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="366f6-113">Requirements</span></span>  
 <span data-ttu-id="366f6-114">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="366f6-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="366f6-115">**Cabeçalho:** Metahost.h</span><span class="sxs-lookup"><span data-stu-id="366f6-115">**Header:** Metahost.h</span></span>  
  
 <span data-ttu-id="366f6-116">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="366f6-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="366f6-117">**Versões do .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="366f6-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="366f6-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="366f6-118">See Also</span></span>  
 [<span data-ttu-id="366f6-119">Enumerações de hospedagem</span><span class="sxs-lookup"><span data-stu-id="366f6-119">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)  
 [<span data-ttu-id="366f6-120">Método GetRequestedRuntime</span><span class="sxs-lookup"><span data-stu-id="366f6-120">GetRequestedRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md)  
 [<span data-ttu-id="366f6-121">Elemento \<startup></span><span class="sxs-lookup"><span data-stu-id="366f6-121">\<startup> Element</span></span>](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md)
