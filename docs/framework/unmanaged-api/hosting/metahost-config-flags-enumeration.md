---
title: "Enumeração METAHOST_CONFIG_FLAGS"
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5743356cdb2a99c4c5eb0c958bc5ca0815146d4d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="metahostconfigflags-enumeration"></a><span data-ttu-id="d4fb1-102">Enumeração METAHOST_CONFIG_FLAGS</span><span class="sxs-lookup"><span data-stu-id="d4fb1-102">METAHOST_CONFIG_FLAGS Enumeration</span></span>
<span data-ttu-id="d4fb1-103">Descreve os possíveis sinalizadores retornados no `pdwConfigFlags` parâmetro do [Iclrmetahostpolicy](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) método, que indica a presença e a configuração do `useLegacyV2RuntimeActivationPolicy` atributo no [ \<inicialização > elemento](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) do arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="d4fb1-103">Describes the possible flags returned in the `pdwConfigFlags` parameter of the [ICLRMetaHostPolicy::GetRequestedRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) method, indicating the presence and setting of the `useLegacyV2RuntimeActivationPolicy` attribute in the [\<startup> element](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) of the configuration file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4fb1-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d4fb1-104">Syntax</span></span>  
  
```  
typedef enum {  
    METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_UNSET  = 0x00,  
    METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_TRUE   = 0x01,  
    METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_FALSE  = 0x02,  
    METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_MASK   = 0x03  
} METAHOST_CONFIG_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="d4fb1-105">Membros</span><span class="sxs-lookup"><span data-stu-id="d4fb1-105">Members</span></span>  
  
|<span data-ttu-id="d4fb1-106">Membro</span><span class="sxs-lookup"><span data-stu-id="d4fb1-106">Member</span></span>|<span data-ttu-id="d4fb1-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="d4fb1-107">Description</span></span>|  
|------------|-----------------|  
|`METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_UNSET`|<span data-ttu-id="d4fb1-108">O `useLegacyV2RuntimeActivationPolicy` atributo não estava presente no [ \<inicialização > elemento](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md).</span><span class="sxs-lookup"><span data-stu-id="d4fb1-108">The `useLegacyV2RuntimeActivationPolicy` attribute was not present in the [\<startup> Element](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md).</span></span>|  
|`METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_TRUE`|<span data-ttu-id="d4fb1-109">O `useLegacyV2RuntimeActivationPolicy` atributo estava presente e definida para `true`.</span><span class="sxs-lookup"><span data-stu-id="d4fb1-109">The `useLegacyV2RuntimeActivationPolicy` attribute was present and set to `true`.</span></span>|  
|`METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_FALSE`|<span data-ttu-id="d4fb1-110">O `useLegacyV2RuntimeActivationPolicy` atributo estava presente e definida para `false`.</span><span class="sxs-lookup"><span data-stu-id="d4fb1-110">The `useLegacyV2RuntimeActivationPolicy` attribute was present and set to `false`.</span></span>|  
|`METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_MASK`|<span data-ttu-id="d4fb1-111">Aplicar essa máscara para o valor retornado em `pdwConfigFlags` para obter os valores relevantes para `useLegacyV2RuntimeActivationPolicy`.</span><span class="sxs-lookup"><span data-stu-id="d4fb1-111">Apply this mask to the value returned in `pdwConfigFlags` to get the values relevant to `useLegacyV2RuntimeActivationPolicy`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d4fb1-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="d4fb1-112">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d4fb1-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d4fb1-113">Requirements</span></span>  
 <span data-ttu-id="d4fb1-114">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d4fb1-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d4fb1-115">**Cabeçalho:** Metahost.h</span><span class="sxs-lookup"><span data-stu-id="d4fb1-115">**Header:** Metahost.h</span></span>  
  
 <span data-ttu-id="d4fb1-116">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="d4fb1-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d4fb1-117">**Versões do .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d4fb1-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4fb1-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d4fb1-118">See Also</span></span>  
 [<span data-ttu-id="d4fb1-119">Enumerações de hospedagem</span><span class="sxs-lookup"><span data-stu-id="d4fb1-119">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)  
 [<span data-ttu-id="d4fb1-120">Método GetRequestedRuntime</span><span class="sxs-lookup"><span data-stu-id="d4fb1-120">GetRequestedRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md)  
 [<span data-ttu-id="d4fb1-121">\<inicialização > elemento</span><span class="sxs-lookup"><span data-stu-id="d4fb1-121">\<startup> Element</span></span>](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md)
