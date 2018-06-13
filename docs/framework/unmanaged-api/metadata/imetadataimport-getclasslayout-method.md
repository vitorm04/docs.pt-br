---
title: Método IMetaDataImport::GetClassLayout
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetClassLayout
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetClassLayout
helpviewer_keywords:
- IMetaDataImport::GetClassLayout method [.NET Framework metadata]
- GetClassLayout method, IMetaDataImport interface [.NET Framework metadata]
ms.assetid: 8f35414d-f40b-4b99-8768-9adb675c622a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b031fc35a4687a8535e3cb5e9ef2a53bab9fe376
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33445501"
---
# <a name="imetadataimportgetclasslayout-method"></a><span data-ttu-id="ab28d-102">Método IMetaDataImport::GetClassLayout</span><span class="sxs-lookup"><span data-stu-id="ab28d-102">IMetaDataImport::GetClassLayout Method</span></span>
<span data-ttu-id="ab28d-103">Obtém informações de layout para a classe referenciada por TypeDef especificado token.</span><span class="sxs-lookup"><span data-stu-id="ab28d-103">Gets layout information for the class referenced by the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab28d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ab28d-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="ab28d-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ab28d-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="ab28d-106">[in] O token de TypeDef para a classe com o layout para retornar.</span><span class="sxs-lookup"><span data-stu-id="ab28d-106">[in] The TypeDef token for the class with the layout to return.</span></span>  
  
 `pdwPackSize`  
 <span data-ttu-id="ab28d-107">[out] Um dos valores de 1, 2, 4, 8 ou 16, que representa o tamanho do pacote da classe.</span><span class="sxs-lookup"><span data-stu-id="ab28d-107">[out] One of the values 1, 2, 4, 8, or 16, representing the pack size of the class.</span></span>  
  
 `rFieldOffset`  
 <span data-ttu-id="ab28d-108">[out] Uma matriz de [COR_FIELD_OFFSET](../../../../docs/framework/unmanaged-api/metadata/cor-field-offset-structure.md) valores.</span><span class="sxs-lookup"><span data-stu-id="ab28d-108">[out] An array of [COR_FIELD_OFFSET](../../../../docs/framework/unmanaged-api/metadata/cor-field-offset-structure.md) values.</span></span>  
  
 `cMax`  
 <span data-ttu-id="ab28d-109">[in] O tamanho máximo da `rFieldOffset` matriz.</span><span class="sxs-lookup"><span data-stu-id="ab28d-109">[in] The maximum size of the `rFieldOffset` array.</span></span>  
  
 `pcFieldOffset`  
 <span data-ttu-id="ab28d-110">[out] O número de elementos retornados em `rFieldOffset`.</span><span class="sxs-lookup"><span data-stu-id="ab28d-110">[out] The number of elements returned in `rFieldOffset`.</span></span>  
  
 `pulClassSize`  
 <span data-ttu-id="ab28d-111">[out] O tamanho em bytes da classe representada pelo `td`.</span><span class="sxs-lookup"><span data-stu-id="ab28d-111">[out] The size in bytes of the class represented by `td`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ab28d-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ab28d-112">Requirements</span></span>  
 <span data-ttu-id="ab28d-113">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ab28d-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ab28d-114">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="ab28d-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ab28d-115">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="ab28d-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ab28d-116">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ab28d-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab28d-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ab28d-117">See Also</span></span>  
 [<span data-ttu-id="ab28d-118">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="ab28d-118">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="ab28d-119">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="ab28d-119">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
