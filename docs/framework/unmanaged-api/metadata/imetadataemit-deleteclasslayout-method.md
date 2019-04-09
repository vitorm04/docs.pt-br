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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a195daf2aa1b1c5a8f9c4335f7c4185f30093360
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59178523"
---
# <a name="imetadataemitdeleteclasslayout-method"></a><span data-ttu-id="dc74d-102">Método IMetaDataEmit::DeleteClassLayout</span><span class="sxs-lookup"><span data-stu-id="dc74d-102">IMetaDataEmit::DeleteClassLayout Method</span></span>
<span data-ttu-id="dc74d-103">Destrói a assinatura de metadados de layout de classe para o tipo representado pelo token especificado.</span><span class="sxs-lookup"><span data-stu-id="dc74d-103">Destroys the class layout metadata signature for the type represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dc74d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="dc74d-104">Syntax</span></span>  
  
```  
HRESULT DeleteClassLayout (  
    [in]  mdTypeDef   td  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dc74d-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="dc74d-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="dc74d-106">[in] Um `mdTypeDef` token de metadados que representa o tipo para o qual o layout da classe será excluído.</span><span class="sxs-lookup"><span data-stu-id="dc74d-106">[in] An `mdTypeDef` metadata token that represents the type for which the class layout will be deleted.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dc74d-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="dc74d-107">Requirements</span></span>  
 <span data-ttu-id="dc74d-108">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dc74d-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dc74d-109">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="dc74d-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="dc74d-110">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="dc74d-110">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="dc74d-111">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="dc74d-111">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="dc74d-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dc74d-112">See also</span></span>

- [<span data-ttu-id="dc74d-113">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="dc74d-113">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="dc74d-114">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="dc74d-114">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
