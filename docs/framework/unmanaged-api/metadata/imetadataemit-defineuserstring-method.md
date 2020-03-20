---
title: Método IMetaDataEmit::DefineUserString
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineUserString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineUserString
helpviewer_keywords:
- DefineUserString method [.NET Framework metadata]
- IMetaDataEmit::DefineUserString method [.NET Framework metadata]
ms.assetid: 88fb7ef3-bbdf-429c-b678-c9c153456461
topic_type:
- apiref
ms.openlocfilehash: a71d8694ec8c5bd35ecd3e98ed32e05bc7b382fc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177614"
---
# <a name="imetadataemitdefineuserstring-method"></a><span data-ttu-id="f82c6-102">Método IMetaDataEmit::DefineUserString</span><span class="sxs-lookup"><span data-stu-id="f82c6-102">IMetaDataEmit::DefineUserString Method</span></span>
<span data-ttu-id="f82c6-103">Obtém um token de metadados para a seqüência literal especificada.</span><span class="sxs-lookup"><span data-stu-id="f82c6-103">Gets a metadata token for the specified literal string.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f82c6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f82c6-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineUserString (
    [in]  LPCWSTR     szString,
    [in]  ULONG       cchString,
    [out] mdString    *pstk
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f82c6-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="f82c6-105">Parameters</span></span>  
 `szString`  
 <span data-ttu-id="f82c6-106">[em] A seqüência de usuário para armazenar.</span><span class="sxs-lookup"><span data-stu-id="f82c6-106">[in] The user string to store.</span></span>  
  
 `cchString`  
 <span data-ttu-id="f82c6-107">[em] A contagem de `szString`personagens largos em .</span><span class="sxs-lookup"><span data-stu-id="f82c6-107">[in] The count of wide characters in `szString`.</span></span>  
  
 `pstk`  
 <span data-ttu-id="f82c6-108">[fora] O token de string atribuído.</span><span class="sxs-lookup"><span data-stu-id="f82c6-108">[out] The string token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f82c6-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f82c6-109">Requirements</span></span>  
 <span data-ttu-id="f82c6-110">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f82c6-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f82c6-111">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="f82c6-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f82c6-112">**Biblioteca:** Usado como recurso em MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f82c6-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f82c6-113">**.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f82c6-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f82c6-114">Confira também</span><span class="sxs-lookup"><span data-stu-id="f82c6-114">See also</span></span>

- [<span data-ttu-id="f82c6-115">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="f82c6-115">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="f82c6-116">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="f82c6-116">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
