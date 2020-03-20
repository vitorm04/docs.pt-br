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
ms.openlocfilehash: 45f40dcd419e8e2fdf8a3349ccc9461854ad9aaf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175727"
---
# <a name="imetadataemitdeletepinvokemap-method"></a><span data-ttu-id="7f02c-102">Método IMetaDataEmit::DeletePinvokeMap</span><span class="sxs-lookup"><span data-stu-id="7f02c-102">IMetaDataEmit::DeletePinvokeMap Method</span></span>
<span data-ttu-id="7f02c-103">Destrói os metadados de mapeamento do PInvoke para o objeto referenciado pelo token especificado.</span><span class="sxs-lookup"><span data-stu-id="7f02c-103">Destroys the PInvoke mapping metadata for the object referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f02c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7f02c-104">Syntax</span></span>  
  
```cpp  
HRESULT DeletePinvokeMap (
    [in]  mdToken     tk
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7f02c-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="7f02c-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="7f02c-106">[em] Um `mdFieldDef` `mdMethodDef` ou token que representa o objeto para o qual excluir os metadados de mapeamento do PInvoke.</span><span class="sxs-lookup"><span data-stu-id="7f02c-106">[in] An `mdFieldDef` or `mdMethodDef` token that represents the object for which to delete the PInvoke mapping metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7f02c-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7f02c-107">Requirements</span></span>  
 <span data-ttu-id="7f02c-108">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7f02c-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7f02c-109">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="7f02c-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7f02c-110">**Biblioteca:** Usado como recurso em MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7f02c-110">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7f02c-111">**.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7f02c-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f02c-112">Confira também</span><span class="sxs-lookup"><span data-stu-id="7f02c-112">See also</span></span>

- [<span data-ttu-id="7f02c-113">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="7f02c-113">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="7f02c-114">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="7f02c-114">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
