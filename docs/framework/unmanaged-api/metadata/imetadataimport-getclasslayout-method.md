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
ms.openlocfilehash: e02d7dd4b287d027b633ae9bf2e98e036062bdd0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175402"
---
# <a name="imetadataimportgetclasslayout-method"></a><span data-ttu-id="ce5ad-102">Método IMetaDataImport::GetClassLayout</span><span class="sxs-lookup"><span data-stu-id="ce5ad-102">IMetaDataImport::GetClassLayout Method</span></span>
<span data-ttu-id="ce5ad-103">Obtém informações de layout para a classe referenciada pelo token TypeDef especificado.</span><span class="sxs-lookup"><span data-stu-id="ce5ad-103">Gets layout information for the class referenced by the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce5ad-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ce5ad-104">Syntax</span></span>  
  
```cpp  
HRESULT GetClassLayout  (
   [in]  mdTypeDef          td,
   [out] DWORD              *pdwPackSize,  
   [out] COR_FIELD_OFFSET   rFieldOffset[],  
   [in]  ULONG              cMax,  
   [out] ULONG              *pcFieldOffset,  
   [out] ULONG              *pulClassSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ce5ad-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="ce5ad-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="ce5ad-106">[em] O token TypeDef para a classe com o layout a retornar.</span><span class="sxs-lookup"><span data-stu-id="ce5ad-106">[in] The TypeDef token for the class with the layout to return.</span></span>  
  
 `pdwPackSize`  
 <span data-ttu-id="ce5ad-107">[fora] Um dos valores 1, 2, 4, 8 ou 16, representando o tamanho do pacote da classe.</span><span class="sxs-lookup"><span data-stu-id="ce5ad-107">[out] One of the values 1, 2, 4, 8, or 16, representing the pack size of the class.</span></span>  
  
 `rFieldOffset`  
 <span data-ttu-id="ce5ad-108">[fora] Uma matriz de valores [COR_FIELD_OFFSET.](../../../../docs/framework/unmanaged-api/metadata/cor-field-offset-structure.md)</span><span class="sxs-lookup"><span data-stu-id="ce5ad-108">[out] An array of [COR_FIELD_OFFSET](../../../../docs/framework/unmanaged-api/metadata/cor-field-offset-structure.md) values.</span></span>  
  
 `cMax`  
 <span data-ttu-id="ce5ad-109">[em] O tamanho máximo `rFieldOffset` da matriz.</span><span class="sxs-lookup"><span data-stu-id="ce5ad-109">[in] The maximum size of the `rFieldOffset` array.</span></span>  
  
 `pcFieldOffset`  
 <span data-ttu-id="ce5ad-110">[fora] O número de elementos retornados em `rFieldOffset`.</span><span class="sxs-lookup"><span data-stu-id="ce5ad-110">[out] The number of elements returned in `rFieldOffset`.</span></span>  
  
 `pulClassSize`  
 <span data-ttu-id="ce5ad-111">[fora] O tamanho em bytes da `td`classe representada por .</span><span class="sxs-lookup"><span data-stu-id="ce5ad-111">[out] The size in bytes of the class represented by `td`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ce5ad-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ce5ad-112">Requirements</span></span>  
 <span data-ttu-id="ce5ad-113">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ce5ad-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ce5ad-114">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="ce5ad-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ce5ad-115">**Biblioteca:** Incluído como um recurso em MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ce5ad-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ce5ad-116">**.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ce5ad-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce5ad-117">Confira também</span><span class="sxs-lookup"><span data-stu-id="ce5ad-117">See also</span></span>

- [<span data-ttu-id="ce5ad-118">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="ce5ad-118">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="ce5ad-119">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="ce5ad-119">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
