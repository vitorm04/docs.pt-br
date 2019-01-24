---
title: Método IMetaDataImport::EnumTypeSpecs
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7a4273b36ce3e761348a091df3acb41212e1df05
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54722309"
---
# <a name="imetadataimportenumtypespecs-method"></a><span data-ttu-id="bc0cc-102">Método IMetaDataImport::EnumTypeSpecs</span><span class="sxs-lookup"><span data-stu-id="bc0cc-102">IMetaDataImport::EnumTypeSpecs Method</span></span>
<span data-ttu-id="bc0cc-103">Enumera os tokens de TypeSpec definidos no escopo atual de metadados.</span><span class="sxs-lookup"><span data-stu-id="bc0cc-103">Enumerates TypeSpec tokens defined in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc0cc-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bc0cc-104">Syntax</span></span>  
  
```  
HRESULT EnumTypeSpecs (  
   [in, out] HCORENUM    *phEnum,  
   [out] mdTypeSpec      rTypeSpecs[],  
   [in]  ULONG           cMax,  
   [out] ULONG           *pcTypeSpecs  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bc0cc-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="bc0cc-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="bc0cc-106">[no, out] Um ponteiro para o enumerador.</span><span class="sxs-lookup"><span data-stu-id="bc0cc-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="bc0cc-107">Esse valor deve ser NULL para a primeira chamada desse método.</span><span class="sxs-lookup"><span data-stu-id="bc0cc-107">This value must be NULL for the first call of this method.</span></span>  
  
 `rTypeSpecs`  
 <span data-ttu-id="bc0cc-108">[out] A matriz usada para armazenar os tokens de TypeSpec.</span><span class="sxs-lookup"><span data-stu-id="bc0cc-108">[out] The array used to store the TypeSpec tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="bc0cc-109">[in] O tamanho máximo da `rTypeSpecs` matriz.</span><span class="sxs-lookup"><span data-stu-id="bc0cc-109">[in] The maximum size of the `rTypeSpecs` array.</span></span>  
  
 `pcTypeSpecs`  
 <span data-ttu-id="bc0cc-110">[out] O número de tokens de TypeSpec retornado no `rTypeSpecs`.</span><span class="sxs-lookup"><span data-stu-id="bc0cc-110">[out] The number of TypeSpec tokens returned in `rTypeSpecs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bc0cc-111">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="bc0cc-111">Return Value</span></span>  
  
|<span data-ttu-id="bc0cc-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="bc0cc-112">HRESULT</span></span>|<span data-ttu-id="bc0cc-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="bc0cc-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="bc0cc-114">`EnumTypeSpecs` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="bc0cc-114">`EnumTypeSpecs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="bc0cc-115">Não há nenhum token para enumerar.</span><span class="sxs-lookup"><span data-stu-id="bc0cc-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="bc0cc-116">Nesse caso, `pcTypeSpecs` é zero.</span><span class="sxs-lookup"><span data-stu-id="bc0cc-116">In that case, `pcTypeSpecs` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bc0cc-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="bc0cc-117">Remarks</span></span>  
 <span data-ttu-id="bc0cc-118">Os tokens de TypeSpec são criados pela [imetadataemit:: Gettokenfromtypespec](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromtypespec-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="bc0cc-118">The TypeSpec tokens are created by the [IMetaDataEmit::GetTokenFromTypeSpec](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromtypespec-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bc0cc-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="bc0cc-119">Requirements</span></span>  
 <span data-ttu-id="bc0cc-120">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bc0cc-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bc0cc-121">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="bc0cc-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="bc0cc-122">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="bc0cc-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="bc0cc-123">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bc0cc-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc0cc-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bc0cc-124">See also</span></span>
- [<span data-ttu-id="bc0cc-125">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="bc0cc-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="bc0cc-126">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="bc0cc-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
