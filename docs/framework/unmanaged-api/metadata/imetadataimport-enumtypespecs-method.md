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
ms.openlocfilehash: 42b8360ac6a7bb62f29046475d6cc98124619770
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449976"
---
# <a name="imetadataimportenumtypespecs-method"></a><span data-ttu-id="dee70-102">Método IMetaDataImport::EnumTypeSpecs</span><span class="sxs-lookup"><span data-stu-id="dee70-102">IMetaDataImport::EnumTypeSpecs Method</span></span>
<span data-ttu-id="dee70-103">Enumera os tokens de TypeSpec definidos no escopo de metadados atual.</span><span class="sxs-lookup"><span data-stu-id="dee70-103">Enumerates TypeSpec tokens defined in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dee70-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="dee70-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumTypeSpecs (  
   [in, out] HCORENUM    *phEnum,  
   [out] mdTypeSpec      rTypeSpecs[],  
   [in]  ULONG           cMax,  
   [out] ULONG           *pcTypeSpecs  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dee70-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="dee70-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="dee70-106">[entrada, saída] Um ponteiro para o enumerador.</span><span class="sxs-lookup"><span data-stu-id="dee70-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="dee70-107">Esse valor deve ser nulo para a primeira chamada deste método.</span><span class="sxs-lookup"><span data-stu-id="dee70-107">This value must be NULL for the first call of this method.</span></span>  
  
 `rTypeSpecs`  
 <span data-ttu-id="dee70-108">fora A matriz usada para armazenar os tokens de TypeSpec.</span><span class="sxs-lookup"><span data-stu-id="dee70-108">[out] The array used to store the TypeSpec tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="dee70-109">no O tamanho máximo da matriz de `rTypeSpecs`.</span><span class="sxs-lookup"><span data-stu-id="dee70-109">[in] The maximum size of the `rTypeSpecs` array.</span></span>  
  
 `pcTypeSpecs`  
 <span data-ttu-id="dee70-110">fora O número de tokens de TypeSpec retornado em `rTypeSpecs`.</span><span class="sxs-lookup"><span data-stu-id="dee70-110">[out] The number of TypeSpec tokens returned in `rTypeSpecs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="dee70-111">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="dee70-111">Return Value</span></span>  
  
|<span data-ttu-id="dee70-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="dee70-112">HRESULT</span></span>|<span data-ttu-id="dee70-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="dee70-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="dee70-114">`EnumTypeSpecs` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="dee70-114">`EnumTypeSpecs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="dee70-115">Não há tokens para enumerar.</span><span class="sxs-lookup"><span data-stu-id="dee70-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="dee70-116">Nesse caso, `pcTypeSpecs` é zero.</span><span class="sxs-lookup"><span data-stu-id="dee70-116">In that case, `pcTypeSpecs` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dee70-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="dee70-117">Remarks</span></span>  
 <span data-ttu-id="dee70-118">Os tokens TypeSpec são criados pelo método [IMetaDataEmit:: GetTokenFromTypeSpec](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromtypespec-method.md) .</span><span class="sxs-lookup"><span data-stu-id="dee70-118">The TypeSpec tokens are created by the [IMetaDataEmit::GetTokenFromTypeSpec](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromtypespec-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dee70-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="dee70-119">Requirements</span></span>  
 <span data-ttu-id="dee70-120">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dee70-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dee70-121">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="dee70-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="dee70-122">**Biblioteca:** Incluído como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="dee70-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="dee70-123">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dee70-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dee70-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dee70-124">See also</span></span>

- [<span data-ttu-id="dee70-125">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="dee70-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="dee70-126">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="dee70-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
