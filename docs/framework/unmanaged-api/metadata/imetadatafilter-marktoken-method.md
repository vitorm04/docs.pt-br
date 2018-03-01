---
title: "Método IMetaDataFilter::MarkToken"
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
- IMetaDataFilter.MarkToken
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataFilter::MarkToken
helpviewer_keywords:
- IMetaDataFilter::MarkToken method [.NET Framework metadata]
- MarkToken method, IMetaDataFilter interface [.NET Framework metadata]
ms.assetid: bd492834-6529-4d39-b93d-f8cdbd3e297f
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: fb40d7674caae119b39f49b0c1024c7500bc892a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadatafiltermarktoken-method"></a><span data-ttu-id="2bd7e-102">Método IMetaDataFilter::MarkToken</span><span class="sxs-lookup"><span data-stu-id="2bd7e-102">IMetaDataFilter::MarkToken Method</span></span>
<span data-ttu-id="2bd7e-103">Define um valor que indica se o token de metadados especificado foi processado.</span><span class="sxs-lookup"><span data-stu-id="2bd7e-103">Sets a value indicating that the specified metadata token has been processed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2bd7e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2bd7e-104">Syntax</span></span>  
  
```  
HRESULT MarkToken (  
    [in] mdToken   tk  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2bd7e-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2bd7e-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="2bd7e-106">[in] O token marcar como processado.</span><span class="sxs-lookup"><span data-stu-id="2bd7e-106">[in] The token to mark as processed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2bd7e-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2bd7e-107">Requirements</span></span>  
 <span data-ttu-id="2bd7e-108">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2bd7e-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2bd7e-109">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="2bd7e-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2bd7e-110">**Biblioteca:** usado como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="2bd7e-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2bd7e-111">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2bd7e-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2bd7e-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2bd7e-112">See Also</span></span>  
 [<span data-ttu-id="2bd7e-113">Interface IMetaDataFilter</span><span class="sxs-lookup"><span data-stu-id="2bd7e-113">IMetaDataFilter Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-interface.md)
