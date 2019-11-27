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
ms.openlocfilehash: 8360a74e9e18e5b68ecc9edd7be2e3a711cb61c9
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74437773"
---
# <a name="imetadataimportgetclasslayout-method"></a><span data-ttu-id="65de3-102">Método IMetaDataImport::GetClassLayout</span><span class="sxs-lookup"><span data-stu-id="65de3-102">IMetaDataImport::GetClassLayout Method</span></span>
<span data-ttu-id="65de3-103">Obtém informações de layout para a classe referenciada pelo token de TypeDef especificado.</span><span class="sxs-lookup"><span data-stu-id="65de3-103">Gets layout information for the class referenced by the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65de3-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="65de3-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="65de3-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="65de3-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="65de3-106">no O token de TypeDef para a classe com o layout a ser retornado.</span><span class="sxs-lookup"><span data-stu-id="65de3-106">[in] The TypeDef token for the class with the layout to return.</span></span>  
  
 `pdwPackSize`  
 <span data-ttu-id="65de3-107">fora Um dos valores 1, 2, 4, 8 ou 16, que representa o tamanho do pacote da classe.</span><span class="sxs-lookup"><span data-stu-id="65de3-107">[out] One of the values 1, 2, 4, 8, or 16, representing the pack size of the class.</span></span>  
  
 `rFieldOffset`  
 <span data-ttu-id="65de3-108">fora Uma matriz de valores de [COR_FIELD_OFFSET](../../../../docs/framework/unmanaged-api/metadata/cor-field-offset-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="65de3-108">[out] An array of [COR_FIELD_OFFSET](../../../../docs/framework/unmanaged-api/metadata/cor-field-offset-structure.md) values.</span></span>  
  
 `cMax`  
 <span data-ttu-id="65de3-109">no O tamanho máximo da matriz de `rFieldOffset`.</span><span class="sxs-lookup"><span data-stu-id="65de3-109">[in] The maximum size of the `rFieldOffset` array.</span></span>  
  
 `pcFieldOffset`  
 <span data-ttu-id="65de3-110">fora O número de elementos retornados em `rFieldOffset`.</span><span class="sxs-lookup"><span data-stu-id="65de3-110">[out] The number of elements returned in `rFieldOffset`.</span></span>  
  
 `pulClassSize`  
 <span data-ttu-id="65de3-111">fora O tamanho em bytes da classe representada por `td`.</span><span class="sxs-lookup"><span data-stu-id="65de3-111">[out] The size in bytes of the class represented by `td`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="65de3-112">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="65de3-112">Requirements</span></span>  
 <span data-ttu-id="65de3-113">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="65de3-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="65de3-114">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="65de3-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="65de3-115">**Biblioteca:** Incluído como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="65de3-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="65de3-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="65de3-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65de3-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="65de3-117">See also</span></span>

- [<span data-ttu-id="65de3-118">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="65de3-118">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="65de3-119">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="65de3-119">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
