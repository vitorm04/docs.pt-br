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
ms.openlocfilehash: 8c884569a452fb2985713956f942205cda6ea1ff
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141250"
---
# <a name="imanagedobjectgetobjectidentity-method"></a><span data-ttu-id="5ce7a-102">Método IManagedObject::GetObjectIdentity</span><span class="sxs-lookup"><span data-stu-id="5ce7a-102">IManagedObject::GetObjectIdentity Method</span></span>
<span data-ttu-id="5ce7a-103">Obtém a identidade deste objeto gerenciado.</span><span class="sxs-lookup"><span data-stu-id="5ce7a-103">Gets the identity of this managed object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ce7a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5ce7a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetObjectIdentity (  
    [out] BSTR*   pBSTRGUID,  
    [out] int*    AppDomainID,  
    [out] CCW_PTR pCCW  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5ce7a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5ce7a-105">Parameters</span></span>  
 `pBSTRGUID`  
 <span data-ttu-id="5ce7a-106">fora Um ponteiro para o GUID do processo no qual o objeto reside.</span><span class="sxs-lookup"><span data-stu-id="5ce7a-106">[out] A pointer to the GUID of the process in which the object resides.</span></span>  
  
 `AppDomainID`  
 <span data-ttu-id="5ce7a-107">fora Um ponteiro para a ID do domínio do aplicativo do objeto.</span><span class="sxs-lookup"><span data-stu-id="5ce7a-107">[out] A pointer to the ID of the object's application domain.</span></span>  
  
 `pCCW`  
 <span data-ttu-id="5ce7a-108">fora Um ponteiro para o índice do objeto na tabela v clássica COM.</span><span class="sxs-lookup"><span data-stu-id="5ce7a-108">[out] A pointer to object's index in the COM classic v-table.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5ce7a-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="5ce7a-109">Remarks</span></span>  
 <span data-ttu-id="5ce7a-110">A identidade de um objeto gerenciado inclui GUID do processo, ID de domínio do aplicativo e o índice do objeto na tabela v clássica do COM.</span><span class="sxs-lookup"><span data-stu-id="5ce7a-110">The identity of a managed object includes process GUID, application domain ID, and the object's index in the COM classic v-table.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5ce7a-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5ce7a-111">Requirements</span></span>  
 <span data-ttu-id="5ce7a-112">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5ce7a-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5ce7a-113">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="5ce7a-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5ce7a-114">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="5ce7a-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5ce7a-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5ce7a-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ce7a-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5ce7a-116">See also</span></span>

- [<span data-ttu-id="5ce7a-117">Interface IManagedObject</span><span class="sxs-lookup"><span data-stu-id="5ce7a-117">IManagedObject Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md)
