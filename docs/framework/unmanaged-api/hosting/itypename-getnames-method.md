---
title: Método ITypeName::GetNames
ms.date: 03/30/2017
api_name:
- ITypeName.GetNames
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- GetNames
helpviewer_keywords:
- ITypeName::GetNames method [.NET Framework hosting]
- GetNames method [.NET Framework hosting]
ms.assetid: e2a3637b-d1e9-4d93-9e9b-0555fbff793d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c6dc2897eb5fe5f4df116dda8be9d4fccab9722e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54623723"
---
# <a name="itypenamegetnames-method"></a><span data-ttu-id="f33bb-102">Método ITypeName::GetNames</span><span class="sxs-lookup"><span data-stu-id="f33bb-102">ITypeName::GetNames Method</span></span>
<span data-ttu-id="f33bb-103">Esse método oferece suporte a infraestrutura do .NET Framework e não se destina a ser usado diretamente do seu código.</span><span class="sxs-lookup"><span data-stu-id="f33bb-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f33bb-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f33bb-104">Syntax</span></span>  
  
```  
HRESULT GetNames (  
    [in] DWORD           count,  
    [out] BSTR*          rgbszNames,  
    [out, retval] DWORD* pCount  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="f33bb-105">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f33bb-105">Requirements</span></span>  
 <span data-ttu-id="f33bb-106">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f33bb-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f33bb-107">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f33bb-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f33bb-108">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="f33bb-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f33bb-109">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f33bb-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f33bb-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f33bb-110">See also</span></span>
- [<span data-ttu-id="f33bb-111">Hospedagem de Interfaces</span><span class="sxs-lookup"><span data-stu-id="f33bb-111">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
