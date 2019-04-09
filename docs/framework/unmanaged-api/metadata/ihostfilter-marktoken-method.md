---
title: Método IHostFilter::MarkToken
ms.date: 03/30/2017
api_name:
- IHostFilter.MarkToken
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostFilter::MarkToken
helpviewer_keywords:
- MarkToken method, IHostFilter interface [.NET Framework metadata]
- IHostFilter::MarkToken method [.NET Framework metadata]
ms.assetid: d7061343-d0a3-4fd5-b312-61974f98bd62
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f3214a21dda27fda01054e96400997b15d11f71b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59194429"
---
# <a name="ihostfiltermarktoken-method"></a><span data-ttu-id="19c03-102">Método IHostFilter::MarkToken</span><span class="sxs-lookup"><span data-stu-id="19c03-102">IHostFilter::MarkToken Method</span></span>
<span data-ttu-id="19c03-103">Indica que o token de metadados especificado será processado.</span><span class="sxs-lookup"><span data-stu-id="19c03-103">Indicates that the specified metadata token will be processed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="19c03-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="19c03-104">Syntax</span></span>  
  
```  
HRESULT MarkToken (  
    [in]  mdToken         tk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="19c03-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="19c03-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="19c03-106">[in] O token de metadados a serem processados.</span><span class="sxs-lookup"><span data-stu-id="19c03-106">[in] The metadata token to be processed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="19c03-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="19c03-107">Remarks</span></span>  
 <span data-ttu-id="19c03-108">Geralmente, você deseja que um token a ser processada se ele está no escopo de metadados.</span><span class="sxs-lookup"><span data-stu-id="19c03-108">Typically, you want a token to be processed if it is in the metadata scope.</span></span> <span data-ttu-id="19c03-109">O `MarkToken` método é passado para o mecanismo de metadados por meio de [imetadataemit:: Sethandler](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-sethandler-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="19c03-109">The `MarkToken` method is passed to the metadata engine via the [IMetaDataEmit::SetHandler](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-sethandler-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="19c03-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="19c03-110">Requirements</span></span>  
 <span data-ttu-id="19c03-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="19c03-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="19c03-112">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="19c03-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="19c03-113">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="19c03-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="19c03-114">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="19c03-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="19c03-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="19c03-115">See also</span></span>

- [<span data-ttu-id="19c03-116">Interfaces de metadados</span><span class="sxs-lookup"><span data-stu-id="19c03-116">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [<span data-ttu-id="19c03-117">Interface IHostFilter</span><span class="sxs-lookup"><span data-stu-id="19c03-117">IHostFilter Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/ihostfilter-interface.md)
