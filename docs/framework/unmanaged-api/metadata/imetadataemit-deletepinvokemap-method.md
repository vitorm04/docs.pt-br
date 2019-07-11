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
ms.openlocfilehash: 64ba852c4bb0ae7b0119876fca4a4b2a107ed934
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777424"
---
# <a name="imetadataemitdeletepinvokemap-method"></a><span data-ttu-id="a9e54-102">Método IMetaDataEmit::DeletePinvokeMap</span><span class="sxs-lookup"><span data-stu-id="a9e54-102">IMetaDataEmit::DeletePinvokeMap Method</span></span>
<span data-ttu-id="a9e54-103">Destrói os metadados de mapeamento de PInvoke do objeto referenciado pelo token especificado.</span><span class="sxs-lookup"><span data-stu-id="a9e54-103">Destroys the PInvoke mapping metadata for the object referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a9e54-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a9e54-104">Syntax</span></span>  
  
```cpp  
HRESULT DeletePinvokeMap (   
    [in]  mdToken     tk   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a9e54-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a9e54-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="a9e54-106">[in] Uma `mdFieldDef` ou `mdMethodDef` token que representa o objeto para o qual excluir os metadados de mapeamento do PInvoke.</span><span class="sxs-lookup"><span data-stu-id="a9e54-106">[in] An `mdFieldDef` or `mdMethodDef` token that represents the object for which to delete the PInvoke mapping metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a9e54-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a9e54-107">Requirements</span></span>  
 <span data-ttu-id="a9e54-108">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a9e54-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a9e54-109">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="a9e54-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a9e54-110">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="a9e54-110">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a9e54-111">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a9e54-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9e54-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a9e54-112">See also</span></span>

- [<span data-ttu-id="a9e54-113">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="a9e54-113">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="a9e54-114">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="a9e54-114">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
