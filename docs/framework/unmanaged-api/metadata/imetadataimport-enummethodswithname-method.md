---
title: Método IMetaDataImport::EnumMethodsWithName
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumMethodsWithName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumMethodsWithName
helpviewer_keywords:
- IMetaDataImport::EnumMethodsWithName method [.NET Framework metadata]
- EnumMethodsWithName method [.NET Framework metadata]
ms.assetid: a8624913-2e23-46ad-a0c1-bb8eccbbf20f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f15ee906fb20cb60272cee3deffa68dbe852f689
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59200175"
---
# <a name="imetadataimportenummethodswithname-method"></a><span data-ttu-id="fbf77-102">Método IMetaDataImport::EnumMethodsWithName</span><span class="sxs-lookup"><span data-stu-id="fbf77-102">IMetaDataImport::EnumMethodsWithName Method</span></span>
<span data-ttu-id="fbf77-103">Enumera métodos que têm o nome especificado e que são definidos pelo tipo referenciado pelo token de TypeDef especificado.</span><span class="sxs-lookup"><span data-stu-id="fbf77-103">Enumerates methods that have the specified name and that are defined by the type referenced by the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fbf77-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fbf77-104">Syntax</span></span>  
  
```  
HRESULT EnumMethodsWithName (  
   [in, out] HCORENUM    *phEnum,  
   [in]  mdTypeDef       cl,  
   [in]  LPCWSTR         szName,  
   [out] mdMethodDef     rMethods[],  
   [in]  ULONG           cMax,  
   [out] ULONG           *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fbf77-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="fbf77-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="fbf77-106">[no, out] Um ponteiro para o enumerador.</span><span class="sxs-lookup"><span data-stu-id="fbf77-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="fbf77-107">Isso deve ser NULL para a primeira chamada desse método.</span><span class="sxs-lookup"><span data-stu-id="fbf77-107">This must be NULL for the first call of this method.</span></span>  
  
 `cl`  
 <span data-ttu-id="fbf77-108">[in] Um token de TypeDef que representa o tipo cujos métodos para enumerar.</span><span class="sxs-lookup"><span data-stu-id="fbf77-108">[in] A TypeDef token representing the type whose methods to enumerate.</span></span>  
  
 `szName`  
 <span data-ttu-id="fbf77-109">[in] O nome que limita o escopo da enumeração.</span><span class="sxs-lookup"><span data-stu-id="fbf77-109">[in] The name that limits the scope of the enumeration.</span></span>  
  
 `rMethods`  
 <span data-ttu-id="fbf77-110">[out] A matriz usada para armazenar os tokens MethodDef.</span><span class="sxs-lookup"><span data-stu-id="fbf77-110">[out] The array used to store the MethodDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="fbf77-111">[in] O tamanho máximo da `rMethods` matriz.</span><span class="sxs-lookup"><span data-stu-id="fbf77-111">[in] The maximum size of the `rMethods` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="fbf77-112">[out] O número de tokens MethodDef retornado no `rMethods`.</span><span class="sxs-lookup"><span data-stu-id="fbf77-112">[out] The number of MethodDef tokens returned in `rMethods`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fbf77-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="fbf77-113">Remarks</span></span>  
 <span data-ttu-id="fbf77-114">Esse método enumera os campos e métodos, mas não as propriedades ou eventos.</span><span class="sxs-lookup"><span data-stu-id="fbf77-114">This method enumerates fields and methods, but not properties or events.</span></span> <span data-ttu-id="fbf77-115">Diferentemente [imetadataimport:: Enummethods](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummethods-method.md), `EnumMethodsWithName` descarta todos os tokens de método que não têm o nome especificado.</span><span class="sxs-lookup"><span data-stu-id="fbf77-115">Unlike [IMetaDataImport::EnumMethods](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummethods-method.md), `EnumMethodsWithName` discards all method tokens that do not have the specified name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fbf77-116">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="fbf77-116">Return Value</span></span>  
  
|<span data-ttu-id="fbf77-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="fbf77-117">HRESULT</span></span>|<span data-ttu-id="fbf77-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="fbf77-118">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|`EnumMethodsWithName` <span data-ttu-id="fbf77-119">retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="fbf77-119">returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="fbf77-120">Não há nenhum token para enumerar.</span><span class="sxs-lookup"><span data-stu-id="fbf77-120">There are no tokens to enumerate.</span></span> <span data-ttu-id="fbf77-121">Nesse caso, `pcTokens` é zero.</span><span class="sxs-lookup"><span data-stu-id="fbf77-121">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="fbf77-122">Requisitos</span><span class="sxs-lookup"><span data-stu-id="fbf77-122">Requirements</span></span>  
 <span data-ttu-id="fbf77-123">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fbf77-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fbf77-124">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="fbf77-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="fbf77-125">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="fbf77-125">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="fbf77-126">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="fbf77-126">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="fbf77-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fbf77-127">See also</span></span>

- [<span data-ttu-id="fbf77-128">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="fbf77-128">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="fbf77-129">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="fbf77-129">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
