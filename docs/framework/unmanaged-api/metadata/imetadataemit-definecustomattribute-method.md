---
title: Método IMetaDataEmit::DefineCustomAttribute
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineCustomAttribute
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineCustomAttribute
helpviewer_keywords:
- DefineCustomAttribute method [.NET Framework metadata]
- IMetaDataEmit::DefineCustomAttribute method [.NET Framework metadata]
ms.assetid: 7dd14854-b756-4401-b167-88ca576dc8f0
topic_type:
- apiref
ms.openlocfilehash: 9c4ed282e259aa46fc0cb0175214dc51d3d5fbee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175883"
---
# <a name="imetadataemitdefinecustomattribute-method"></a><span data-ttu-id="5b4b4-102">Método IMetaDataEmit::DefineCustomAttribute</span><span class="sxs-lookup"><span data-stu-id="5b4b4-102">IMetaDataEmit::DefineCustomAttribute Method</span></span>
<span data-ttu-id="5b4b4-103">Cria uma definição para um atributo personalizado com a assinatura de metadados especificada, a ser anexada ao objeto especificado e obtém um token para essa definição de atributo personalizado.</span><span class="sxs-lookup"><span data-stu-id="5b4b4-103">Creates a definition for a custom attribute with the specified metadata signature, to be attached to the specified object, and gets a token to that custom attribute definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5b4b4-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5b4b4-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineCustomAttribute (
    [in]  mdToken     tkObj,
    [in]  mdToken     tkType,
    [in]  void const  *pCustomAttribute,
    [in]  ULONG       cbCustomAttribute,
    [out] mdCustomAttribute *pcv
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5b4b4-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="5b4b4-105">Parameters</span></span>  
 `tkObj`  
 <span data-ttu-id="5b4b4-106">[em] O token para o item do proprietário.</span><span class="sxs-lookup"><span data-stu-id="5b4b4-106">[in] The token for the owner item.</span></span>  
  
 `tkType`  
 <span data-ttu-id="5b4b4-107">[em] O token que identifica o atributo personalizado.</span><span class="sxs-lookup"><span data-stu-id="5b4b4-107">[in] The token that identifies the custom attribute.</span></span>  
  
 `pCustomAttribute`  
 <span data-ttu-id="5b4b4-108">[em] Um ponteiro para o atributo personalizado.</span><span class="sxs-lookup"><span data-stu-id="5b4b4-108">[in] A pointer to the custom attribute.</span></span>  
  
 `cbCustomAttribute`  
 <span data-ttu-id="5b4b4-109">[em] A contagem de `pCustomAttribute`bytes em .</span><span class="sxs-lookup"><span data-stu-id="5b4b4-109">[in] The count of bytes in `pCustomAttribute`.</span></span>  
  
 `pcv`  
 <span data-ttu-id="5b4b4-110">[fora] O `mdCustomAttribute` token atribuído.</span><span class="sxs-lookup"><span data-stu-id="5b4b4-110">[out] The `mdCustomAttribute` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5b4b4-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5b4b4-111">Requirements</span></span>  
 <span data-ttu-id="5b4b4-112">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5b4b4-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5b4b4-113">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="5b4b4-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5b4b4-114">**Biblioteca:** Usado como recurso em MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="5b4b4-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5b4b4-115">**.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5b4b4-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b4b4-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="5b4b4-116">See also</span></span>

- [<span data-ttu-id="5b4b4-117">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="5b4b4-117">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="5b4b4-118">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="5b4b4-118">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
