---
title: Método ITypeName::GetModifiers
ms.date: 03/30/2017
api_name:
- ITypeName.GetModifiers
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- GetModifiers
helpviewer_keywords:
- ITypeName::GetModifiers method [.NET Framework hosting]
- GetModifiers method [.NET Framework hosting]
ms.assetid: 75508c55-3e09-4135-80da-cc811003fa82
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 66976b99b5686c62ad31c8a0365ce14f1bf33f85
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="itypenamegetmodifiers-method"></a><span data-ttu-id="50299-102">Método ITypeName::GetModifiers</span><span class="sxs-lookup"><span data-stu-id="50299-102">ITypeName::GetModifiers Method</span></span>
<span data-ttu-id="50299-103">Esse método oferece suporte a infraestrutura do .NET Framework e não se destina a ser usado diretamente do seu código.</span><span class="sxs-lookup"><span data-stu-id="50299-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="50299-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="50299-104">Syntax</span></span>  
  
```  
HRESULT GetModifiers (  
    [in] DWORD           count,  
    [out] DWORD*         rgModifiers,  
    [out, retval] DWORD* pCount  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="50299-105">Requisitos</span><span class="sxs-lookup"><span data-stu-id="50299-105">Requirements</span></span>  
 <span data-ttu-id="50299-106">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="50299-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="50299-107">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="50299-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="50299-108">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="50299-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="50299-109">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="50299-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50299-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="50299-110">See Also</span></span>  
 [<span data-ttu-id="50299-111">Hospedagem de Interfaces</span><span class="sxs-lookup"><span data-stu-id="50299-111">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
