---
title: "Método IMetaDataImport::EnumProperties"
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
- IMetaDataImport.EnumProperties
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumProperties
helpviewer_keywords:
- IMetaDataImport::EnumProperties method [.NET Framework metadata]
- EnumProperties method [.NET Framework metadata]
ms.assetid: 60573ad7-8821-4721-a068-3f7a6d25926a
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 63ff10904440f55ec3fe6fb6aa581fbf560763e0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportenumproperties-method"></a><span data-ttu-id="babbb-102">Método IMetaDataImport::EnumProperties</span><span class="sxs-lookup"><span data-stu-id="babbb-102">IMetaDataImport::EnumProperties Method</span></span>
<span data-ttu-id="babbb-103">Enumera os tokens de PropertyDef que representa as propriedades do tipo referenciado pelo token de TypeDef especificado.</span><span class="sxs-lookup"><span data-stu-id="babbb-103">Enumerates PropertyDef tokens representing the properties of the type referenced by the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="babbb-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="babbb-104">Syntax</span></span>  
  
```  
HRESULT EnumProperties (  
   [in, out] HCORENUM    *phEnum,  
   [in]      mdTypeDef   td,  
   [out]     mdProperty  rProperties[],  
   [in]      ULONG       cMax,  
   [out]     ULONG       *pcProperties  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="babbb-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="babbb-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="babbb-106">[out no] Um ponteiro para o enumerador.</span><span class="sxs-lookup"><span data-stu-id="babbb-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="babbb-107">Isso deve ser NULL para a primeira chamada do método.</span><span class="sxs-lookup"><span data-stu-id="babbb-107">This must be NULL for the first call of this method.</span></span>  
  
 `td`  
 <span data-ttu-id="babbb-108">[in] Um token de TypeDef que representa o tipo com propriedades para enumerar.</span><span class="sxs-lookup"><span data-stu-id="babbb-108">[in] A TypeDef token representing the type with properties to enumerate.</span></span>  
  
 `rProperties`  
 <span data-ttu-id="babbb-109">[out] A matriz usada para armazenar os tokens de PropertyDef.</span><span class="sxs-lookup"><span data-stu-id="babbb-109">[out] The array used to store the PropertyDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="babbb-110">[in] O tamanho máximo da `rProperties` matriz.</span><span class="sxs-lookup"><span data-stu-id="babbb-110">[in] The maximum size of the `rProperties` array.</span></span>  
  
 `pcProperties`  
 <span data-ttu-id="babbb-111">[out] O número de tokens PropertyDef retornado em `rProperties`.</span><span class="sxs-lookup"><span data-stu-id="babbb-111">[out] The number of PropertyDef tokens returned in `rProperties`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="babbb-112">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="babbb-112">Return Value</span></span>  
  
|<span data-ttu-id="babbb-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="babbb-113">HRESULT</span></span>|<span data-ttu-id="babbb-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="babbb-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="babbb-115">`EnumProperties`retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="babbb-115">`EnumProperties` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="babbb-116">Não há nenhum tokens para enumerar.</span><span class="sxs-lookup"><span data-stu-id="babbb-116">There are no tokens to enumerate.</span></span> <span data-ttu-id="babbb-117">Nesse caso, `pcProperties` é zero.</span><span class="sxs-lookup"><span data-stu-id="babbb-117">In that case, `pcProperties` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="babbb-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="babbb-118">Requirements</span></span>  
 <span data-ttu-id="babbb-119">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="babbb-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="babbb-120">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="babbb-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="babbb-121">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="babbb-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="babbb-122">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="babbb-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="babbb-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="babbb-123">See Also</span></span>  
 [<span data-ttu-id="babbb-124">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="babbb-124">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="babbb-125">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="babbb-125">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
