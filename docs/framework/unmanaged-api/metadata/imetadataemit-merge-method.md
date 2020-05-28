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
ms.openlocfilehash: e7fe5cbe27c0771a71e4c03d14ab68ada7d0741a
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84004147"
---
# <a name="imetadataemitmerge-method"></a><span data-ttu-id="88dc5-102">Método IMetaDataEmit::Merge</span><span class="sxs-lookup"><span data-stu-id="88dc5-102">IMetaDataEmit::Merge Method</span></span>
<span data-ttu-id="88dc5-103">Adiciona o escopo importado especificado à lista de escopos a serem mesclados.</span><span class="sxs-lookup"><span data-stu-id="88dc5-103">Adds the specified imported scope to the list of scopes to be merged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="88dc5-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="88dc5-104">Syntax</span></span>  
  
```cpp  
HRESULT Merge (
    [in]  IMetaDataImport  *pImport,
    [in]  IMapToken        *pHostMapToken,
    [in]  IUnknown         *pHandler
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="88dc5-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="88dc5-105">Parameters</span></span>  
 `pImport`  
 <span data-ttu-id="88dc5-106">no Um ponteiro para um objeto [IMetaDataImport](imetadataimport-interface.md) que identifica o escopo importado a ser mesclado.</span><span class="sxs-lookup"><span data-stu-id="88dc5-106">[in] A pointer to an [IMetaDataImport](imetadataimport-interface.md) object that identifies the imported scope to be merged.</span></span>  
  
 `pIMap`  
 <span data-ttu-id="88dc5-107">no Um ponteiro para um objeto [IMapToken](imaptoken-interface.md) que especifica o novo mapeamento do token.</span><span class="sxs-lookup"><span data-stu-id="88dc5-107">[in] A pointer to an [IMapToken](imaptoken-interface.md) object that specifies the token re-map.</span></span>  
  
 `pHandler`  
 <span data-ttu-id="88dc5-108">no Um ponteiro para um objeto [IUnknown](/cpp/atl/iunknown) que especifica os erros.</span><span class="sxs-lookup"><span data-stu-id="88dc5-108">[in] A pointer to an [IUnknown](/cpp/atl/iunknown) object that specifies the errors.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="88dc5-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="88dc5-109">Remarks</span></span>  
 <span data-ttu-id="88dc5-110">Chame [IMetaDataEmit:: MergeEnd](imetadataemit-mergeend-method.md) para disparar a fusão de metadados em um único escopo.</span><span class="sxs-lookup"><span data-stu-id="88dc5-110">Call [IMetaDataEmit::MergeEnd](imetadataemit-mergeend-method.md) to trigger the merger of metadata into a single scope.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="88dc5-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="88dc5-111">Requirements</span></span>  
 <span data-ttu-id="88dc5-112">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="88dc5-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="88dc5-113">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="88dc5-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="88dc5-114">**Biblioteca:** Usado como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="88dc5-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="88dc5-115">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="88dc5-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88dc5-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="88dc5-116">See also</span></span>

- [<span data-ttu-id="88dc5-117">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="88dc5-117">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="88dc5-118">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="88dc5-118">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
