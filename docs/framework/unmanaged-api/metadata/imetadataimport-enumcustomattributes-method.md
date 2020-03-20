---
title: Método IMetaDataImport::EnumCustomAttributes
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumCustomAttributes
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumCustomAttributes
helpviewer_keywords:
- EnumCustomAttributes method [.NET Framework metadata]
- IMetaDataImport::EnumCustomAttributes method [.NET Framework metadata]
ms.assetid: 798513a0-68b1-4d04-bc5b-782a4445ea68
topic_type:
- apiref
ms.openlocfilehash: 61b5678a546bdbadbcc6d8ee86447cb17ce72b99
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175519"
---
# <a name="imetadataimportenumcustomattributes-method"></a><span data-ttu-id="2b525-102">Método IMetaDataImport::EnumCustomAttributes</span><span class="sxs-lookup"><span data-stu-id="2b525-102">IMetaDataImport::EnumCustomAttributes Method</span></span>
<span data-ttu-id="2b525-103">Enumera tokens personalizados de definição de atributos associados ao tipo ou membro especificado.</span><span class="sxs-lookup"><span data-stu-id="2b525-103">Enumerates custom attribute-definition tokens associated with the specified type or member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b525-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2b525-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumCustomAttributes (
   [in, out] HCORENUM      *phEnum,  
   [in]  mdToken            tk,
   [in]  mdToken            tkType,
   [out] mdCustomAttribute  rCustomAttributes[],
   [in]  ULONG              cMax,  
   [out, optional] ULONG   *pcCustomAttributes  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2b525-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="2b525-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="2b525-106">[dentro, fora] Um ponteiro para o enumerador retornado.</span><span class="sxs-lookup"><span data-stu-id="2b525-106">[in, out] A pointer to the returned enumerator.</span></span>  
  
 `tk`  
 <span data-ttu-id="2b525-107">[em] Um token para o escopo da enumeração, ou zero para todos os atributos personalizados.</span><span class="sxs-lookup"><span data-stu-id="2b525-107">[in] A token for the scope of the enumeration, or zero for all custom attributes.</span></span>  
  
 `tkType`  
 <span data-ttu-id="2b525-108">[em] Um token para o construtor do tipo de atributos `null` a serem enumerados, ou para todos os tipos.</span><span class="sxs-lookup"><span data-stu-id="2b525-108">[in] A token for the constructor of the type of the attributes to be enumerated, or `null` for all types.</span></span>  
  
 `rCustomAttributes`  
 <span data-ttu-id="2b525-109">[fora] Uma matriz de tokens de atributo personalizados.</span><span class="sxs-lookup"><span data-stu-id="2b525-109">[out] An array of custom attribute tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="2b525-110">[em] O tamanho máximo `rCustomAttributes` da matriz.</span><span class="sxs-lookup"><span data-stu-id="2b525-110">[in] The maximum size of the `rCustomAttributes` array.</span></span>  
  
 `pcCustomAttributes`  
 <span data-ttu-id="2b525-111">[fora, opcional] O número real de valores `rCustomAttributes`de token retornado em .</span><span class="sxs-lookup"><span data-stu-id="2b525-111">[out, optional] The actual number of token values returned in `rCustomAttributes`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2b525-112">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="2b525-112">Return Value</span></span>  
  
|<span data-ttu-id="2b525-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2b525-113">HRESULT</span></span>|<span data-ttu-id="2b525-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="2b525-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="2b525-115">`EnumCustomAttributes`retornou com sucesso.</span><span class="sxs-lookup"><span data-stu-id="2b525-115">`EnumCustomAttributes` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="2b525-116">Não há atributos personalizados para enumerar.</span><span class="sxs-lookup"><span data-stu-id="2b525-116">There are no custom attributes to enumerate.</span></span> <span data-ttu-id="2b525-117">Nesse caso, `pcCustomAttributes` é zero.</span><span class="sxs-lookup"><span data-stu-id="2b525-117">In that case, `pcCustomAttributes` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2b525-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2b525-118">Requirements</span></span>  
 <span data-ttu-id="2b525-119">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2b525-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2b525-120">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="2b525-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2b525-121">**Biblioteca:** Incluído como um recurso em MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2b525-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2b525-122">**.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2b525-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b525-123">Confira também</span><span class="sxs-lookup"><span data-stu-id="2b525-123">See also</span></span>

- [<span data-ttu-id="2b525-124">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="2b525-124">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="2b525-125">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="2b525-125">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
