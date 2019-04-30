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
ms.openlocfilehash: 6d014d2900ea790f84331ed933143513ae9e63f7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61943501"
---
# <a name="imanagedobjectgetobjectidentity-method"></a><span data-ttu-id="e4976-102">Método IManagedObject::GetObjectIdentity</span><span class="sxs-lookup"><span data-stu-id="e4976-102">IManagedObject::GetObjectIdentity Method</span></span>
<span data-ttu-id="e4976-103">Obtém a identidade do objeto gerenciado.</span><span class="sxs-lookup"><span data-stu-id="e4976-103">Gets the identity of this managed object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4976-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e4976-104">Syntax</span></span>  
  
```  
HRESULT GetObjectIdentity (  
    [out] BSTR*   pBSTRGUID,  
    [out] int*    AppDomainID,  
    [out] CCW_PTR pCCW  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e4976-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e4976-105">Parameters</span></span>  
 `pBSTRGUID`  
 <span data-ttu-id="e4976-106">[out] Um ponteiro para o GUID do processo no qual o objeto reside.</span><span class="sxs-lookup"><span data-stu-id="e4976-106">[out] A pointer to the GUID of the process in which the object resides.</span></span>  
  
 `AppDomainID`  
 <span data-ttu-id="e4976-107">[out] Um ponteiro para a ID do objeto domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e4976-107">[out] A pointer to the ID of the object's application domain.</span></span>  
  
 `pCCW`  
 <span data-ttu-id="e4976-108">[out] Um ponteiro para o índice do objeto no COM clássico tabela v.</span><span class="sxs-lookup"><span data-stu-id="e4976-108">[out] A pointer to object's index in the COM classic v-table.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e4976-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="e4976-109">Remarks</span></span>  
 <span data-ttu-id="e4976-110">A identidade de um objeto gerenciado inclui o GUID do processo, ID de domínio do aplicativo e o índice do objeto no COM clássica tabela v.</span><span class="sxs-lookup"><span data-stu-id="e4976-110">The identity of a managed object includes process GUID, application domain ID, and the object's index in the COM classic v-table.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e4976-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e4976-111">Requirements</span></span>  
 <span data-ttu-id="e4976-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e4976-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e4976-113">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e4976-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e4976-114">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="e4976-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e4976-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e4976-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4976-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e4976-116">See also</span></span>

- [<span data-ttu-id="e4976-117">Interface IManagedObject</span><span class="sxs-lookup"><span data-stu-id="e4976-117">IManagedObject Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md)
