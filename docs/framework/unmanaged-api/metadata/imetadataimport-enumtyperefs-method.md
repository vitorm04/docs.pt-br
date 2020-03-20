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
ms.openlocfilehash: e5d4ddd43b27d733a63c2e0dc5e92ffd2ba94a7f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175428"
---
# <a name="imetadataimportenumtyperefs-method"></a><span data-ttu-id="67d08-102">Método IMetaDataImport::EnumTypeRefs</span><span class="sxs-lookup"><span data-stu-id="67d08-102">IMetaDataImport::EnumTypeRefs Method</span></span>
<span data-ttu-id="67d08-103">Enumera tokens TypeRef definidos no escopo de metadados atuais.</span><span class="sxs-lookup"><span data-stu-id="67d08-103">Enumerates TypeRef tokens defined in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="67d08-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="67d08-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumTypeRefs (  
   [in, out] HCORENUM    *phEnum,
   [out] mdTypeRef       rTypeRefs[],  
   [in]  ULONG           cMax,
   [out] ULONG           *pcTypeRefs  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="67d08-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="67d08-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="67d08-106">[dentro, fora] Um ponteiro para o enumerador.</span><span class="sxs-lookup"><span data-stu-id="67d08-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="67d08-107">Isto deve ser NULO para a primeira chamada deste método.</span><span class="sxs-lookup"><span data-stu-id="67d08-107">This must be NULL for the first call of this method.</span></span>  
  
 `rTypeRefs`  
 <span data-ttu-id="67d08-108">[fora] A matriz usada para armazenar os tokens TypeRef.</span><span class="sxs-lookup"><span data-stu-id="67d08-108">[out] The array used to store the TypeRef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="67d08-109">[em] O tamanho máximo `rTypeRefs` da matriz.</span><span class="sxs-lookup"><span data-stu-id="67d08-109">[in] The maximum size of the `rTypeRefs` array.</span></span>  
  
 `pcTypeRefs`  
 <span data-ttu-id="67d08-110">[fora] Um ponteiro para o número de tokens TypeRef retornado em `rTypeRefs`.</span><span class="sxs-lookup"><span data-stu-id="67d08-110">[out] A pointer to the number of TypeRef tokens returned in `rTypeRefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="67d08-111">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="67d08-111">Return Value</span></span>  
  
|<span data-ttu-id="67d08-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="67d08-112">HRESULT</span></span>|<span data-ttu-id="67d08-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="67d08-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="67d08-114">`EnumTypeRefs`retornou com sucesso.</span><span class="sxs-lookup"><span data-stu-id="67d08-114">`EnumTypeRefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="67d08-115">Não há tokens para enumerar.</span><span class="sxs-lookup"><span data-stu-id="67d08-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="67d08-116">Nesse caso, `pcTypeRefs` é zero.</span><span class="sxs-lookup"><span data-stu-id="67d08-116">In that case, `pcTypeRefs` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="67d08-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="67d08-117">Remarks</span></span>  
 <span data-ttu-id="67d08-118">Um token TypeRef representa uma referência a um tipo.</span><span class="sxs-lookup"><span data-stu-id="67d08-118">A TypeRef token represents a reference to a type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="67d08-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="67d08-119">Requirements</span></span>  
 <span data-ttu-id="67d08-120">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="67d08-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="67d08-121">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="67d08-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="67d08-122">**Biblioteca:** Incluído como um recurso em MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="67d08-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="67d08-123">**.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="67d08-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67d08-124">Confira também</span><span class="sxs-lookup"><span data-stu-id="67d08-124">See also</span></span>

- [<span data-ttu-id="67d08-125">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="67d08-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="67d08-126">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="67d08-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
