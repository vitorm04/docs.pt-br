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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61905418"
---
# <a name="ihostfiltermarktoken-method"></a><span data-ttu-id="ebd8f-102">Método IHostFilter::MarkToken</span><span class="sxs-lookup"><span data-stu-id="ebd8f-102">IHostFilter::MarkToken Method</span></span>
<span data-ttu-id="ebd8f-103">Indica que o token de metadados especificado será processado.</span><span class="sxs-lookup"><span data-stu-id="ebd8f-103">Indicates that the specified metadata token will be processed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ebd8f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ebd8f-104">Syntax</span></span>  
  
```  
HRESULT MarkToken (  
    [in]  mdToken         tk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ebd8f-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ebd8f-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="ebd8f-106">[in] O token de metadados a serem processados.</span><span class="sxs-lookup"><span data-stu-id="ebd8f-106">[in] The metadata token to be processed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ebd8f-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="ebd8f-107">Remarks</span></span>  
 <span data-ttu-id="ebd8f-108">Geralmente, você deseja que um token a ser processada se ele está no escopo de metadados.</span><span class="sxs-lookup"><span data-stu-id="ebd8f-108">Typically, you want a token to be processed if it is in the metadata scope.</span></span> <span data-ttu-id="ebd8f-109">O `MarkToken` método é passado para o mecanismo de metadados por meio de [imetadataemit:: Sethandler](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-sethandler-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="ebd8f-109">The `MarkToken` method is passed to the metadata engine via the [IMetaDataEmit::SetHandler](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-sethandler-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ebd8f-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ebd8f-110">Requirements</span></span>  
 <span data-ttu-id="ebd8f-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ebd8f-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ebd8f-112">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="ebd8f-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ebd8f-113">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="ebd8f-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ebd8f-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ebd8f-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ebd8f-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ebd8f-115">See also</span></span>

- [<span data-ttu-id="ebd8f-116">Interfaces de metadados</span><span class="sxs-lookup"><span data-stu-id="ebd8f-116">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [<span data-ttu-id="ebd8f-117">Interface IHostFilter</span><span class="sxs-lookup"><span data-stu-id="ebd8f-117">IHostFilter Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/ihostfilter-interface.md)
