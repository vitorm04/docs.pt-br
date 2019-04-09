---
title: Interface ICLRHostBindingPolicyManager
ms.date: 03/30/2017
api_name:
- ICLRHostBindingPolicyManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRHostBindingPolicyManager
helpviewer_keywords:
- ICLRHostBindingPolicyManager interface [.NET Framework hosting]
ms.assetid: f9da168b-366b-4b2b-bdb9-330b6bad5a6b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e494bbbd08a77329b7b64816216e4bb2e1b724a2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59074190"
---
# <a name="iclrhostbindingpolicymanager-interface"></a><span data-ttu-id="faf05-102">Interface ICLRHostBindingPolicyManager</span><span class="sxs-lookup"><span data-stu-id="faf05-102">ICLRHostBindingPolicyManager Interface</span></span>
<span data-ttu-id="faf05-103">Fornece métodos para o host avaliar a política de associação atual e se comunicar alterações de política para um assembly especificado.</span><span class="sxs-lookup"><span data-stu-id="faf05-103">Provides methods for the host to evaluate current binding policy and communicate policy changes for a specified assembly.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="faf05-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="faf05-104">Methods</span></span>  
  
|<span data-ttu-id="faf05-105">Método</span><span class="sxs-lookup"><span data-stu-id="faf05-105">Method</span></span>|<span data-ttu-id="faf05-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="faf05-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="faf05-107">Método EvaluatePolicy</span><span class="sxs-lookup"><span data-stu-id="faf05-107">EvaluatePolicy Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-evaluatepolicy-method.md)|<span data-ttu-id="faf05-108">Avalia a política de associação em nome do host.</span><span class="sxs-lookup"><span data-stu-id="faf05-108">Evaluates binding policy on behalf of the host.</span></span>|  
|[<span data-ttu-id="faf05-109">Método ModifyApplicationPolicy</span><span class="sxs-lookup"><span data-stu-id="faf05-109">ModifyApplicationPolicy Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-modifyapplicationpolicy-method.md)|<span data-ttu-id="faf05-110">Modifica a política de associação para o assembly especificado e cria uma nova versão da política.</span><span class="sxs-lookup"><span data-stu-id="faf05-110">Modifies the binding policy for the specified assembly, and creates a new version of the policy.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="faf05-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="faf05-111">Requirements</span></span>  
 <span data-ttu-id="faf05-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="faf05-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="faf05-113">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="faf05-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="faf05-114">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="faf05-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="faf05-115">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="faf05-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="faf05-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="faf05-116">See also</span></span>

- [<span data-ttu-id="faf05-117">Interface ICLRAssemblyIdentityManager</span><span class="sxs-lookup"><span data-stu-id="faf05-117">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="faf05-118">Interface IHostAssemblyStore</span><span class="sxs-lookup"><span data-stu-id="faf05-118">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
- [<span data-ttu-id="faf05-119">Interfaces de hospedagem</span><span class="sxs-lookup"><span data-stu-id="faf05-119">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
