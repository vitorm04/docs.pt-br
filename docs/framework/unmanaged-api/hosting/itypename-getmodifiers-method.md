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
ms.openlocfilehash: 78d86aff385bbff479c57d8902fbd0973a6ad1bc
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59226411"
---
# <a name="itypenamegetmodifiers-method"></a><span data-ttu-id="2cae0-102">Método ITypeName::GetModifiers</span><span class="sxs-lookup"><span data-stu-id="2cae0-102">ITypeName::GetModifiers Method</span></span>
<span data-ttu-id="2cae0-103">Esse método oferece suporte a infraestrutura do .NET Framework e não se destina a ser usado diretamente do seu código.</span><span class="sxs-lookup"><span data-stu-id="2cae0-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2cae0-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2cae0-104">Syntax</span></span>  
  
```  
HRESULT GetModifiers (  
    [in] DWORD           count,  
    [out] DWORD*         rgModifiers,  
    [out, retval] DWORD* pCount  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="2cae0-105">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2cae0-105">Requirements</span></span>  
 <span data-ttu-id="2cae0-106">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2cae0-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2cae0-107">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="2cae0-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2cae0-108">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="2cae0-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="2cae0-109">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="2cae0-109">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="2cae0-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2cae0-110">See also</span></span>

- [<span data-ttu-id="2cae0-111">Interfaces de hospedagem</span><span class="sxs-lookup"><span data-stu-id="2cae0-111">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
