---
title: Método IMetaDataImport::EnumTypeRefs
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumTypeRefs
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumTypeRefs
helpviewer_keywords:
- EnumTypeRefs method [.NET Framework metadata]
- IMetaDataImport::EnumTypeRefs method [.NET Framework metadata]
ms.assetid: b4896b8f-8e97-469c-8089-e72a025661b5
topic_type:
- apiref
ms.openlocfilehash: 778ebf1d4fad0c8703964be88fdc3ff8c033bc28
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449987"
---
# <a name="imetadataimportenumtyperefs-method"></a><span data-ttu-id="307a3-102">Método IMetaDataImport::EnumTypeRefs</span><span class="sxs-lookup"><span data-stu-id="307a3-102">IMetaDataImport::EnumTypeRefs Method</span></span>
<span data-ttu-id="307a3-103">Enumera tokens TypeRef definidos no escopo de metadados atual.</span><span class="sxs-lookup"><span data-stu-id="307a3-103">Enumerates TypeRef tokens defined in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="307a3-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="307a3-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumTypeRefs (  
   [in, out] HCORENUM    *phEnum,   
   [out] mdTypeRef       rTypeRefs[],  
   [in]  ULONG           cMax,   
   [out] ULONG           *pcTypeRefs  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="307a3-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="307a3-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="307a3-106">[entrada, saída] Um ponteiro para o enumerador.</span><span class="sxs-lookup"><span data-stu-id="307a3-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="307a3-107">Isso deve ser nulo para a primeira chamada deste método.</span><span class="sxs-lookup"><span data-stu-id="307a3-107">This must be NULL for the first call of this method.</span></span>  
  
 `rTypeRefs`  
 <span data-ttu-id="307a3-108">fora A matriz usada para armazenar os tokens TypeRef.</span><span class="sxs-lookup"><span data-stu-id="307a3-108">[out] The array used to store the TypeRef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="307a3-109">no O tamanho máximo da matriz de `rTypeRefs`.</span><span class="sxs-lookup"><span data-stu-id="307a3-109">[in] The maximum size of the `rTypeRefs` array.</span></span>  
  
 `pcTypeRefs`  
 <span data-ttu-id="307a3-110">fora Um ponteiro para o número de tokens TypeRef retornado em `rTypeRefs`.</span><span class="sxs-lookup"><span data-stu-id="307a3-110">[out] A pointer to the number of TypeRef tokens returned in `rTypeRefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="307a3-111">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="307a3-111">Return Value</span></span>  
  
|<span data-ttu-id="307a3-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="307a3-112">HRESULT</span></span>|<span data-ttu-id="307a3-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="307a3-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="307a3-114">`EnumTypeRefs` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="307a3-114">`EnumTypeRefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="307a3-115">Não há tokens para enumerar.</span><span class="sxs-lookup"><span data-stu-id="307a3-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="307a3-116">Nesse caso, `pcTypeRefs` é zero.</span><span class="sxs-lookup"><span data-stu-id="307a3-116">In that case, `pcTypeRefs` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="307a3-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="307a3-117">Remarks</span></span>  
 <span data-ttu-id="307a3-118">Um token TypeRef representa uma referência a um tipo.</span><span class="sxs-lookup"><span data-stu-id="307a3-118">A TypeRef token represents a reference to a type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="307a3-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="307a3-119">Requirements</span></span>  
 <span data-ttu-id="307a3-120">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="307a3-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="307a3-121">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="307a3-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="307a3-122">**Biblioteca:** Incluído como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="307a3-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="307a3-123">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="307a3-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="307a3-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="307a3-124">See also</span></span>

- [<span data-ttu-id="307a3-125">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="307a3-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="307a3-126">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="307a3-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
