---
title: Método ITypeName::GetAssemblyName
ms.date: 03/30/2017
api_name:
- ITypeName.GetAssemblyName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- GetAssemblyName
helpviewer_keywords:
- ITypeName::GetAssemblyName method [.NET Framework hosting]
- GetAssemblyName method [.NET Framework hosting]
ms.assetid: 97801d99-f5f1-4a30-882f-959827093fac
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 81b93675870d73902cf986a64d34d7c270e02203
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67780550"
---
# <a name="itypenamegetassemblyname-method"></a><span data-ttu-id="26f24-102">Método ITypeName::GetAssemblyName</span><span class="sxs-lookup"><span data-stu-id="26f24-102">ITypeName::GetAssemblyName Method</span></span>
<span data-ttu-id="26f24-103">Esse método oferece suporte a infraestrutura do .NET Framework e não se destina a ser usado diretamente do seu código.</span><span class="sxs-lookup"><span data-stu-id="26f24-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26f24-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="26f24-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAssemblyName (  
    [out, retval] BSTR* rgbszAssemblyNames  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="26f24-105">Requisitos</span><span class="sxs-lookup"><span data-stu-id="26f24-105">Requirements</span></span>  
 <span data-ttu-id="26f24-106">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="26f24-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="26f24-107">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="26f24-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="26f24-108">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="26f24-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="26f24-109">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="26f24-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26f24-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="26f24-110">See also</span></span>

- [<span data-ttu-id="26f24-111">Hospedagem de Interfaces</span><span class="sxs-lookup"><span data-stu-id="26f24-111">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
