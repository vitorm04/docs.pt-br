---
title: Método IMetaDataImport::EnumProperties
ms.date: 03/30/2017
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
ms.openlocfilehash: 4fed7dbe4ec8343a3854d1f277e3228b14c0bf21
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450017"
---
# <a name="imetadataimportenumproperties-method"></a><span data-ttu-id="38768-102">Método IMetaDataImport::EnumProperties</span><span class="sxs-lookup"><span data-stu-id="38768-102">IMetaDataImport::EnumProperties Method</span></span>
<span data-ttu-id="38768-103">Enumera os tokens PropertyDef que representam as propriedades do tipo referenciado pelo token de TypeDef especificado.</span><span class="sxs-lookup"><span data-stu-id="38768-103">Enumerates PropertyDef tokens representing the properties of the type referenced by the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38768-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="38768-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumProperties (  
   [in, out] HCORENUM    *phEnum,  
   [in]      mdTypeDef   td,  
   [out]     mdProperty  rProperties[],  
   [in]      ULONG       cMax,  
   [out]     ULONG       *pcProperties  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="38768-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="38768-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="38768-106">[entrada, saída] Um ponteiro para o enumerador.</span><span class="sxs-lookup"><span data-stu-id="38768-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="38768-107">Isso deve ser nulo para a primeira chamada deste método.</span><span class="sxs-lookup"><span data-stu-id="38768-107">This must be NULL for the first call of this method.</span></span>  
  
 `td`  
 <span data-ttu-id="38768-108">no Um token de TypeDef que representa o tipo com propriedades a serem enumeradas.</span><span class="sxs-lookup"><span data-stu-id="38768-108">[in] A TypeDef token representing the type with properties to enumerate.</span></span>  
  
 `rProperties`  
 <span data-ttu-id="38768-109">fora A matriz usada para armazenar os tokens PropertyDef.</span><span class="sxs-lookup"><span data-stu-id="38768-109">[out] The array used to store the PropertyDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="38768-110">no O tamanho máximo da matriz de `rProperties`.</span><span class="sxs-lookup"><span data-stu-id="38768-110">[in] The maximum size of the `rProperties` array.</span></span>  
  
 `pcProperties`  
 <span data-ttu-id="38768-111">fora O número de tokens PropertyDef retornados em `rProperties`.</span><span class="sxs-lookup"><span data-stu-id="38768-111">[out] The number of PropertyDef tokens returned in `rProperties`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="38768-112">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="38768-112">Return Value</span></span>  
  
|<span data-ttu-id="38768-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="38768-113">HRESULT</span></span>|<span data-ttu-id="38768-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="38768-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="38768-115">`EnumProperties` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="38768-115">`EnumProperties` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="38768-116">Não há tokens para enumerar.</span><span class="sxs-lookup"><span data-stu-id="38768-116">There are no tokens to enumerate.</span></span> <span data-ttu-id="38768-117">Nesse caso, `pcProperties` é zero.</span><span class="sxs-lookup"><span data-stu-id="38768-117">In that case, `pcProperties` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="38768-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="38768-118">Requirements</span></span>  
 <span data-ttu-id="38768-119">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="38768-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="38768-120">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="38768-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="38768-121">**Biblioteca:** Incluído como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="38768-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="38768-122">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="38768-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38768-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="38768-123">See also</span></span>

- [<span data-ttu-id="38768-124">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="38768-124">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="38768-125">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="38768-125">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
