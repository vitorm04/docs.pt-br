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
ms.openlocfilehash: adf3c74526bbf2b8e740f505ab6f4243cd799041
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57474573"
---
# <a name="imetadataemitdefinecustomattribute-method"></a><span data-ttu-id="4a3e1-102">Método IMetaDataEmit::DefineCustomAttribute</span><span class="sxs-lookup"><span data-stu-id="4a3e1-102">IMetaDataEmit::DefineCustomAttribute Method</span></span>
<span data-ttu-id="4a3e1-103">Cria uma definição para um atributo personalizado com a assinatura de metadados especificado, a ser anexado ao objeto especificado e obtém um token a definição desse atributo personalizado.</span><span class="sxs-lookup"><span data-stu-id="4a3e1-103">Creates a definition for a custom attribute with the specified metadata signature, to be attached to the specified object, and gets a token to that custom attribute definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a3e1-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4a3e1-104">Syntax</span></span>  
  
```  
HRESULT DefineCustomAttribute (   
    [in]  mdToken     tkObj,   
    [in]  mdToken     tkType,   
    [in]  void const  *pCustomAttribute,   
    [in]  ULONG       cbCustomAttribute,   
    [out] mdCustomAttribute *pcv   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4a3e1-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="4a3e1-105">Parameters</span></span>  
 `tkObj`  
 <span data-ttu-id="4a3e1-106">[in] O token para o item do proprietário.</span><span class="sxs-lookup"><span data-stu-id="4a3e1-106">[in] The token for the owner item.</span></span>  
  
 `tkType`  
 <span data-ttu-id="4a3e1-107">[in] O token que identifica o atributo personalizado.</span><span class="sxs-lookup"><span data-stu-id="4a3e1-107">[in] The token that identifies the custom attribute.</span></span>  
  
 `pCustomAttribute`  
 <span data-ttu-id="4a3e1-108">[in] Um ponteiro para o atributo personalizado.</span><span class="sxs-lookup"><span data-stu-id="4a3e1-108">[in] A pointer to the custom attribute.</span></span>  
  
 `cbCustomAttribute`  
 <span data-ttu-id="4a3e1-109">[in] A contagem de bytes em `pCustomAttribute`.</span><span class="sxs-lookup"><span data-stu-id="4a3e1-109">[in] The count of bytes in `pCustomAttribute`.</span></span>  
  
 `pcv`  
 <span data-ttu-id="4a3e1-110">[out] O `mdCustomAttribute` token atribuído.</span><span class="sxs-lookup"><span data-stu-id="4a3e1-110">[out] The `mdCustomAttribute` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4a3e1-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4a3e1-111">Requirements</span></span>  
 <span data-ttu-id="4a3e1-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4a3e1-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4a3e1-113">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="4a3e1-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4a3e1-114">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="4a3e1-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4a3e1-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4a3e1-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a3e1-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4a3e1-116">See also</span></span>
- [<span data-ttu-id="4a3e1-117">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="4a3e1-117">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="4a3e1-118">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="4a3e1-118">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
