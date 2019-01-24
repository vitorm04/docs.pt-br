---
title: Método IMetaDataEmit::DeleteFieldMarshal
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DeleteFieldMarshal
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DeleteFieldMarshal
helpviewer_keywords:
- IMetaDataEmit::DeleteFieldMarshal method [.NET Framework metadata]
- DeleteFieldMarshal method [.NET Framework metadata]
ms.assetid: 7c75aef9-c742-4b33-a14b-56ff94b0f725
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e7ba2d6f143b6bbb9ddc5a056191e53f719bfeb1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54643943"
---
# <a name="imetadataemitdeletefieldmarshal-method"></a><span data-ttu-id="526c5-102">Método IMetaDataEmit::DeleteFieldMarshal</span><span class="sxs-lookup"><span data-stu-id="526c5-102">IMetaDataEmit::DeleteFieldMarshal Method</span></span>
<span data-ttu-id="526c5-103">Destrói o PInvoke marshaling de assinatura de metadados do objeto referenciado pelo token especificado.</span><span class="sxs-lookup"><span data-stu-id="526c5-103">Destroys the PInvoke marshaling metadata signature for the object referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="526c5-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="526c5-104">Syntax</span></span>  
  
```  
HRESULT DeleteFieldMarshal (  
    [in]  mdToken     tk  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="526c5-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="526c5-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="526c5-106">[in] Uma `mdFieldDef` ou `mdParamDef` token que representa o campo ou parâmetro para o qual excluir a assinatura de metadados de marshaling.</span><span class="sxs-lookup"><span data-stu-id="526c5-106">[in] An `mdFieldDef` or `mdParamDef` token that represents the field or parameter for which to delete the marshaling metadata signature.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="526c5-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="526c5-107">Requirements</span></span>  
 <span data-ttu-id="526c5-108">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="526c5-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="526c5-109">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="526c5-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="526c5-110">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="526c5-110">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="526c5-111">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="526c5-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="526c5-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="526c5-112">See also</span></span>
- [<span data-ttu-id="526c5-113">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="526c5-113">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="526c5-114">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="526c5-114">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
