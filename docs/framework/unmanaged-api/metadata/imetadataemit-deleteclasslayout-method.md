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
ms.openlocfilehash: 663f2de5acb3aac92c29a19f5f5db16b5355fe89
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33444777"
---
# <a name="imetadataemitdeleteclasslayout-method"></a><span data-ttu-id="0522e-102">Método IMetaDataEmit::DeleteClassLayout</span><span class="sxs-lookup"><span data-stu-id="0522e-102">IMetaDataEmit::DeleteClassLayout Method</span></span>
<span data-ttu-id="0522e-103">Destrói a assinatura de metadados de layout de classe para o tipo representado pelo token especificado.</span><span class="sxs-lookup"><span data-stu-id="0522e-103">Destroys the class layout metadata signature for the type represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0522e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0522e-104">Syntax</span></span>  
  
```  
HRESULT DeleteClassLayout (  
    [in]  mdTypeDef   td  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0522e-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0522e-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="0522e-106">[in] Um `mdTypeDef` token de metadados que representa o tipo para o qual o layout de classe será excluído.</span><span class="sxs-lookup"><span data-stu-id="0522e-106">[in] An `mdTypeDef` metadata token that represents the type for which the class layout will be deleted.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0522e-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0522e-107">Requirements</span></span>  
 <span data-ttu-id="0522e-108">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0522e-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0522e-109">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="0522e-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0522e-110">**Biblioteca:** usado como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="0522e-110">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0522e-111">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0522e-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0522e-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0522e-112">See Also</span></span>  
 [<span data-ttu-id="0522e-113">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="0522e-113">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="0522e-114">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="0522e-114">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
