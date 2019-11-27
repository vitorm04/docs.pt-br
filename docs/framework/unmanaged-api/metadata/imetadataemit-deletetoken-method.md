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
ms.openlocfilehash: e8c145632911817e8e19d587bb8afead0a6c33af
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74434338"
---
# <a name="imetadataemitdeletetoken-method"></a><span data-ttu-id="c90cd-102">Método IMetaDataEmit::DeleteToken</span><span class="sxs-lookup"><span data-stu-id="c90cd-102">IMetaDataEmit::DeleteToken Method</span></span>
<span data-ttu-id="c90cd-103">Exclui o token especificado do escopo de metadados atual.</span><span class="sxs-lookup"><span data-stu-id="c90cd-103">Deletes the specified token from the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c90cd-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c90cd-104">Syntax</span></span>  
  
```cpp  
HRESULT DeleteToken (   
    [in]  mdToken     tkObj   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c90cd-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c90cd-105">Parameters</span></span>  
 `tkObj`  
 <span data-ttu-id="c90cd-106">no O token a ser excluído.</span><span class="sxs-lookup"><span data-stu-id="c90cd-106">[in] The token to be deleted.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c90cd-107">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="c90cd-107">Requirements</span></span>  
 <span data-ttu-id="c90cd-108">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c90cd-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c90cd-109">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="c90cd-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c90cd-110">**Biblioteca:** Usado como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="c90cd-110">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c90cd-111">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c90cd-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c90cd-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c90cd-112">See also</span></span>

- [<span data-ttu-id="c90cd-113">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="c90cd-113">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="c90cd-114">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="c90cd-114">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
