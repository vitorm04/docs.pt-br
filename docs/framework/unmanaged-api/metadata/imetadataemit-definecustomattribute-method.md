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
ms.openlocfilehash: 17757df566ba8d141e7adec00dcc1f75959d0e00
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84005618"
---
# <a name="imetadataemitdefinecustomattribute-method"></a><span data-ttu-id="4e245-102">Método IMetaDataEmit::DefineCustomAttribute</span><span class="sxs-lookup"><span data-stu-id="4e245-102">IMetaDataEmit::DefineCustomAttribute Method</span></span>
<span data-ttu-id="4e245-103">Cria uma definição para um atributo personalizado com a assinatura de metadados especificada, a ser anexada ao objeto especificado e Obtém um token para essa definição de atributo personalizado.</span><span class="sxs-lookup"><span data-stu-id="4e245-103">Creates a definition for a custom attribute with the specified metadata signature, to be attached to the specified object, and gets a token to that custom attribute definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4e245-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4e245-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineCustomAttribute (
    [in]  mdToken     tkObj,
    [in]  mdToken     tkType,
    [in]  void const  *pCustomAttribute,
    [in]  ULONG       cbCustomAttribute,
    [out] mdCustomAttribute *pcv
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4e245-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="4e245-105">Parameters</span></span>  
 `tkObj`  
 <span data-ttu-id="4e245-106">no O token para o item de proprietário.</span><span class="sxs-lookup"><span data-stu-id="4e245-106">[in] The token for the owner item.</span></span>  
  
 `tkType`  
 <span data-ttu-id="4e245-107">no O token que identifica o atributo personalizado.</span><span class="sxs-lookup"><span data-stu-id="4e245-107">[in] The token that identifies the custom attribute.</span></span>  
  
 `pCustomAttribute`  
 <span data-ttu-id="4e245-108">no Um ponteiro para o atributo personalizado.</span><span class="sxs-lookup"><span data-stu-id="4e245-108">[in] A pointer to the custom attribute.</span></span>  
  
 `cbCustomAttribute`  
 <span data-ttu-id="4e245-109">no A contagem de bytes em `pCustomAttribute` .</span><span class="sxs-lookup"><span data-stu-id="4e245-109">[in] The count of bytes in `pCustomAttribute`.</span></span>  
  
 `pcv`  
 <span data-ttu-id="4e245-110">fora O `mdCustomAttribute` token atribuído.</span><span class="sxs-lookup"><span data-stu-id="4e245-110">[out] The `mdCustomAttribute` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4e245-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4e245-111">Requirements</span></span>  
 <span data-ttu-id="4e245-112">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4e245-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4e245-113">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="4e245-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4e245-114">**Biblioteca:** Usado como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="4e245-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4e245-115">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4e245-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e245-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="4e245-116">See also</span></span>

- [<span data-ttu-id="4e245-117">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="4e245-117">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="4e245-118">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="4e245-118">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
