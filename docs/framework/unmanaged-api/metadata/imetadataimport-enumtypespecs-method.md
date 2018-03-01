---
title: "Método IMetaDataImport::EnumTypeSpecs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IMetaDataImport.EnumTypeSpecs
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumTypeSpecs
helpviewer_keywords:
- EnumTypeSpecs method [.NET Framework metadata]
- IMetaDataImport::EnumTypeSpecs method [.NET Framework metadata]
ms.assetid: 75331c7b-988b-436c-9eb9-a270d37b4f06
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9e34a3086474918c913a366c02bbf9eadf313b43
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportenumtypespecs-method"></a><span data-ttu-id="67fa1-102">Método IMetaDataImport::EnumTypeSpecs</span><span class="sxs-lookup"><span data-stu-id="67fa1-102">IMetaDataImport::EnumTypeSpecs Method</span></span>
<span data-ttu-id="67fa1-103">Enumera os tokens de TypeSpec definidos no escopo atual de metadados.</span><span class="sxs-lookup"><span data-stu-id="67fa1-103">Enumerates TypeSpec tokens defined in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="67fa1-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="67fa1-104">Syntax</span></span>  
  
```  
HRESULT EnumTypeSpecs (  
   [in, out] HCORENUM    *phEnum,  
   [out] mdTypeSpec      rTypeSpecs[],  
   [in]  ULONG           cMax,  
   [out] ULONG           *pcTypeSpecs  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="67fa1-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="67fa1-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="67fa1-106">[out no] Um ponteiro para o enumerador.</span><span class="sxs-lookup"><span data-stu-id="67fa1-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="67fa1-107">Esse valor deve ser NULL para a primeira chamada do método.</span><span class="sxs-lookup"><span data-stu-id="67fa1-107">This value must be NULL for the first call of this method.</span></span>  
  
 `rTypeSpecs`  
 <span data-ttu-id="67fa1-108">[out] A matriz usada para armazenar os tokens TypeSpec.</span><span class="sxs-lookup"><span data-stu-id="67fa1-108">[out] The array used to store the TypeSpec tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="67fa1-109">[in] O tamanho máximo da `rTypeSpecs` matriz.</span><span class="sxs-lookup"><span data-stu-id="67fa1-109">[in] The maximum size of the `rTypeSpecs` array.</span></span>  
  
 `pcTypeSpecs`  
 <span data-ttu-id="67fa1-110">[out] O número de tokens TypeSpec retornados em `rTypeSpecs`.</span><span class="sxs-lookup"><span data-stu-id="67fa1-110">[out] The number of TypeSpec tokens returned in `rTypeSpecs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="67fa1-111">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="67fa1-111">Return Value</span></span>  
  
|<span data-ttu-id="67fa1-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="67fa1-112">HRESULT</span></span>|<span data-ttu-id="67fa1-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="67fa1-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="67fa1-114">`EnumTypeSpecs`retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="67fa1-114">`EnumTypeSpecs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="67fa1-115">Não há nenhum tokens para enumerar.</span><span class="sxs-lookup"><span data-stu-id="67fa1-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="67fa1-116">Nesse caso, `pcTypeSpecs` é zero.</span><span class="sxs-lookup"><span data-stu-id="67fa1-116">In that case, `pcTypeSpecs` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="67fa1-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="67fa1-117">Remarks</span></span>  
 <span data-ttu-id="67fa1-118">Os tokens de TypeSpec são criados pelo [: Gettokenfromtypespec](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromtypespec-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="67fa1-118">The TypeSpec tokens are created by the [IMetaDataEmit::GetTokenFromTypeSpec](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromtypespec-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="67fa1-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="67fa1-119">Requirements</span></span>  
 <span data-ttu-id="67fa1-120">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="67fa1-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="67fa1-121">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="67fa1-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="67fa1-122">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="67fa1-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="67fa1-123">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="67fa1-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67fa1-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="67fa1-124">See Also</span></span>  
 [<span data-ttu-id="67fa1-125">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="67fa1-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="67fa1-126">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="67fa1-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
