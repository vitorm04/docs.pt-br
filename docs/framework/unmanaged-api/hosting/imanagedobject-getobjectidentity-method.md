---
title: Método IManagedObject::GetObjectIdentity
ms.date: 03/30/2017
api_name:
- IManagedObject.GetObjectIdentity
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- GetObjectIdentity
helpviewer_keywords:
- GetObjectIdentity method [.NET Framework hosting]
- IManagedObject::GetObjectIdentity method [.NET Framework hosting]
ms.assetid: b862ff3e-e480-4cdf-84e2-e1013334a467
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f1975e5bf20453a3bcd6761d9734be7ddd2ceef7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="imanagedobjectgetobjectidentity-method"></a><span data-ttu-id="cc53c-102">Método IManagedObject::GetObjectIdentity</span><span class="sxs-lookup"><span data-stu-id="cc53c-102">IManagedObject::GetObjectIdentity Method</span></span>
<span data-ttu-id="cc53c-103">Obtém a identidade do objeto gerenciado.</span><span class="sxs-lookup"><span data-stu-id="cc53c-103">Gets the identity of this managed object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc53c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cc53c-104">Syntax</span></span>  
  
```  
HRESULT GetObjectIdentity (  
    [out] BSTR*   pBSTRGUID,  
    [out] int*    AppDomainID,  
    [out] CCW_PTR pCCW  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cc53c-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="cc53c-105">Parameters</span></span>  
 `pBSTRGUID`  
 <span data-ttu-id="cc53c-106">[out] Um ponteiro para o GUID do processo no qual o objeto reside.</span><span class="sxs-lookup"><span data-stu-id="cc53c-106">[out] A pointer to the GUID of the process in which the object resides.</span></span>  
  
 `AppDomainID`  
 <span data-ttu-id="cc53c-107">[out] Um ponteiro para a ID de domínio de aplicativo do objeto.</span><span class="sxs-lookup"><span data-stu-id="cc53c-107">[out] A pointer to the ID of the object's application domain.</span></span>  
  
 `pCCW`  
 <span data-ttu-id="cc53c-108">[out] Um ponteiro para o índice do objeto do COM clássico tabela v.</span><span class="sxs-lookup"><span data-stu-id="cc53c-108">[out] A pointer to object's index in the COM classic v-table.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cc53c-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="cc53c-109">Remarks</span></span>  
 <span data-ttu-id="cc53c-110">A identidade de um objeto gerenciado inclui o GUID do processo, ID de domínio de aplicativo e o índice do objeto da COM clássica tabela v.</span><span class="sxs-lookup"><span data-stu-id="cc53c-110">The identity of a managed object includes process GUID, application domain ID, and the object's index in the COM classic v-table.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cc53c-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="cc53c-111">Requirements</span></span>  
 <span data-ttu-id="cc53c-112">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cc53c-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cc53c-113">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="cc53c-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="cc53c-114">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="cc53c-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cc53c-115">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cc53c-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc53c-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cc53c-116">See Also</span></span>  
 [<span data-ttu-id="cc53c-117">Interface IManagedObject</span><span class="sxs-lookup"><span data-stu-id="cc53c-117">IManagedObject Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md)
