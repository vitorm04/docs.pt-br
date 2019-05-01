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
ms.openlocfilehash: 5ea100ff86286cb98db5aa9fa6f3c12f5d318a90
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62043117"
---
# <a name="imetadataemitdeletepinvokemap-method"></a><span data-ttu-id="fd342-102">Método IMetaDataEmit::DeletePinvokeMap</span><span class="sxs-lookup"><span data-stu-id="fd342-102">IMetaDataEmit::DeletePinvokeMap Method</span></span>
<span data-ttu-id="fd342-103">Destrói os metadados de mapeamento de PInvoke do objeto referenciado pelo token especificado.</span><span class="sxs-lookup"><span data-stu-id="fd342-103">Destroys the PInvoke mapping metadata for the object referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fd342-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fd342-104">Syntax</span></span>  
  
```  
HRESULT DeletePinvokeMap (   
    [in]  mdToken     tk   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fd342-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="fd342-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="fd342-106">[in] Uma `mdFieldDef` ou `mdMethodDef` token que representa o objeto para o qual excluir os metadados de mapeamento do PInvoke.</span><span class="sxs-lookup"><span data-stu-id="fd342-106">[in] An `mdFieldDef` or `mdMethodDef` token that represents the object for which to delete the PInvoke mapping metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fd342-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="fd342-107">Requirements</span></span>  
 <span data-ttu-id="fd342-108">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fd342-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fd342-109">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="fd342-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="fd342-110">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="fd342-110">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fd342-111">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fd342-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd342-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fd342-112">See also</span></span>

- [<span data-ttu-id="fd342-113">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="fd342-113">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="fd342-114">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="fd342-114">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
