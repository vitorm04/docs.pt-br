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
ms.openlocfilehash: 34db47b9f43412c9b6c5f58dd6afded505703905
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33445371"
---
# <a name="imetadataemitdeletepinvokemap-method"></a><span data-ttu-id="ac195-102">Método IMetaDataEmit::DeletePinvokeMap</span><span class="sxs-lookup"><span data-stu-id="ac195-102">IMetaDataEmit::DeletePinvokeMap Method</span></span>
<span data-ttu-id="ac195-103">Destrói os metadados de mapeamento de PInvoke para o objeto referenciado por token especificado.</span><span class="sxs-lookup"><span data-stu-id="ac195-103">Destroys the PInvoke mapping metadata for the object referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac195-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ac195-104">Syntax</span></span>  
  
```  
HRESULT DeletePinvokeMap (   
    [in]  mdToken     tk   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ac195-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ac195-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="ac195-106">[in] Um `mdFieldDef` ou `mdMethodDef` token que representa o objeto para o qual excluir os metadados de mapeamento de PInvoke.</span><span class="sxs-lookup"><span data-stu-id="ac195-106">[in] An `mdFieldDef` or `mdMethodDef` token that represents the object for which to delete the PInvoke mapping metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ac195-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ac195-107">Requirements</span></span>  
 <span data-ttu-id="ac195-108">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ac195-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ac195-109">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="ac195-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ac195-110">**Biblioteca:** usado como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="ac195-110">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ac195-111">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ac195-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac195-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ac195-112">See Also</span></span>  
 [<span data-ttu-id="ac195-113">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="ac195-113">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="ac195-114">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="ac195-114">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
