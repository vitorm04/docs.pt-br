---
title: "Método IMetaDataImport::GetClassLayout"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.GetClassLayout
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::GetClassLayout
helpviewer_keywords:
- IMetaDataImport::GetClassLayout method [.NET Framework metadata]
- GetClassLayout method, IMetaDataImport interface [.NET Framework metadata]
ms.assetid: 8f35414d-f40b-4b99-8768-9adb675c622a
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: cece37a6321fc68cbff2957f9753af5f2f916f5f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportgetclasslayout-method"></a><span data-ttu-id="0fac5-102">Método IMetaDataImport::GetClassLayout</span><span class="sxs-lookup"><span data-stu-id="0fac5-102">IMetaDataImport::GetClassLayout Method</span></span>
<span data-ttu-id="0fac5-103">Obtém informações de layout para a classe referenciada por TypeDef especificado token.</span><span class="sxs-lookup"><span data-stu-id="0fac5-103">Gets layout information for the class referenced by the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0fac5-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0fac5-104">Syntax</span></span>  
  
```  
HRESULT GetClassLayout  (   
   [in]  mdTypeDef          td,   
   [out] DWORD              *pdwPackSize,  
   [out] COR_FIELD_OFFSET   rFieldOffset[],  
   [in]  ULONG              cMax,  
   [out] ULONG              *pcFieldOffset,  
   [out] ULONG              *pulClassSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0fac5-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0fac5-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="0fac5-106">[in] O token de TypeDef para a classe com o layout para retornar.</span><span class="sxs-lookup"><span data-stu-id="0fac5-106">[in] The TypeDef token for the class with the layout to return.</span></span>  
  
 `pdwPackSize`  
 <span data-ttu-id="0fac5-107">[out] Um dos valores de 1, 2, 4, 8 ou 16, que representa o tamanho do pacote da classe.</span><span class="sxs-lookup"><span data-stu-id="0fac5-107">[out] One of the values 1, 2, 4, 8, or 16, representing the pack size of the class.</span></span>  
  
 `rFieldOffset`  
 <span data-ttu-id="0fac5-108">[out] Uma matriz de [COR_FIELD_OFFSET](../../../../docs/framework/unmanaged-api/metadata/cor-field-offset-structure.md) valores.</span><span class="sxs-lookup"><span data-stu-id="0fac5-108">[out] An array of [COR_FIELD_OFFSET](../../../../docs/framework/unmanaged-api/metadata/cor-field-offset-structure.md) values.</span></span>  
  
 `cMax`  
 <span data-ttu-id="0fac5-109">[in] O tamanho máximo da `rFieldOffset` matriz.</span><span class="sxs-lookup"><span data-stu-id="0fac5-109">[in] The maximum size of the `rFieldOffset` array.</span></span>  
  
 `pcFieldOffset`  
 <span data-ttu-id="0fac5-110">[out] O número de elementos retornados em `rFieldOffset`.</span><span class="sxs-lookup"><span data-stu-id="0fac5-110">[out] The number of elements returned in `rFieldOffset`.</span></span>  
  
 `pulClassSize`  
 <span data-ttu-id="0fac5-111">[out] O tamanho em bytes da classe representada pelo `td`.</span><span class="sxs-lookup"><span data-stu-id="0fac5-111">[out] The size in bytes of the class represented by `td`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0fac5-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0fac5-112">Requirements</span></span>  
 <span data-ttu-id="0fac5-113">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0fac5-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0fac5-114">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="0fac5-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0fac5-115">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="0fac5-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0fac5-116">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0fac5-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0fac5-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0fac5-117">See Also</span></span>  
 [<span data-ttu-id="0fac5-118">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="0fac5-118">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="0fac5-119">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="0fac5-119">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
