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
ms.openlocfilehash: ac835459f88655377d96699e6aea0e877218c8fb
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125284"
---
# <a name="itypenamegettypearguments-method"></a><span data-ttu-id="23be8-102">Método ITypeName::GetTypeArguments</span><span class="sxs-lookup"><span data-stu-id="23be8-102">ITypeName::GetTypeArguments Method</span></span>
<span data-ttu-id="23be8-103">Esse método oferece suporte a infraestrutura do .NET Framework e não se destina a ser usado diretamente do seu código.</span><span class="sxs-lookup"><span data-stu-id="23be8-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="23be8-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="23be8-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeArguments (  
    [in] DWORD           count,  
    [out] ITypeName**    rgpArguments,  
    [out, retval] DWORD* pCount  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="23be8-105">Requisitos</span><span class="sxs-lookup"><span data-stu-id="23be8-105">Requirements</span></span>  
 <span data-ttu-id="23be8-106">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="23be8-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="23be8-107">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="23be8-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="23be8-108">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="23be8-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="23be8-109">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="23be8-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23be8-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="23be8-110">See also</span></span>

- [<span data-ttu-id="23be8-111">Hospedagem de Interfaces</span><span class="sxs-lookup"><span data-stu-id="23be8-111">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
