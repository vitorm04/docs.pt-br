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
ms.openlocfilehash: 291246169a5cc2c95b117bc55bc269791885b2ea
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67749108"
---
# <a name="imanagedobjectgetobjectidentity-method"></a><span data-ttu-id="8f775-102">Método IManagedObject::GetObjectIdentity</span><span class="sxs-lookup"><span data-stu-id="8f775-102">IManagedObject::GetObjectIdentity Method</span></span>
<span data-ttu-id="8f775-103">Obtém a identidade do objeto gerenciado.</span><span class="sxs-lookup"><span data-stu-id="8f775-103">Gets the identity of this managed object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8f775-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8f775-104">Syntax</span></span>  
  
```cpp  
HRESULT GetObjectIdentity (  
    [out] BSTR*   pBSTRGUID,  
    [out] int*    AppDomainID,  
    [out] CCW_PTR pCCW  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8f775-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8f775-105">Parameters</span></span>  
 `pBSTRGUID`  
 <span data-ttu-id="8f775-106">[out] Um ponteiro para o GUID do processo no qual o objeto reside.</span><span class="sxs-lookup"><span data-stu-id="8f775-106">[out] A pointer to the GUID of the process in which the object resides.</span></span>  
  
 `AppDomainID`  
 <span data-ttu-id="8f775-107">[out] Um ponteiro para a ID do objeto domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8f775-107">[out] A pointer to the ID of the object's application domain.</span></span>  
  
 `pCCW`  
 <span data-ttu-id="8f775-108">[out] Um ponteiro para o índice do objeto no COM clássico tabela v.</span><span class="sxs-lookup"><span data-stu-id="8f775-108">[out] A pointer to object's index in the COM classic v-table.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8f775-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="8f775-109">Remarks</span></span>  
 <span data-ttu-id="8f775-110">A identidade de um objeto gerenciado inclui o GUID do processo, ID de domínio do aplicativo e o índice do objeto no COM clássica tabela v.</span><span class="sxs-lookup"><span data-stu-id="8f775-110">The identity of a managed object includes process GUID, application domain ID, and the object's index in the COM classic v-table.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8f775-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8f775-111">Requirements</span></span>  
 <span data-ttu-id="8f775-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8f775-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8f775-113">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="8f775-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8f775-114">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="8f775-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8f775-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8f775-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f775-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8f775-116">See also</span></span>

- [<span data-ttu-id="8f775-117">Interface IManagedObject</span><span class="sxs-lookup"><span data-stu-id="8f775-117">IManagedObject Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md)
