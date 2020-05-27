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
ms.openlocfilehash: 6d0f9a8c5c3baf7594e098a3d5544bad55fdc917
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009282"
---
# <a name="imetadataemitdeletefieldmarshal-method"></a><span data-ttu-id="afe14-102">Método IMetaDataEmit::DeleteFieldMarshal</span><span class="sxs-lookup"><span data-stu-id="afe14-102">IMetaDataEmit::DeleteFieldMarshal Method</span></span>
<span data-ttu-id="afe14-103">Destrói a assinatura de metadados de marshaling do PInvoke para o objeto referenciado pelo token especificado.</span><span class="sxs-lookup"><span data-stu-id="afe14-103">Destroys the PInvoke marshaling metadata signature for the object referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="afe14-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="afe14-104">Syntax</span></span>  
  
```cpp  
HRESULT DeleteFieldMarshal (  
    [in]  mdToken     tk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="afe14-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="afe14-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="afe14-106">no Um `mdFieldDef` `mdParamDef` token ou que representa o campo ou parâmetro para o qual excluir a assinatura de metadados de marshaling.</span><span class="sxs-lookup"><span data-stu-id="afe14-106">[in] An `mdFieldDef` or `mdParamDef` token that represents the field or parameter for which to delete the marshaling metadata signature.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="afe14-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="afe14-107">Requirements</span></span>  
 <span data-ttu-id="afe14-108">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="afe14-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="afe14-109">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="afe14-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="afe14-110">**Biblioteca:** Usado como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="afe14-110">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="afe14-111">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="afe14-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="afe14-112">Confira também</span><span class="sxs-lookup"><span data-stu-id="afe14-112">See also</span></span>

- [<span data-ttu-id="afe14-113">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="afe14-113">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="afe14-114">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="afe14-114">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
