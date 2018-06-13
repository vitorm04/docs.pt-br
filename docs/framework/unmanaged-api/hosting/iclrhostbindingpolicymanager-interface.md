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
ms.openlocfilehash: 637803c509935fdff080802f66f9f73ab8cf25e0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33431982"
---
# <a name="iclrhostbindingpolicymanager-interface"></a><span data-ttu-id="c32af-102">Interface ICLRHostBindingPolicyManager</span><span class="sxs-lookup"><span data-stu-id="c32af-102">ICLRHostBindingPolicyManager Interface</span></span>
<span data-ttu-id="c32af-103">Fornece métodos para o host avaliar a política atual de associação e se comunicar alterações de política para um assembly específico.</span><span class="sxs-lookup"><span data-stu-id="c32af-103">Provides methods for the host to evaluate current binding policy and communicate policy changes for a specified assembly.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c32af-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="c32af-104">Methods</span></span>  
  
|<span data-ttu-id="c32af-105">Método</span><span class="sxs-lookup"><span data-stu-id="c32af-105">Method</span></span>|<span data-ttu-id="c32af-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="c32af-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c32af-107">Método EvaluatePolicy</span><span class="sxs-lookup"><span data-stu-id="c32af-107">EvaluatePolicy Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-evaluatepolicy-method.md)|<span data-ttu-id="c32af-108">Avalia a política de associação em nome de host.</span><span class="sxs-lookup"><span data-stu-id="c32af-108">Evaluates binding policy on behalf of the host.</span></span>|  
|[<span data-ttu-id="c32af-109">Método ModifyApplicationPolicy</span><span class="sxs-lookup"><span data-stu-id="c32af-109">ModifyApplicationPolicy Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-modifyapplicationpolicy-method.md)|<span data-ttu-id="c32af-110">Modifica a política de associação para o assembly especificado e cria uma nova versão da política.</span><span class="sxs-lookup"><span data-stu-id="c32af-110">Modifies the binding policy for the specified assembly, and creates a new version of the policy.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c32af-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c32af-111">Requirements</span></span>  
 <span data-ttu-id="c32af-112">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c32af-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c32af-113">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c32af-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c32af-114">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="c32af-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c32af-115">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c32af-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c32af-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c32af-116">See Also</span></span>  
 [<span data-ttu-id="c32af-117">Interface ICLRAssemblyIdentityManager</span><span class="sxs-lookup"><span data-stu-id="c32af-117">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 [<span data-ttu-id="c32af-118">Interface IHostAssemblyStore</span><span class="sxs-lookup"><span data-stu-id="c32af-118">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)  
 [<span data-ttu-id="c32af-119">Hospedagem de Interfaces</span><span class="sxs-lookup"><span data-stu-id="c32af-119">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
