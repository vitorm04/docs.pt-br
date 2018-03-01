---
title: "Método ITypeNameFactory::ParseTypeName"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ITypeNameFactory.ParseTypeName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ParseTypeName
helpviewer_keywords:
- ITypeNameFactory::ParseTypeName method [.NET Framework hosting]
- ParseTypeName method [.NET Framework hosting]
ms.assetid: 13c9f063-371c-4911-a5e7-e1e0b88ae382
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b1bb762dbf1751a32939cb1acd41e1dd2fb77ef2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="itypenamefactoryparsetypename-method"></a><span data-ttu-id="f6a5d-102">Método ITypeNameFactory::ParseTypeName</span><span class="sxs-lookup"><span data-stu-id="f6a5d-102">ITypeNameFactory::ParseTypeName Method</span></span>
<span data-ttu-id="f6a5d-103">Esse método oferece suporte a infraestrutura do .NET Framework e não se destina a ser usado diretamente do seu código.</span><span class="sxs-lookup"><span data-stu-id="f6a5d-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f6a5d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f6a5d-104">Syntax</span></span>  
  
```  
HRESULT ParseTypeName (  
    [in]  LPCWSTR             szName,  
    [out] DWORD*              pError,  
    [out, retval] ITypeName** ppTypeName  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="f6a5d-105">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f6a5d-105">Requirements</span></span>  
 <span data-ttu-id="f6a5d-106">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f6a5d-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f6a5d-107">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f6a5d-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f6a5d-108">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="f6a5d-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f6a5d-109">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f6a5d-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6a5d-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f6a5d-110">See Also</span></span>  
 [<span data-ttu-id="f6a5d-111">Hospedagem de Interfaces</span><span class="sxs-lookup"><span data-stu-id="f6a5d-111">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
