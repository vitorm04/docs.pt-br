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
ms.openlocfilehash: 6e322f5c7119d13c8a872bd87d00c1e55324b581
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61765187"
---
# <a name="metahostconfigflags-enumeration"></a><span data-ttu-id="5721c-102">Enumeração METAHOST_CONFIG_FLAGS</span><span class="sxs-lookup"><span data-stu-id="5721c-102">METAHOST_CONFIG_FLAGS Enumeration</span></span>
<span data-ttu-id="5721c-103">Descreve os possíveis sinalizadores retornados na `pdwConfigFlags` parâmetro do [iclrmetahostpolicy:: Getrequestedruntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) método, que indica a presença e configuração do `useLegacyV2RuntimeActivationPolicy` atributo no [ \<inicialização > elemento](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) do arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="5721c-103">Describes the possible flags returned in the `pdwConfigFlags` parameter of the [ICLRMetaHostPolicy::GetRequestedRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) method, indicating the presence and setting of the `useLegacyV2RuntimeActivationPolicy` attribute in the [\<startup> element](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) of the configuration file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5721c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5721c-104">Syntax</span></span>  
  
```  
typedef enum {  
    METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_UNSET  = 0x00,  
    METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_TRUE   = 0x01,  
    METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_FALSE  = 0x02,  
    METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_MASK   = 0x03  
} METAHOST_CONFIG_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="5721c-105">Membros</span><span class="sxs-lookup"><span data-stu-id="5721c-105">Members</span></span>  
  
|<span data-ttu-id="5721c-106">Membro</span><span class="sxs-lookup"><span data-stu-id="5721c-106">Member</span></span>|<span data-ttu-id="5721c-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="5721c-107">Description</span></span>|  
|------------|-----------------|  
|`METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_UNSET`|<span data-ttu-id="5721c-108">O `useLegacyV2RuntimeActivationPolicy` não existia no atributo o [ \<inicialização > elemento](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md).</span><span class="sxs-lookup"><span data-stu-id="5721c-108">The `useLegacyV2RuntimeActivationPolicy` attribute was not present in the [\<startup> Element](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md).</span></span>|  
|`METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_TRUE`|<span data-ttu-id="5721c-109">O `useLegacyV2RuntimeActivationPolicy` atributo estava presente e definido para `true`.</span><span class="sxs-lookup"><span data-stu-id="5721c-109">The `useLegacyV2RuntimeActivationPolicy` attribute was present and set to `true`.</span></span>|  
|`METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_FALSE`|<span data-ttu-id="5721c-110">O `useLegacyV2RuntimeActivationPolicy` atributo estava presente e definido para `false`.</span><span class="sxs-lookup"><span data-stu-id="5721c-110">The `useLegacyV2RuntimeActivationPolicy` attribute was present and set to `false`.</span></span>|  
|`METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_MASK`|<span data-ttu-id="5721c-111">Aplicar essa máscara para o valor retornado em `pdwConfigFlags` para obter os valores relevantes para `useLegacyV2RuntimeActivationPolicy`.</span><span class="sxs-lookup"><span data-stu-id="5721c-111">Apply this mask to the value returned in `pdwConfigFlags` to get the values relevant to `useLegacyV2RuntimeActivationPolicy`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5721c-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="5721c-112">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5721c-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5721c-113">Requirements</span></span>  
 <span data-ttu-id="5721c-114">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5721c-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5721c-115">**Cabeçalho:** Metahost.h</span><span class="sxs-lookup"><span data-stu-id="5721c-115">**Header:** Metahost.h</span></span>  
  
 <span data-ttu-id="5721c-116">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="5721c-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5721c-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5721c-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5721c-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5721c-118">See also</span></span>

- [<span data-ttu-id="5721c-119">Enumerações de hospedagem</span><span class="sxs-lookup"><span data-stu-id="5721c-119">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
- [<span data-ttu-id="5721c-120">Método GetRequestedRuntime</span><span class="sxs-lookup"><span data-stu-id="5721c-120">GetRequestedRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md)
- [<span data-ttu-id="5721c-121">Elemento \<startup></span><span class="sxs-lookup"><span data-stu-id="5721c-121">\<startup> Element</span></span>](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md)
