---
title: "Método IMetaDataImport::EnumTypeRefs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.EnumTypeRefs
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::EnumTypeRefs
helpviewer_keywords:
- EnumTypeRefs method [.NET Framework metadata]
- IMetaDataImport::EnumTypeRefs method [.NET Framework metadata]
ms.assetid: b4896b8f-8e97-469c-8089-e72a025661b5
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 890f70900f2a1d4909d1511791d4d22bb81d3a1b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportenumtyperefs-method"></a><span data-ttu-id="38911-102">Método IMetaDataImport::EnumTypeRefs</span><span class="sxs-lookup"><span data-stu-id="38911-102">IMetaDataImport::EnumTypeRefs Method</span></span>
<span data-ttu-id="38911-103">Enumera os tokens de TypeRef definidos no escopo atual de metadados.</span><span class="sxs-lookup"><span data-stu-id="38911-103">Enumerates TypeRef tokens defined in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38911-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="38911-104">Syntax</span></span>  
  
```  
HRESULT EnumTypeRefs (  
   [in, out] HCORENUM    *phEnum,   
   [out] mdTypeRef       rTypeRefs[],  
   [in]  ULONG           cMax,   
   [out] ULONG           *pcTypeRefs  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="38911-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="38911-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="38911-106">[out no] Um ponteiro para o enumerador.</span><span class="sxs-lookup"><span data-stu-id="38911-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="38911-107">Isso deve ser NULL para a primeira chamada do método.</span><span class="sxs-lookup"><span data-stu-id="38911-107">This must be NULL for the first call of this method.</span></span>  
  
 `rTypeRefs`  
 <span data-ttu-id="38911-108">[out] A matriz usada para armazenar os tokens de TypeRef.</span><span class="sxs-lookup"><span data-stu-id="38911-108">[out] The array used to store the TypeRef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="38911-109">[in] O tamanho máximo da `rTypeRefs` matriz.</span><span class="sxs-lookup"><span data-stu-id="38911-109">[in] The maximum size of the `rTypeRefs` array.</span></span>  
  
 `pcTypeRefs`  
 <span data-ttu-id="38911-110">[out] Um ponteiro para o número de tokens de TypeRef retornados em `rTypeRefs`.</span><span class="sxs-lookup"><span data-stu-id="38911-110">[out] A pointer to the number of TypeRef tokens returned in `rTypeRefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="38911-111">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="38911-111">Return Value</span></span>  
  
|<span data-ttu-id="38911-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="38911-112">HRESULT</span></span>|<span data-ttu-id="38911-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="38911-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="38911-114">`EnumTypeRefs`retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="38911-114">`EnumTypeRefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="38911-115">Não há nenhum tokens para enumerar.</span><span class="sxs-lookup"><span data-stu-id="38911-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="38911-116">Nesse caso, `pcTypeRefs` é zero.</span><span class="sxs-lookup"><span data-stu-id="38911-116">In that case, `pcTypeRefs` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="38911-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="38911-117">Remarks</span></span>  
 <span data-ttu-id="38911-118">Um token TypeRef representa uma referência a um tipo.</span><span class="sxs-lookup"><span data-stu-id="38911-118">A TypeRef token represents a reference to a type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="38911-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="38911-119">Requirements</span></span>  
 <span data-ttu-id="38911-120">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="38911-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="38911-121">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="38911-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="38911-122">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="38911-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="38911-123">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="38911-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38911-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="38911-124">See Also</span></span>  
 [<span data-ttu-id="38911-125">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="38911-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="38911-126">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="38911-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
