---
title: Método IMetaDataImport::EnumEvents
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumEvents
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumEvents
helpviewer_keywords:
- IMetaDataImport::EnumEvents method [.NET Framework metadata]
- EnumEvents method [.NET Framework metadata]
ms.assetid: e1efedcb-3dd7-42ae-a399-21c24728aec5
topic_type:
- apiref
ms.openlocfilehash: bd50d63b1f7080f510c29f90979b7b36242af1c0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177366"
---
# <a name="imetadataimportenumevents-method"></a><span data-ttu-id="52ea2-102">Método IMetaDataImport::EnumEvents</span><span class="sxs-lookup"><span data-stu-id="52ea2-102">IMetaDataImport::EnumEvents Method</span></span>
<span data-ttu-id="52ea2-103">Enumera tokens de definição de evento para o token TypeDef especificado.</span><span class="sxs-lookup"><span data-stu-id="52ea2-103">Enumerates event definition tokens for the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="52ea2-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="52ea2-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumEvents (
   [in, out] HCORENUM    *phEnum,
   [in]      mdTypeDef   td,
   [out]     mdEvent     rEvents[],
   [in]      ULONG       cMax,  
   [out]    ULONG        *pcEvents  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="52ea2-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="52ea2-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="52ea2-106">[dentro, fora] Um ponteiro para o enumerador.</span><span class="sxs-lookup"><span data-stu-id="52ea2-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `td`  
 <span data-ttu-id="52ea2-107">[em] O token TypeDef cujas definições de evento devem ser enumeradas.</span><span class="sxs-lookup"><span data-stu-id="52ea2-107">[in] The TypeDef token whose event definitions are to be enumerated.</span></span>  
  
 `rEvents`  
 <span data-ttu-id="52ea2-108">[fora] A matriz de eventos retornados.</span><span class="sxs-lookup"><span data-stu-id="52ea2-108">[out] The array of returned events.</span></span>  
  
 `cMax`  
 <span data-ttu-id="52ea2-109">[em] O tamanho máximo `rEvents` da matriz.</span><span class="sxs-lookup"><span data-stu-id="52ea2-109">[in] The maximum size of the `rEvents` array.</span></span>  
  
 `pcEvents`  
 <span data-ttu-id="52ea2-110">[fora] O número real de `rEvents`eventos retornou em .</span><span class="sxs-lookup"><span data-stu-id="52ea2-110">[out] The actual number of events returned in `rEvents`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="52ea2-111">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="52ea2-111">Return Value</span></span>  
  
|<span data-ttu-id="52ea2-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="52ea2-112">HRESULT</span></span>|<span data-ttu-id="52ea2-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="52ea2-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="52ea2-114">`EnumEvents`retornou com sucesso.</span><span class="sxs-lookup"><span data-stu-id="52ea2-114">`EnumEvents` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="52ea2-115">Não há eventos para enumerar.</span><span class="sxs-lookup"><span data-stu-id="52ea2-115">There are no events to enumerate.</span></span> <span data-ttu-id="52ea2-116">Nesse caso, `pcEvents` é zero.</span><span class="sxs-lookup"><span data-stu-id="52ea2-116">In that case, `pcEvents` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="52ea2-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="52ea2-117">Requirements</span></span>  
 <span data-ttu-id="52ea2-118">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="52ea2-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="52ea2-119">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="52ea2-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="52ea2-120">**Biblioteca:** Incluído como um recurso em MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="52ea2-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="52ea2-121">**.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="52ea2-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52ea2-122">Confira também</span><span class="sxs-lookup"><span data-stu-id="52ea2-122">See also</span></span>

- [<span data-ttu-id="52ea2-123">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="52ea2-123">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="52ea2-124">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="52ea2-124">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
