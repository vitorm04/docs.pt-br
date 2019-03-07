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
ms.openlocfilehash: 4d825a0c67f88e1f37023feb96a217b115653056
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57496931"
---
# <a name="imanagedobjectgetobjectidentity-method"></a><span data-ttu-id="e9cd1-102">Método IManagedObject::GetObjectIdentity</span><span class="sxs-lookup"><span data-stu-id="e9cd1-102">IManagedObject::GetObjectIdentity Method</span></span>
<span data-ttu-id="e9cd1-103">Obtém a identidade do objeto gerenciado.</span><span class="sxs-lookup"><span data-stu-id="e9cd1-103">Gets the identity of this managed object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9cd1-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e9cd1-104">Syntax</span></span>  
  
```  
HRESULT GetObjectIdentity (  
    [out] BSTR*   pBSTRGUID,  
    [out] int*    AppDomainID,  
    [out] CCW_PTR pCCW  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e9cd1-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e9cd1-105">Parameters</span></span>  
 `pBSTRGUID`  
 <span data-ttu-id="e9cd1-106">[out] Um ponteiro para o GUID do processo no qual o objeto reside.</span><span class="sxs-lookup"><span data-stu-id="e9cd1-106">[out] A pointer to the GUID of the process in which the object resides.</span></span>  
  
 `AppDomainID`  
 <span data-ttu-id="e9cd1-107">[out] Um ponteiro para a ID do objeto domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e9cd1-107">[out] A pointer to the ID of the object's application domain.</span></span>  
  
 `pCCW`  
 <span data-ttu-id="e9cd1-108">[out] Um ponteiro para o índice do objeto no COM clássico tabela v.</span><span class="sxs-lookup"><span data-stu-id="e9cd1-108">[out] A pointer to object's index in the COM classic v-table.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e9cd1-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="e9cd1-109">Remarks</span></span>  
 <span data-ttu-id="e9cd1-110">A identidade de um objeto gerenciado inclui o GUID do processo, ID de domínio do aplicativo e o índice do objeto no COM clássica tabela v.</span><span class="sxs-lookup"><span data-stu-id="e9cd1-110">The identity of a managed object includes process GUID, application domain ID, and the object's index in the COM classic v-table.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e9cd1-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e9cd1-111">Requirements</span></span>  
 <span data-ttu-id="e9cd1-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e9cd1-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e9cd1-113">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e9cd1-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e9cd1-114">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="e9cd1-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e9cd1-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e9cd1-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9cd1-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e9cd1-116">See also</span></span>
- [<span data-ttu-id="e9cd1-117">Interface IManagedObject</span><span class="sxs-lookup"><span data-stu-id="e9cd1-117">IManagedObject Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md)
