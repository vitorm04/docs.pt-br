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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: de0fe4a51fbb49e80377b6b434bf3b72ddb90f02
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59081613"
---
# <a name="imetadataimportenumtyperefs-method"></a><span data-ttu-id="02253-102">Método IMetaDataImport::EnumTypeRefs</span><span class="sxs-lookup"><span data-stu-id="02253-102">IMetaDataImport::EnumTypeRefs Method</span></span>
<span data-ttu-id="02253-103">Enumera os tokens TypeRef definidos no escopo atual de metadados.</span><span class="sxs-lookup"><span data-stu-id="02253-103">Enumerates TypeRef tokens defined in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="02253-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="02253-104">Syntax</span></span>  
  
```  
HRESULT EnumTypeRefs (  
   [in, out] HCORENUM    *phEnum,   
   [out] mdTypeRef       rTypeRefs[],  
   [in]  ULONG           cMax,   
   [out] ULONG           *pcTypeRefs  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="02253-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="02253-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="02253-106">[no, out] Um ponteiro para o enumerador.</span><span class="sxs-lookup"><span data-stu-id="02253-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="02253-107">Isso deve ser NULL para a primeira chamada desse método.</span><span class="sxs-lookup"><span data-stu-id="02253-107">This must be NULL for the first call of this method.</span></span>  
  
 `rTypeRefs`  
 <span data-ttu-id="02253-108">[out] A matriz usada para armazenar os tokens TypeRef.</span><span class="sxs-lookup"><span data-stu-id="02253-108">[out] The array used to store the TypeRef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="02253-109">[in] O tamanho máximo da `rTypeRefs` matriz.</span><span class="sxs-lookup"><span data-stu-id="02253-109">[in] The maximum size of the `rTypeRefs` array.</span></span>  
  
 `pcTypeRefs`  
 <span data-ttu-id="02253-110">[out] Um ponteiro para o número de tokens TypeRef retornado no `rTypeRefs`.</span><span class="sxs-lookup"><span data-stu-id="02253-110">[out] A pointer to the number of TypeRef tokens returned in `rTypeRefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="02253-111">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="02253-111">Return Value</span></span>  
  
|<span data-ttu-id="02253-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="02253-112">HRESULT</span></span>|<span data-ttu-id="02253-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="02253-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="02253-114">`EnumTypeRefs` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="02253-114">`EnumTypeRefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="02253-115">Não há nenhum token para enumerar.</span><span class="sxs-lookup"><span data-stu-id="02253-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="02253-116">Nesse caso, `pcTypeRefs` é zero.</span><span class="sxs-lookup"><span data-stu-id="02253-116">In that case, `pcTypeRefs` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="02253-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="02253-117">Remarks</span></span>  
 <span data-ttu-id="02253-118">Um token TypeRef representa uma referência a um tipo.</span><span class="sxs-lookup"><span data-stu-id="02253-118">A TypeRef token represents a reference to a type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="02253-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="02253-119">Requirements</span></span>  
 <span data-ttu-id="02253-120">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="02253-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="02253-121">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="02253-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="02253-122">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="02253-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="02253-123">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="02253-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02253-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="02253-124">See also</span></span>

- [<span data-ttu-id="02253-125">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="02253-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="02253-126">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="02253-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
