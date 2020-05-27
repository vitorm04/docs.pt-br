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
ms.openlocfilehash: 78f3ea0d84c932732a752f3af2dc952100fef831
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009269"
---
# <a name="imetadataemitdeletetoken-method"></a><span data-ttu-id="d272a-102">Método IMetaDataEmit::DeleteToken</span><span class="sxs-lookup"><span data-stu-id="d272a-102">IMetaDataEmit::DeleteToken Method</span></span>
<span data-ttu-id="d272a-103">Exclui o token especificado do escopo de metadados atual.</span><span class="sxs-lookup"><span data-stu-id="d272a-103">Deletes the specified token from the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d272a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d272a-104">Syntax</span></span>  
  
```cpp  
HRESULT DeleteToken (
    [in]  mdToken     tkObj
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d272a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d272a-105">Parameters</span></span>  
 `tkObj`  
 <span data-ttu-id="d272a-106">no O token a ser excluído.</span><span class="sxs-lookup"><span data-stu-id="d272a-106">[in] The token to be deleted.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d272a-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d272a-107">Requirements</span></span>  
 <span data-ttu-id="d272a-108">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d272a-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d272a-109">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="d272a-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d272a-110">**Biblioteca:** Usado como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="d272a-110">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d272a-111">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d272a-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d272a-112">Confira também</span><span class="sxs-lookup"><span data-stu-id="d272a-112">See also</span></span>

- [<span data-ttu-id="d272a-113">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="d272a-113">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="d272a-114">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="d272a-114">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
