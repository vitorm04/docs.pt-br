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
ms.openlocfilehash: 94b4c3935c949c0c4008e41244713b6bfa4dba84
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503712"
---
# <a name="imetadataimportenumtypespecs-method"></a><span data-ttu-id="b9ed4-102">Método IMetaDataImport::EnumTypeSpecs</span><span class="sxs-lookup"><span data-stu-id="b9ed4-102">IMetaDataImport::EnumTypeSpecs Method</span></span>
<span data-ttu-id="b9ed4-103">Enumera os tokens de TypeSpec definidos no escopo de metadados atual.</span><span class="sxs-lookup"><span data-stu-id="b9ed4-103">Enumerates TypeSpec tokens defined in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b9ed4-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b9ed4-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumTypeSpecs (  
   [in, out] HCORENUM    *phEnum,  
   [out] mdTypeSpec      rTypeSpecs[],  
   [in]  ULONG           cMax,  
   [out] ULONG           *pcTypeSpecs  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b9ed4-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b9ed4-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="b9ed4-106">[entrada, saída] Um ponteiro para o enumerador.</span><span class="sxs-lookup"><span data-stu-id="b9ed4-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="b9ed4-107">Esse valor deve ser nulo para a primeira chamada deste método.</span><span class="sxs-lookup"><span data-stu-id="b9ed4-107">This value must be NULL for the first call of this method.</span></span>  
  
 `rTypeSpecs`  
 <span data-ttu-id="b9ed4-108">fora A matriz usada para armazenar os tokens de TypeSpec.</span><span class="sxs-lookup"><span data-stu-id="b9ed4-108">[out] The array used to store the TypeSpec tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="b9ed4-109">no O tamanho máximo da `rTypeSpecs` matriz.</span><span class="sxs-lookup"><span data-stu-id="b9ed4-109">[in] The maximum size of the `rTypeSpecs` array.</span></span>  
  
 `pcTypeSpecs`  
 <span data-ttu-id="b9ed4-110">fora O número de tokens TypeSpec retornados em `rTypeSpecs` .</span><span class="sxs-lookup"><span data-stu-id="b9ed4-110">[out] The number of TypeSpec tokens returned in `rTypeSpecs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b9ed4-111">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="b9ed4-111">Return Value</span></span>  
  
|<span data-ttu-id="b9ed4-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b9ed4-112">HRESULT</span></span>|<span data-ttu-id="b9ed4-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="b9ed4-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="b9ed4-114">`EnumTypeSpecs`retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="b9ed4-114">`EnumTypeSpecs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="b9ed4-115">Não há tokens para enumerar.</span><span class="sxs-lookup"><span data-stu-id="b9ed4-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="b9ed4-116">Nesse caso, `pcTypeSpecs` é zero.</span><span class="sxs-lookup"><span data-stu-id="b9ed4-116">In that case, `pcTypeSpecs` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b9ed4-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="b9ed4-117">Remarks</span></span>  
 <span data-ttu-id="b9ed4-118">Os tokens TypeSpec são criados pelo método [IMetaDataEmit:: GetTokenFromTypeSpec](imetadataemit-gettokenfromtypespec-method.md) .</span><span class="sxs-lookup"><span data-stu-id="b9ed4-118">The TypeSpec tokens are created by the [IMetaDataEmit::GetTokenFromTypeSpec](imetadataemit-gettokenfromtypespec-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b9ed4-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b9ed4-119">Requirements</span></span>  
 <span data-ttu-id="b9ed4-120">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b9ed4-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b9ed4-121">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="b9ed4-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b9ed4-122">**Biblioteca:** Incluído como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="b9ed4-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b9ed4-123">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b9ed4-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9ed4-124">Confira também</span><span class="sxs-lookup"><span data-stu-id="b9ed4-124">See also</span></span>

- [<span data-ttu-id="b9ed4-125">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="b9ed4-125">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="b9ed4-126">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="b9ed4-126">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
