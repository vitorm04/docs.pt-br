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
ms.openlocfilehash: 15804673733ffba7e65c3d280cdc87a76739aaed
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67748995"
---
# <a name="itypenamegetmodifiers-method"></a><span data-ttu-id="5069f-102">Método ITypeName::GetModifiers</span><span class="sxs-lookup"><span data-stu-id="5069f-102">ITypeName::GetModifiers Method</span></span>
<span data-ttu-id="5069f-103">Esse método oferece suporte a infraestrutura do .NET Framework e não se destina a ser usado diretamente do seu código.</span><span class="sxs-lookup"><span data-stu-id="5069f-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5069f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5069f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetModifiers (  
    [in] DWORD           count,  
    [out] DWORD*         rgModifiers,  
    [out, retval] DWORD* pCount  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="5069f-105">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5069f-105">Requirements</span></span>  
 <span data-ttu-id="5069f-106">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5069f-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5069f-107">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="5069f-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5069f-108">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="5069f-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5069f-109">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5069f-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5069f-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5069f-110">See also</span></span>

- [<span data-ttu-id="5069f-111">Hospedagem de Interfaces</span><span class="sxs-lookup"><span data-stu-id="5069f-111">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
