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
ms.openlocfilehash: 6b37fcfc04e3ec880c67f102ec12d7f3e4b06a43
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84493156"
---
# <a name="metahost_config_flags-enumeration"></a><span data-ttu-id="ed8d9-102">Enumeração METAHOST_CONFIG_FLAGS</span><span class="sxs-lookup"><span data-stu-id="ed8d9-102">METAHOST_CONFIG_FLAGS Enumeration</span></span>
<span data-ttu-id="ed8d9-103">Descreve os possíveis sinalizadores retornados no `pdwConfigFlags` parâmetro do método [ICLRMetaHostPolicy:: GetRequestedRuntime](iclrmetahostpolicy-getrequestedruntime-method.md) , indicando a presença e a configuração do `useLegacyV2RuntimeActivationPolicy` atributo no [ \<startup> elemento](../../configure-apps/file-schema/startup/startup-element.md) do arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="ed8d9-103">Describes the possible flags returned in the `pdwConfigFlags` parameter of the [ICLRMetaHostPolicy::GetRequestedRuntime](iclrmetahostpolicy-getrequestedruntime-method.md) method, indicating the presence and setting of the `useLegacyV2RuntimeActivationPolicy` attribute in the [\<startup> element](../../configure-apps/file-schema/startup/startup-element.md) of the configuration file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ed8d9-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ed8d9-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_UNSET  = 0x00,  
    METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_TRUE   = 0x01,  
    METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_FALSE  = 0x02,  
    METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_MASK   = 0x03  
} METAHOST_CONFIG_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="ed8d9-105">Membros</span><span class="sxs-lookup"><span data-stu-id="ed8d9-105">Members</span></span>  
  
|<span data-ttu-id="ed8d9-106">Membro</span><span class="sxs-lookup"><span data-stu-id="ed8d9-106">Member</span></span>|<span data-ttu-id="ed8d9-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="ed8d9-107">Description</span></span>|  
|------------|-----------------|  
|`METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_UNSET`|<span data-ttu-id="ed8d9-108">O `useLegacyV2RuntimeActivationPolicy` atributo não estava presente no [ \<startup> elemento](../../configure-apps/file-schema/startup/startup-element.md).</span><span class="sxs-lookup"><span data-stu-id="ed8d9-108">The `useLegacyV2RuntimeActivationPolicy` attribute was not present in the [\<startup> Element](../../configure-apps/file-schema/startup/startup-element.md).</span></span>|  
|`METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_TRUE`|<span data-ttu-id="ed8d9-109">O `useLegacyV2RuntimeActivationPolicy` atributo estava presente e definido como `true` .</span><span class="sxs-lookup"><span data-stu-id="ed8d9-109">The `useLegacyV2RuntimeActivationPolicy` attribute was present and set to `true`.</span></span>|  
|`METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_FALSE`|<span data-ttu-id="ed8d9-110">O `useLegacyV2RuntimeActivationPolicy` atributo estava presente e definido como `false` .</span><span class="sxs-lookup"><span data-stu-id="ed8d9-110">The `useLegacyV2RuntimeActivationPolicy` attribute was present and set to `false`.</span></span>|  
|`METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_MASK`|<span data-ttu-id="ed8d9-111">Aplique essa máscara ao valor retornado em `pdwConfigFlags` para obter os valores relevantes para `useLegacyV2RuntimeActivationPolicy` .</span><span class="sxs-lookup"><span data-stu-id="ed8d9-111">Apply this mask to the value returned in `pdwConfigFlags` to get the values relevant to `useLegacyV2RuntimeActivationPolicy`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ed8d9-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="ed8d9-112">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ed8d9-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ed8d9-113">Requirements</span></span>  
 <span data-ttu-id="ed8d9-114">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ed8d9-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ed8d9-115">**Cabeçalho:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="ed8d9-115">**Header:** Metahost.h</span></span>  
  
 <span data-ttu-id="ed8d9-116">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="ed8d9-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ed8d9-117">**.NET Framework versões:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ed8d9-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed8d9-118">Confira também</span><span class="sxs-lookup"><span data-stu-id="ed8d9-118">See also</span></span>

- [<span data-ttu-id="ed8d9-119">Hospedando enumerações</span><span class="sxs-lookup"><span data-stu-id="ed8d9-119">Hosting Enumerations</span></span>](hosting-enumerations.md)
- [<span data-ttu-id="ed8d9-120">Método GetRequestedRuntime</span><span class="sxs-lookup"><span data-stu-id="ed8d9-120">GetRequestedRuntime Method</span></span>](iclrmetahostpolicy-getrequestedruntime-method.md)
- [<span data-ttu-id="ed8d9-121">\<startup>Elementos</span><span class="sxs-lookup"><span data-stu-id="ed8d9-121">\<startup> Element</span></span>](../../configure-apps/file-schema/startup/startup-element.md)
