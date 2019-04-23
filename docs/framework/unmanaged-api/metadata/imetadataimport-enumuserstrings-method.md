---
title: Método IMetaDataImport::EnumUserStrings
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumUserStrings
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumUserStrings
helpviewer_keywords:
- IMetaDataImport::EnumUserStrings method [.NET Framework metadata]
- EnumUserStrings method [.NET Framework metadata]
ms.assetid: 2b1f1418-4be8-4cdb-b418-b3abccc527a7
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f4be12e46851b11a5e6db60c351094a356fa61f2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59082939"
---
# <a name="imetadataimportenumuserstrings-method"></a><span data-ttu-id="25733-102">Método IMetaDataImport::EnumUserStrings</span><span class="sxs-lookup"><span data-stu-id="25733-102">IMetaDataImport::EnumUserStrings Method</span></span>
<span data-ttu-id="25733-103">Enumera os tokens de cadeia de caracteres que representa cadeias de caracteres codificadas no escopo atual de metadados.</span><span class="sxs-lookup"><span data-stu-id="25733-103">Enumerates String tokens representing hard-coded strings in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25733-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="25733-104">Syntax</span></span>  
  
```  
HRESULT EnumUserStrings (  
   [in, out]  HCORENUM    *phEnum,  
   [out]  mdString        rStrings[],  
   [in]   ULONG           cMax,  
   [out]  ULONG           *pcStrings  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="25733-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="25733-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="25733-106">[no, out] Um ponteiro para o enumerador.</span><span class="sxs-lookup"><span data-stu-id="25733-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="25733-107">Isso deve ser NULL para a primeira chamada desse método.</span><span class="sxs-lookup"><span data-stu-id="25733-107">This must be NULL for the first call of this method.</span></span>  
  
 `rStrings`  
 <span data-ttu-id="25733-108">[out] A matriz usada para armazenar os tokens de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="25733-108">[out] The array used to store the String tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="25733-109">[in] O tamanho máximo da `rStrings` matriz.</span><span class="sxs-lookup"><span data-stu-id="25733-109">[in] The maximum size of the `rStrings` array.</span></span>  
  
 `pcStrings`  
 <span data-ttu-id="25733-110">[out] O número de tokens de cadeia de caracteres retornada no `rStrings`.</span><span class="sxs-lookup"><span data-stu-id="25733-110">[out] The number of String tokens returned in `rStrings`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="25733-111">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="25733-111">Return Value</span></span>  
  
|<span data-ttu-id="25733-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="25733-112">HRESULT</span></span>|<span data-ttu-id="25733-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="25733-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="25733-114">`EnumUserStrings` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="25733-114">`EnumUserStrings` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="25733-115">Não há nenhum token para enumerar.</span><span class="sxs-lookup"><span data-stu-id="25733-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="25733-116">Nesse caso, `pcStrings` é zero.</span><span class="sxs-lookup"><span data-stu-id="25733-116">In that case, `pcStrings` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="25733-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="25733-117">Remarks</span></span>  
 <span data-ttu-id="25733-118">Os tokens de cadeia de caracteres são criados pela [imetadataemit:: Defineuserstring](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineuserstring-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="25733-118">The String tokens are created by the [IMetaDataEmit::DefineUserString](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineuserstring-method.md) method.</span></span> <span data-ttu-id="25733-119">Esse método é projetado para ser usado por um navegador de metadados em vez de um compilador.</span><span class="sxs-lookup"><span data-stu-id="25733-119">This method is designed to be used by a metadata browser rather than by a compiler.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="25733-120">Requisitos</span><span class="sxs-lookup"><span data-stu-id="25733-120">Requirements</span></span>  
 <span data-ttu-id="25733-121">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="25733-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="25733-122">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="25733-122">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="25733-123">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="25733-123">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="25733-124">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="25733-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25733-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="25733-125">See also</span></span>

- [<span data-ttu-id="25733-126">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="25733-126">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="25733-127">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="25733-127">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
