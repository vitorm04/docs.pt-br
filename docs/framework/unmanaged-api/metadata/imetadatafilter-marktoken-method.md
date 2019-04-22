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
ms.openlocfilehash: 6fdd50f0de014aa68b14303e9e22924b0790fa55
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59085110"
---
# <a name="imetadatafiltermarktoken-method"></a><span data-ttu-id="30ddb-102">Método IMetaDataFilter::MarkToken</span><span class="sxs-lookup"><span data-stu-id="30ddb-102">IMetaDataFilter::MarkToken Method</span></span>
<span data-ttu-id="30ddb-103">Define um valor que indica que o token de metadados especificado foi processado.</span><span class="sxs-lookup"><span data-stu-id="30ddb-103">Sets a value indicating that the specified metadata token has been processed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30ddb-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="30ddb-104">Syntax</span></span>  
  
```  
HRESULT MarkToken (  
    [in] mdToken   tk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="30ddb-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="30ddb-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="30ddb-106">[in] O token para marcar como processado.</span><span class="sxs-lookup"><span data-stu-id="30ddb-106">[in] The token to mark as processed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="30ddb-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="30ddb-107">Requirements</span></span>  
 <span data-ttu-id="30ddb-108">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="30ddb-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="30ddb-109">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="30ddb-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="30ddb-110">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="30ddb-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="30ddb-111">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="30ddb-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30ddb-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="30ddb-112">See also</span></span>

- [<span data-ttu-id="30ddb-113">Interface IMetaDataFilter</span><span class="sxs-lookup"><span data-stu-id="30ddb-113">IMetaDataFilter Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-interface.md)
