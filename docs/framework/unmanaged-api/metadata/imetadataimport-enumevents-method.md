---
title: "Método IMetaDataImport::EnumEvents"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.EnumEvents
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::EnumEvents
helpviewer_keywords:
- IMetaDataImport::EnumEvents method [.NET Framework metadata]
- EnumEvents method [.NET Framework metadata]
ms.assetid: e1efedcb-3dd7-42ae-a399-21c24728aec5
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: ba893d59f9f119ce2f7eaf1af4ce268b6534acd1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportenumevents-method"></a><span data-ttu-id="ac05d-102">Método IMetaDataImport::EnumEvents</span><span class="sxs-lookup"><span data-stu-id="ac05d-102">IMetaDataImport::EnumEvents Method</span></span>
<span data-ttu-id="ac05d-103">Enumera os tokens de definição de eventos para o token de TypeDef especificado.</span><span class="sxs-lookup"><span data-stu-id="ac05d-103">Enumerates event definition tokens for the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac05d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ac05d-104">Syntax</span></span>  
  
```  
HRESULT EnumEvents (   
   [in, out] HCORENUM    *phEnum,   
   [in]      mdTypeDef   td,   
   [out]     mdEvent     rEvents[],   
   [in]      ULONG       cMax,  
   [out]    ULONG        *pcEvents  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ac05d-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ac05d-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="ac05d-106">[out no] Um ponteiro para o enumerador.</span><span class="sxs-lookup"><span data-stu-id="ac05d-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `td`  
 <span data-ttu-id="ac05d-107">[in] O token de TypeDef cujas definições de evento são a serem enumerados.</span><span class="sxs-lookup"><span data-stu-id="ac05d-107">[in] The TypeDef token whose event definitions are to be enumerated.</span></span>  
  
 `rEvents`  
 <span data-ttu-id="ac05d-108">[out] A matriz de eventos retornados.</span><span class="sxs-lookup"><span data-stu-id="ac05d-108">[out] The array of returned events.</span></span>  
  
 `cMax`  
 <span data-ttu-id="ac05d-109">[in] O tamanho máximo da `rEvents` matriz.</span><span class="sxs-lookup"><span data-stu-id="ac05d-109">[in] The maximum size of the `rEvents` array.</span></span>  
  
 `pcEvents`  
 <span data-ttu-id="ac05d-110">[out] O número real de eventos retornados em `rEvents`.</span><span class="sxs-lookup"><span data-stu-id="ac05d-110">[out] The actual number of events returned in `rEvents`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ac05d-111">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="ac05d-111">Return Value</span></span>  
  
|<span data-ttu-id="ac05d-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ac05d-112">HRESULT</span></span>|<span data-ttu-id="ac05d-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="ac05d-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="ac05d-114">`EnumEvents`retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="ac05d-114">`EnumEvents` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="ac05d-115">Não existem eventos para enumerar.</span><span class="sxs-lookup"><span data-stu-id="ac05d-115">There are no events to enumerate.</span></span> <span data-ttu-id="ac05d-116">Nesse caso, `pcEvents` é zero.</span><span class="sxs-lookup"><span data-stu-id="ac05d-116">In that case, `pcEvents` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ac05d-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ac05d-117">Requirements</span></span>  
 <span data-ttu-id="ac05d-118">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ac05d-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ac05d-119">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="ac05d-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ac05d-120">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="ac05d-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ac05d-121">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ac05d-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac05d-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ac05d-122">See Also</span></span>  
 [<span data-ttu-id="ac05d-123">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="ac05d-123">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="ac05d-124">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="ac05d-124">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
