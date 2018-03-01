---
title: "Método IMetaDataEmit::SetFieldMarshal"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IMetaDataEmit.SetFieldMarshal
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetFieldMarshal
helpviewer_keywords:
- SetFieldMarshal method [.NET Framework metadata]
- IMetaDataEmit::SetFieldMarshal method [.NET Framework metadata]
ms.assetid: be232314-7f69-4855-bfab-63361bd22307
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 20186870510e67e518414d2bd5e9a00fd5164dc8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemitsetfieldmarshal-method"></a><span data-ttu-id="78613-102">Método IMetaDataEmit::SetFieldMarshal</span><span class="sxs-lookup"><span data-stu-id="78613-102">IMetaDataEmit::SetFieldMarshal Method</span></span>
<span data-ttu-id="78613-103">Define o PInvoke marshaling informações para o parâmetro de campo, método de retorno ou método referenciada pelo token especificado.</span><span class="sxs-lookup"><span data-stu-id="78613-103">Sets the PInvoke marshaling information for the field, method return, or method parameter referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78613-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="78613-104">Syntax</span></span>  
  
```  
HRESULT SetFieldMarshal (  
    [in]  mdToken          tk,   
    [in]  PCCOR_SIGNATURE  pvNativeType,   
    [in]  ULONG            cbNativeType   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="78613-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="78613-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="78613-106">[in] O token para o item de dados de destino.</span><span class="sxs-lookup"><span data-stu-id="78613-106">[in] The token for target data item.</span></span> <span data-ttu-id="78613-107">Isso é uma `mdFieldDef` ou um `mdParamDef` token.</span><span class="sxs-lookup"><span data-stu-id="78613-107">This is either a `mdFieldDef` or a `mdParamDef` token.</span></span>  
  
 `pvNativeType`  
 <span data-ttu-id="78613-108">[in] A assinatura para o tipo não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="78613-108">[in] The signature for unmanaged type.</span></span>  
  
 `cbNativeType`  
 <span data-ttu-id="78613-109">[in] A contagem de bytes em `pvNativeType`.</span><span class="sxs-lookup"><span data-stu-id="78613-109">[in] The count of bytes in `pvNativeType`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="78613-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="78613-110">Requirements</span></span>  
 <span data-ttu-id="78613-111">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="78613-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="78613-112">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="78613-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="78613-113">**Biblioteca:** usado como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="78613-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="78613-114">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="78613-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78613-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="78613-115">See Also</span></span>  
 [<span data-ttu-id="78613-116">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="78613-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="78613-117">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="78613-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
