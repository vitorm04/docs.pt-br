---
title: Método ITypeName::GetTypeArguments
ms.date: 03/30/2017
api_name:
- ITypeName.GetTypeArguments
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- GetTypeArguments
helpviewer_keywords:
- ITypeName::GetTypeArguments method [.NET Framework hosting]
- GetTypeArguments method [.NET Framework hosting]
ms.assetid: 638d77df-ff9c-40d9-88ee-930f5f87ada1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e4cd4fa8f4ba2bea5a2a853544eae6239bfaaeba
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59132269"
---
# <a name="itypenamegettypearguments-method"></a><span data-ttu-id="83d70-102">Método ITypeName::GetTypeArguments</span><span class="sxs-lookup"><span data-stu-id="83d70-102">ITypeName::GetTypeArguments Method</span></span>
<span data-ttu-id="83d70-103">Esse método oferece suporte a infraestrutura do .NET Framework e não se destina a ser usado diretamente do seu código.</span><span class="sxs-lookup"><span data-stu-id="83d70-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83d70-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="83d70-104">Syntax</span></span>  
  
```  
HRESULT GetTypeArguments (  
    [in] DWORD           count,  
    [out] ITypeName**    rgpArguments,  
    [out, retval] DWORD* pCount  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="83d70-105">Requisitos</span><span class="sxs-lookup"><span data-stu-id="83d70-105">Requirements</span></span>  
 <span data-ttu-id="83d70-106">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="83d70-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="83d70-107">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="83d70-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="83d70-108">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="83d70-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="83d70-109">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="83d70-109">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="83d70-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="83d70-110">See also</span></span>

- [<span data-ttu-id="83d70-111">Interfaces de hospedagem</span><span class="sxs-lookup"><span data-stu-id="83d70-111">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
