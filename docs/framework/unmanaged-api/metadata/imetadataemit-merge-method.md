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
ms.openlocfilehash: 899f2ca5ef1b987687f5c065ad3e1965e142d103
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44080784"
---
# <a name="imetadataemitmerge-method"></a><span data-ttu-id="0c631-102">Método IMetaDataEmit::Merge</span><span class="sxs-lookup"><span data-stu-id="0c631-102">IMetaDataEmit::Merge Method</span></span>
<span data-ttu-id="0c631-103">Adiciona o escopo importado especificado à lista de escopos a serem mesclados.</span><span class="sxs-lookup"><span data-stu-id="0c631-103">Adds the specified imported scope to the list of scopes to be merged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0c631-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0c631-104">Syntax</span></span>  
  
```  
HRESULT Merge (   
    [in]  IMetaDataImport  *pImport,   
    [in]  IMapToken        *pHostMapToken,   
    [in]  IUnknown         *pHandler   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0c631-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0c631-105">Parameters</span></span>  
 `pImport`  
 <span data-ttu-id="0c631-106">[in] Um ponteiro para um [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) objeto que identifica o escopo importado a serem mesclados.</span><span class="sxs-lookup"><span data-stu-id="0c631-106">[in] A pointer to an [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) object that identifies the imported scope to be merged.</span></span>  
  
 `pIMap`  
 <span data-ttu-id="0c631-107">[in] Um ponteiro para um [IMapToken](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md) objeto que especifica o token remapear.</span><span class="sxs-lookup"><span data-stu-id="0c631-107">[in] A pointer to an [IMapToken](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md) object that specifies the token re-map.</span></span>  
  
 `pHandleer`  
 <span data-ttu-id="0c631-108">[in] Um ponteiro para um [IUnknown](/cpp/atl/iunknown) objeto que especifica os erros.</span><span class="sxs-lookup"><span data-stu-id="0c631-108">[in] A pointer to an [IUnknown](/cpp/atl/iunknown) object that specifies the errors.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0c631-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="0c631-109">Remarks</span></span>  
 <span data-ttu-id="0c631-110">Chame [imetadataemit:: Mergeend](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-mergeend-method.md) para disparar a fusão de metadados em um único escopo.</span><span class="sxs-lookup"><span data-stu-id="0c631-110">Call [IMetaDataEmit::MergeEnd](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-mergeend-method.md) to trigger the merger of metadata into a single scope.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0c631-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0c631-111">Requirements</span></span>  
 <span data-ttu-id="0c631-112">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0c631-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0c631-113">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="0c631-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0c631-114">**Biblioteca:** usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="0c631-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0c631-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0c631-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c631-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0c631-116">See Also</span></span>  
 [<span data-ttu-id="0c631-117">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="0c631-117">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="0c631-118">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="0c631-118">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
