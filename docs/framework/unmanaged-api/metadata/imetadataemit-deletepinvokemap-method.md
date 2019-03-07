---
title: Método IMetaDataEmit::DeletePinvokeMap
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DeletePinvokeMap
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DeletePinvokeMap
helpviewer_keywords:
- IMetaDataEmit::DeletePinvokeMap method [.NET Framework metadata]
- DeletePinvokeMap method [.NET Framework metadata]
ms.assetid: 3c4f6b54-5ce7-4a2a-83e1-6dec16441f50
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5775c249236fdbe488ce11be0c664d2073ccfb67
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57477069"
---
# <a name="imetadataemitdeletepinvokemap-method"></a><span data-ttu-id="82e71-102">Método IMetaDataEmit::DeletePinvokeMap</span><span class="sxs-lookup"><span data-stu-id="82e71-102">IMetaDataEmit::DeletePinvokeMap Method</span></span>
<span data-ttu-id="82e71-103">Destrói os metadados de mapeamento de PInvoke do objeto referenciado pelo token especificado.</span><span class="sxs-lookup"><span data-stu-id="82e71-103">Destroys the PInvoke mapping metadata for the object referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82e71-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="82e71-104">Syntax</span></span>  
  
```  
HRESULT DeletePinvokeMap (   
    [in]  mdToken     tk   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="82e71-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="82e71-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="82e71-106">[in] Uma `mdFieldDef` ou `mdMethodDef` token que representa o objeto para o qual excluir os metadados de mapeamento do PInvoke.</span><span class="sxs-lookup"><span data-stu-id="82e71-106">[in] An `mdFieldDef` or `mdMethodDef` token that represents the object for which to delete the PInvoke mapping metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="82e71-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="82e71-107">Requirements</span></span>  
 <span data-ttu-id="82e71-108">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="82e71-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="82e71-109">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="82e71-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="82e71-110">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="82e71-110">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="82e71-111">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="82e71-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82e71-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="82e71-112">See also</span></span>
- [<span data-ttu-id="82e71-113">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="82e71-113">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="82e71-114">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="82e71-114">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
