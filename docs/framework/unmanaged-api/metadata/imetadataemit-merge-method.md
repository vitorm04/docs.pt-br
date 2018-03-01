---
title: "Método IMetaDataEmit::Merge"
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f05f2e39365b021e902b2bdaa41cda481b5af8b6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemitmerge-method"></a><span data-ttu-id="9a4cc-102">Método IMetaDataEmit::Merge</span><span class="sxs-lookup"><span data-stu-id="9a4cc-102">IMetaDataEmit::Merge Method</span></span>
<span data-ttu-id="9a4cc-103">Adiciona o escopo importado especificado à lista de escopos a serem mesclados.</span><span class="sxs-lookup"><span data-stu-id="9a4cc-103">Adds the specified imported scope to the list of scopes to be merged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a4cc-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9a4cc-104">Syntax</span></span>  
  
```  
HRESULT Merge (   
    [in]  IMetaDataImport  *pImport,   
    [in]  IMapToken        *pHostMapToken,   
    [in]  IUnknown         *pHandler   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9a4cc-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="9a4cc-105">Parameters</span></span>  
 `pImport`  
 <span data-ttu-id="9a4cc-106">[in] Um ponteiro para um [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) objeto que identifica o escopo importado a serem mesclados.</span><span class="sxs-lookup"><span data-stu-id="9a4cc-106">[in] A pointer to an [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) object that identifies the imported scope to be merged.</span></span>  
  
 `pIMap`  
 <span data-ttu-id="9a4cc-107">[in] Um ponteiro para um [IMapToken](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md) objeto que especifica o token remapear.</span><span class="sxs-lookup"><span data-stu-id="9a4cc-107">[in] A pointer to an [IMapToken](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md) object that specifies the token re-map.</span></span>  
  
 `pHandleer`  
 <span data-ttu-id="9a4cc-108">[in] Um ponteiro para um <!--<<!--zzxref:IUnknown --> `IUnknown` >-->  `IUnknown` objeto que especifica os erros.</span><span class="sxs-lookup"><span data-stu-id="9a4cc-108">[in] A pointer to an <!--<<!--zzxref:IUnknown --> `IUnknown`>--> `IUnknown` object that specifies the errors.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9a4cc-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="9a4cc-109">Remarks</span></span>  
 <span data-ttu-id="9a4cc-110">Chamar [: Mergeend](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-mergeend-method.md) para disparar a fusão de metadados em um único escopo.</span><span class="sxs-lookup"><span data-stu-id="9a4cc-110">Call [IMetaDataEmit::MergeEnd](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-mergeend-method.md) to trigger the merger of metadata into a single scope.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9a4cc-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9a4cc-111">Requirements</span></span>  
 <span data-ttu-id="9a4cc-112">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9a4cc-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9a4cc-113">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="9a4cc-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9a4cc-114">**Biblioteca:** usado como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="9a4cc-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9a4cc-115">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9a4cc-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a4cc-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9a4cc-116">See Also</span></span>  
 [<span data-ttu-id="9a4cc-117">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="9a4cc-117">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="9a4cc-118">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="9a4cc-118">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
