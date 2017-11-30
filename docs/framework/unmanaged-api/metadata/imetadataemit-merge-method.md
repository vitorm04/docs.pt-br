---
title: "Método IMetaDataEmit::Merge"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.Merge
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::Merge
helpviewer_keywords:
- IMetaDataEmit::Merge method [.NET Framework metadata]
- Merge method [.NET Framework metadata]
ms.assetid: 7596220c-f699-4b6c-8ae7-c83220610650
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 42ebc188dfecde068ef8e2979970118fee91ec4b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemitmerge-method"></a><span data-ttu-id="14ce8-102">Método IMetaDataEmit::Merge</span><span class="sxs-lookup"><span data-stu-id="14ce8-102">IMetaDataEmit::Merge Method</span></span>
<span data-ttu-id="14ce8-103">Adiciona o escopo importado especificado à lista de escopos a serem mesclados.</span><span class="sxs-lookup"><span data-stu-id="14ce8-103">Adds the specified imported scope to the list of scopes to be merged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="14ce8-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="14ce8-104">Syntax</span></span>  
  
```  
HRESULT Merge (   
    [in]  IMetaDataImport  *pImport,   
    [in]  IMapToken        *pHostMapToken,   
    [in]  IUnknown         *pHandler   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="14ce8-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="14ce8-105">Parameters</span></span>  
 `pImport`  
 <span data-ttu-id="14ce8-106">[in] Um ponteiro para um [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) objeto que identifica o escopo importado a serem mesclados.</span><span class="sxs-lookup"><span data-stu-id="14ce8-106">[in] A pointer to an [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) object that identifies the imported scope to be merged.</span></span>  
  
 `pIMap`  
 <span data-ttu-id="14ce8-107">[in] Um ponteiro para um [IMapToken](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md) objeto que especifica o token remapear.</span><span class="sxs-lookup"><span data-stu-id="14ce8-107">[in] A pointer to an [IMapToken](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md) object that specifies the token re-map.</span></span>  
  
 `pHandleer`  
 <span data-ttu-id="14ce8-108">[in] Um ponteiro para um <!--<<!--zzxref:IUnknown --> `IUnknown` >-->  `IUnknown` objeto que especifica os erros.</span><span class="sxs-lookup"><span data-stu-id="14ce8-108">[in] A pointer to an <!--<<!--zzxref:IUnknown --> `IUnknown`>--> `IUnknown` object that specifies the errors.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="14ce8-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="14ce8-109">Remarks</span></span>  
 <span data-ttu-id="14ce8-110">Chamar [: Mergeend](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-mergeend-method.md) para disparar a fusão de metadados em um único escopo.</span><span class="sxs-lookup"><span data-stu-id="14ce8-110">Call [IMetaDataEmit::MergeEnd](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-mergeend-method.md) to trigger the merger of metadata into a single scope.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="14ce8-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="14ce8-111">Requirements</span></span>  
 <span data-ttu-id="14ce8-112">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="14ce8-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="14ce8-113">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="14ce8-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="14ce8-114">**Biblioteca:** usado como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="14ce8-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="14ce8-115">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="14ce8-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14ce8-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="14ce8-116">See Also</span></span>  
 [<span data-ttu-id="14ce8-117">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="14ce8-117">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="14ce8-118">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="14ce8-118">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
