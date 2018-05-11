---
title: Método IMetaDataFilter::MarkToken
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 97f184bae4628f2aa357644188594396468671ee
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="imetadatafiltermarktoken-method"></a><span data-ttu-id="edf17-102">Método IMetaDataFilter::MarkToken</span><span class="sxs-lookup"><span data-stu-id="edf17-102">IMetaDataFilter::MarkToken Method</span></span>
<span data-ttu-id="edf17-103">Define um valor que indica se o token de metadados especificado foi processado.</span><span class="sxs-lookup"><span data-stu-id="edf17-103">Sets a value indicating that the specified metadata token has been processed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="edf17-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="edf17-104">Syntax</span></span>  
  
```  
HRESULT MarkToken (  
    [in] mdToken   tk  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="edf17-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="edf17-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="edf17-106">[in] O token marcar como processado.</span><span class="sxs-lookup"><span data-stu-id="edf17-106">[in] The token to mark as processed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="edf17-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="edf17-107">Requirements</span></span>  
 <span data-ttu-id="edf17-108">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="edf17-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="edf17-109">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="edf17-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="edf17-110">**Biblioteca:** usado como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="edf17-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="edf17-111">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="edf17-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="edf17-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="edf17-112">See Also</span></span>  
 [<span data-ttu-id="edf17-113">Interface IMetaDataFilter</span><span class="sxs-lookup"><span data-stu-id="edf17-113">IMetaDataFilter Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-interface.md)
