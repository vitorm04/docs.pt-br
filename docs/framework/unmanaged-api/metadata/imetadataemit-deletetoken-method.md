---
title: Método IMetaDataEmit::DeleteToken
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DeleteToken
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DeleteToken
helpviewer_keywords:
- DeleteToken method [.NET Framework metadata]
- IMetaDataEmit::DeleteToken method [.NET Framework metadata]
ms.assetid: a4926d0a-261b-46b1-9994-82633661a64b
topic_type:
- apiref
ms.openlocfilehash: 3b8aed6522b1c7eb2d8916f71d8a66b367623765
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177602"
---
# <a name="imetadataemitdeletetoken-method"></a><span data-ttu-id="27bc8-102">Método IMetaDataEmit::DeleteToken</span><span class="sxs-lookup"><span data-stu-id="27bc8-102">IMetaDataEmit::DeleteToken Method</span></span>
<span data-ttu-id="27bc8-103">Exclui o token especificado do escopo de metadados atual.</span><span class="sxs-lookup"><span data-stu-id="27bc8-103">Deletes the specified token from the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27bc8-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="27bc8-104">Syntax</span></span>  
  
```cpp  
HRESULT DeleteToken (
    [in]  mdToken     tkObj
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="27bc8-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="27bc8-105">Parameters</span></span>  
 `tkObj`  
 <span data-ttu-id="27bc8-106">[em] O token a ser excluído.</span><span class="sxs-lookup"><span data-stu-id="27bc8-106">[in] The token to be deleted.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="27bc8-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="27bc8-107">Requirements</span></span>  
 <span data-ttu-id="27bc8-108">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="27bc8-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="27bc8-109">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="27bc8-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="27bc8-110">**Biblioteca:** Usado como recurso em MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="27bc8-110">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="27bc8-111">**.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="27bc8-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27bc8-112">Confira também</span><span class="sxs-lookup"><span data-stu-id="27bc8-112">See also</span></span>

- [<span data-ttu-id="27bc8-113">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="27bc8-113">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="27bc8-114">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="27bc8-114">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
