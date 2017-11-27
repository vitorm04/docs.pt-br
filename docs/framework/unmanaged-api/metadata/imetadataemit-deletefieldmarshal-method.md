---
title: "Método IMetaDataEmit::DeleteFieldMarshal"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.DeleteFieldMarshal
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::DeleteFieldMarshal
helpviewer_keywords:
- IMetaDataEmit::DeleteFieldMarshal method [.NET Framework metadata]
- DeleteFieldMarshal method [.NET Framework metadata]
ms.assetid: 7c75aef9-c742-4b33-a14b-56ff94b0f725
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: f66307a2589a824db0f8ce9dca737e6b201dad59
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemitdeletefieldmarshal-method"></a><span data-ttu-id="ee65e-102">Método IMetaDataEmit::DeleteFieldMarshal</span><span class="sxs-lookup"><span data-stu-id="ee65e-102">IMetaDataEmit::DeleteFieldMarshal Method</span></span>
<span data-ttu-id="ee65e-103">Destrói o PInvoke empacotamento de assinatura de metadados para o objeto referenciado por token especificado.</span><span class="sxs-lookup"><span data-stu-id="ee65e-103">Destroys the PInvoke marshaling metadata signature for the object referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ee65e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ee65e-104">Syntax</span></span>  
  
```  
HRESULT DeleteFieldMarshal (  
    [in]  mdToken     tk  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ee65e-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ee65e-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="ee65e-106">[in] Um `mdFieldDef` ou `mdParamDef` token que representa o campo ou parâmetro para o qual excluir a assinatura de metadados de marshaling.</span><span class="sxs-lookup"><span data-stu-id="ee65e-106">[in] An `mdFieldDef` or `mdParamDef` token that represents the field or parameter for which to delete the marshaling metadata signature.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ee65e-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ee65e-107">Requirements</span></span>  
 <span data-ttu-id="ee65e-108">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ee65e-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ee65e-109">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="ee65e-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ee65e-110">**Biblioteca:** usado como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="ee65e-110">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ee65e-111">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ee65e-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee65e-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ee65e-112">See Also</span></span>  
 [<span data-ttu-id="ee65e-113">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="ee65e-113">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="ee65e-114">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="ee65e-114">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
