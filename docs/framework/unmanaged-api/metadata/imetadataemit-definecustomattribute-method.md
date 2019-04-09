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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 52190583338f1c1ee9183a98d5f4a6cd7236342d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59075649"
---
# <a name="imetadataemitdefinecustomattribute-method"></a><span data-ttu-id="8bc2d-102">Método IMetaDataEmit::DefineCustomAttribute</span><span class="sxs-lookup"><span data-stu-id="8bc2d-102">IMetaDataEmit::DefineCustomAttribute Method</span></span>
<span data-ttu-id="8bc2d-103">Cria uma definição para um atributo personalizado com a assinatura de metadados especificado, a ser anexado ao objeto especificado e obtém um token a definição desse atributo personalizado.</span><span class="sxs-lookup"><span data-stu-id="8bc2d-103">Creates a definition for a custom attribute with the specified metadata signature, to be attached to the specified object, and gets a token to that custom attribute definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8bc2d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8bc2d-104">Syntax</span></span>  
  
```  
HRESULT DefineCustomAttribute (   
    [in]  mdToken     tkObj,   
    [in]  mdToken     tkType,   
    [in]  void const  *pCustomAttribute,   
    [in]  ULONG       cbCustomAttribute,   
    [out] mdCustomAttribute *pcv   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8bc2d-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8bc2d-105">Parameters</span></span>  
 `tkObj`  
 <span data-ttu-id="8bc2d-106">[in] O token para o item do proprietário.</span><span class="sxs-lookup"><span data-stu-id="8bc2d-106">[in] The token for the owner item.</span></span>  
  
 `tkType`  
 <span data-ttu-id="8bc2d-107">[in] O token que identifica o atributo personalizado.</span><span class="sxs-lookup"><span data-stu-id="8bc2d-107">[in] The token that identifies the custom attribute.</span></span>  
  
 `pCustomAttribute`  
 <span data-ttu-id="8bc2d-108">[in] Um ponteiro para o atributo personalizado.</span><span class="sxs-lookup"><span data-stu-id="8bc2d-108">[in] A pointer to the custom attribute.</span></span>  
  
 `cbCustomAttribute`  
 <span data-ttu-id="8bc2d-109">[in] A contagem de bytes em `pCustomAttribute`.</span><span class="sxs-lookup"><span data-stu-id="8bc2d-109">[in] The count of bytes in `pCustomAttribute`.</span></span>  
  
 `pcv`  
 <span data-ttu-id="8bc2d-110">[out] O `mdCustomAttribute` token atribuído.</span><span class="sxs-lookup"><span data-stu-id="8bc2d-110">[out] The `mdCustomAttribute` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8bc2d-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8bc2d-111">Requirements</span></span>  
 <span data-ttu-id="8bc2d-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8bc2d-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8bc2d-113">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="8bc2d-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8bc2d-114">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="8bc2d-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="8bc2d-115">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="8bc2d-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="8bc2d-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8bc2d-116">See also</span></span>

- [<span data-ttu-id="8bc2d-117">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="8bc2d-117">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="8bc2d-118">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="8bc2d-118">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
