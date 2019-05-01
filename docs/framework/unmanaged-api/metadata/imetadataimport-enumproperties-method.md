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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 410fd7a702d3aa3812b4ea053c43fdaa507a474a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62042504"
---
# <a name="imetadataimportenumproperties-method"></a><span data-ttu-id="29a10-102">Método IMetaDataImport::EnumProperties</span><span class="sxs-lookup"><span data-stu-id="29a10-102">IMetaDataImport::EnumProperties Method</span></span>
<span data-ttu-id="29a10-103">Enumera os tokens de PropertyDef que representa as propriedades do tipo referenciado pelo token de TypeDef especificado.</span><span class="sxs-lookup"><span data-stu-id="29a10-103">Enumerates PropertyDef tokens representing the properties of the type referenced by the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29a10-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="29a10-104">Syntax</span></span>  
  
```  
HRESULT EnumProperties (  
   [in, out] HCORENUM    *phEnum,  
   [in]      mdTypeDef   td,  
   [out]     mdProperty  rProperties[],  
   [in]      ULONG       cMax,  
   [out]     ULONG       *pcProperties  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="29a10-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="29a10-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="29a10-106">[no, out] Um ponteiro para o enumerador.</span><span class="sxs-lookup"><span data-stu-id="29a10-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="29a10-107">Isso deve ser NULL para a primeira chamada desse método.</span><span class="sxs-lookup"><span data-stu-id="29a10-107">This must be NULL for the first call of this method.</span></span>  
  
 `td`  
 <span data-ttu-id="29a10-108">[in] Um token de TypeDef que representa o tipo com propriedades para enumerar.</span><span class="sxs-lookup"><span data-stu-id="29a10-108">[in] A TypeDef token representing the type with properties to enumerate.</span></span>  
  
 `rProperties`  
 <span data-ttu-id="29a10-109">[out] A matriz usada para armazenar os tokens de PropertyDef.</span><span class="sxs-lookup"><span data-stu-id="29a10-109">[out] The array used to store the PropertyDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="29a10-110">[in] O tamanho máximo da `rProperties` matriz.</span><span class="sxs-lookup"><span data-stu-id="29a10-110">[in] The maximum size of the `rProperties` array.</span></span>  
  
 `pcProperties`  
 <span data-ttu-id="29a10-111">[out] O número de tokens PropertyDef retornado no `rProperties`.</span><span class="sxs-lookup"><span data-stu-id="29a10-111">[out] The number of PropertyDef tokens returned in `rProperties`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="29a10-112">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="29a10-112">Return Value</span></span>  
  
|<span data-ttu-id="29a10-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="29a10-113">HRESULT</span></span>|<span data-ttu-id="29a10-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="29a10-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="29a10-115">`EnumProperties` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="29a10-115">`EnumProperties` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="29a10-116">Não há nenhum token para enumerar.</span><span class="sxs-lookup"><span data-stu-id="29a10-116">There are no tokens to enumerate.</span></span> <span data-ttu-id="29a10-117">Nesse caso, `pcProperties` é zero.</span><span class="sxs-lookup"><span data-stu-id="29a10-117">In that case, `pcProperties` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="29a10-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="29a10-118">Requirements</span></span>  
 <span data-ttu-id="29a10-119">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="29a10-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="29a10-120">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="29a10-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="29a10-121">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="29a10-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="29a10-122">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="29a10-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29a10-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="29a10-123">See also</span></span>

- [<span data-ttu-id="29a10-124">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="29a10-124">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="29a10-125">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="29a10-125">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
