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
ms.openlocfilehash: 06894f238f9fda3111d5484bb1b2add183a5abb2
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448061"
---
# <a name="imetadataemitmerge-method"></a><span data-ttu-id="217d1-102">Método IMetaDataEmit::Merge</span><span class="sxs-lookup"><span data-stu-id="217d1-102">IMetaDataEmit::Merge Method</span></span>
<span data-ttu-id="217d1-103">Adiciona o escopo importado especificado à lista de escopos a serem mesclados.</span><span class="sxs-lookup"><span data-stu-id="217d1-103">Adds the specified imported scope to the list of scopes to be merged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="217d1-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="217d1-104">Syntax</span></span>  
  
```cpp  
HRESULT Merge (   
    [in]  IMetaDataImport  *pImport,   
    [in]  IMapToken        *pHostMapToken,   
    [in]  IUnknown         *pHandler   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="217d1-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="217d1-105">Parameters</span></span>  
 `pImport`  
 <span data-ttu-id="217d1-106">no Um ponteiro para um objeto [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) que identifica o escopo importado a ser mesclado.</span><span class="sxs-lookup"><span data-stu-id="217d1-106">[in] A pointer to an [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) object that identifies the imported scope to be merged.</span></span>  
  
 `pIMap`  
 <span data-ttu-id="217d1-107">no Um ponteiro para um objeto [IMapToken](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md) que especifica o novo mapeamento do token.</span><span class="sxs-lookup"><span data-stu-id="217d1-107">[in] A pointer to an [IMapToken](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md) object that specifies the token re-map.</span></span>  
  
 `pHandler`  
 <span data-ttu-id="217d1-108">no Um ponteiro para um objeto [IUnknown](/cpp/atl/iunknown) que especifica os erros.</span><span class="sxs-lookup"><span data-stu-id="217d1-108">[in] A pointer to an [IUnknown](/cpp/atl/iunknown) object that specifies the errors.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="217d1-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="217d1-109">Remarks</span></span>  
 <span data-ttu-id="217d1-110">Chame [IMetaDataEmit:: MergeEnd](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-mergeend-method.md) para disparar a fusão de metadados em um único escopo.</span><span class="sxs-lookup"><span data-stu-id="217d1-110">Call [IMetaDataEmit::MergeEnd](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-mergeend-method.md) to trigger the merger of metadata into a single scope.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="217d1-111">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="217d1-111">Requirements</span></span>  
 <span data-ttu-id="217d1-112">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="217d1-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="217d1-113">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="217d1-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="217d1-114">**Biblioteca:** Usado como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="217d1-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="217d1-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="217d1-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="217d1-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="217d1-116">See also</span></span>

- [<span data-ttu-id="217d1-117">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="217d1-117">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="217d1-118">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="217d1-118">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
