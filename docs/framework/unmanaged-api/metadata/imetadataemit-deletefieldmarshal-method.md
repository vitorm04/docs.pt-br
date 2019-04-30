---
title: Método IMetaDataEmit::DeleteFieldMarshal
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DeleteFieldMarshal
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DeleteFieldMarshal
helpviewer_keywords:
- IMetaDataEmit::DeleteFieldMarshal method [.NET Framework metadata]
- DeleteFieldMarshal method [.NET Framework metadata]
ms.assetid: 7c75aef9-c742-4b33-a14b-56ff94b0f725
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 78f2405bba9172b775b01e5417860c3f3d2dd4a4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61992518"
---
# <a name="imetadataemitdeletefieldmarshal-method"></a><span data-ttu-id="1e83c-102">Método IMetaDataEmit::DeleteFieldMarshal</span><span class="sxs-lookup"><span data-stu-id="1e83c-102">IMetaDataEmit::DeleteFieldMarshal Method</span></span>
<span data-ttu-id="1e83c-103">Destrói o PInvoke marshaling de assinatura de metadados do objeto referenciado pelo token especificado.</span><span class="sxs-lookup"><span data-stu-id="1e83c-103">Destroys the PInvoke marshaling metadata signature for the object referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1e83c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1e83c-104">Syntax</span></span>  
  
```  
HRESULT DeleteFieldMarshal (  
    [in]  mdToken     tk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1e83c-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="1e83c-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="1e83c-106">[in] Uma `mdFieldDef` ou `mdParamDef` token que representa o campo ou parâmetro para o qual excluir a assinatura de metadados de marshaling.</span><span class="sxs-lookup"><span data-stu-id="1e83c-106">[in] An `mdFieldDef` or `mdParamDef` token that represents the field or parameter for which to delete the marshaling metadata signature.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1e83c-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1e83c-107">Requirements</span></span>  
 <span data-ttu-id="1e83c-108">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1e83c-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1e83c-109">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="1e83c-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1e83c-110">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="1e83c-110">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1e83c-111">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1e83c-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e83c-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1e83c-112">See also</span></span>

- [<span data-ttu-id="1e83c-113">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="1e83c-113">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="1e83c-114">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="1e83c-114">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
