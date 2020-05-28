---
title: Método IMetaDataEmit::DeleteClassLayout
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DeleteClassLayout
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DeleteClassLayout
helpviewer_keywords:
- DeleteClassLayout method [.NET Framework metadata]
- IMetaDataEmit::DeleteClassLayout method [.NET Framework metadata]
ms.assetid: 65a4ad49-fa49-4b36-8ed1-76dd6a185ab4
topic_type:
- apiref
ms.openlocfilehash: 3ef6b89ed6578d77f30d5e53657b962b200b0ed6
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009309"
---
# <a name="imetadataemitdeleteclasslayout-method"></a><span data-ttu-id="58f6d-102">Método IMetaDataEmit::DeleteClassLayout</span><span class="sxs-lookup"><span data-stu-id="58f6d-102">IMetaDataEmit::DeleteClassLayout Method</span></span>
<span data-ttu-id="58f6d-103">Destrói a assinatura de metadados de layout de classe para o tipo representado pelo token especificado.</span><span class="sxs-lookup"><span data-stu-id="58f6d-103">Destroys the class layout metadata signature for the type represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58f6d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="58f6d-104">Syntax</span></span>  
  
```cpp  
HRESULT DeleteClassLayout (  
    [in]  mdTypeDef   td  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="58f6d-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="58f6d-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="58f6d-106">no Um `mdTypeDef` token de metadados que representa o tipo para o qual o layout de classe será excluído.</span><span class="sxs-lookup"><span data-stu-id="58f6d-106">[in] An `mdTypeDef` metadata token that represents the type for which the class layout will be deleted.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="58f6d-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="58f6d-107">Requirements</span></span>  
 <span data-ttu-id="58f6d-108">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="58f6d-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="58f6d-109">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="58f6d-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="58f6d-110">**Biblioteca:** Usado como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="58f6d-110">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="58f6d-111">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="58f6d-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58f6d-112">Confira também</span><span class="sxs-lookup"><span data-stu-id="58f6d-112">See also</span></span>

- [<span data-ttu-id="58f6d-113">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="58f6d-113">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="58f6d-114">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="58f6d-114">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
