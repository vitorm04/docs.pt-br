---
title: Método IMetaDataEmit::Merge
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.Merge
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::Merge
helpviewer_keywords:
- IMetaDataEmit::Merge method [.NET Framework metadata]
- Merge method [.NET Framework metadata]
ms.assetid: 7596220c-f699-4b6c-8ae7-c83220610650
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3fee3c0b82bec102d8e292a76d3df5a14d40ace8
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67757675"
---
# <a name="imetadataemitmerge-method"></a><span data-ttu-id="351e6-102">Método IMetaDataEmit::Merge</span><span class="sxs-lookup"><span data-stu-id="351e6-102">IMetaDataEmit::Merge Method</span></span>
<span data-ttu-id="351e6-103">Adiciona o escopo importado especificado à lista de escopos a serem mesclados.</span><span class="sxs-lookup"><span data-stu-id="351e6-103">Adds the specified imported scope to the list of scopes to be merged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="351e6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="351e6-104">Syntax</span></span>  
  
```cpp  
HRESULT Merge (   
    [in]  IMetaDataImport  *pImport,   
    [in]  IMapToken        *pHostMapToken,   
    [in]  IUnknown         *pHandler   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="351e6-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="351e6-105">Parameters</span></span>  
 `pImport`  
 <span data-ttu-id="351e6-106">[in] Um ponteiro para um [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) objeto que identifica o escopo importado a serem mesclados.</span><span class="sxs-lookup"><span data-stu-id="351e6-106">[in] A pointer to an [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) object that identifies the imported scope to be merged.</span></span>  
  
 `pIMap`  
 <span data-ttu-id="351e6-107">[in] Um ponteiro para um [IMapToken](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md) objeto que especifica o token remapear.</span><span class="sxs-lookup"><span data-stu-id="351e6-107">[in] A pointer to an [IMapToken](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md) object that specifies the token re-map.</span></span>  
  
 `pHandler`  
 <span data-ttu-id="351e6-108">[in] Um ponteiro para um [IUnknown](/cpp/atl/iunknown) objeto que especifica os erros.</span><span class="sxs-lookup"><span data-stu-id="351e6-108">[in] A pointer to an [IUnknown](/cpp/atl/iunknown) object that specifies the errors.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="351e6-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="351e6-109">Remarks</span></span>  
 <span data-ttu-id="351e6-110">Chame [imetadataemit:: Mergeend](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-mergeend-method.md) para disparar a fusão de metadados em um único escopo.</span><span class="sxs-lookup"><span data-stu-id="351e6-110">Call [IMetaDataEmit::MergeEnd](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-mergeend-method.md) to trigger the merger of metadata into a single scope.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="351e6-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="351e6-111">Requirements</span></span>  
 <span data-ttu-id="351e6-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="351e6-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="351e6-113">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="351e6-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="351e6-114">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="351e6-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="351e6-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="351e6-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="351e6-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="351e6-116">See also</span></span>

- [<span data-ttu-id="351e6-117">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="351e6-117">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="351e6-118">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="351e6-118">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
