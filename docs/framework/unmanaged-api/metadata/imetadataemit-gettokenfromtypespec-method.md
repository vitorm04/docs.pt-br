---
title: Método IMetaDataEmit::GetTokenFromTypeSpec
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.GetTokenFromTypeSpec
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::GetTokenFromTypeSpec
helpviewer_keywords:
- GetTokenFromTypeSpec method [.NET Framework metadata]
- IMetaDataEmit::GetTokenFromTypeSpec method [.NET Framework metadata]
ms.assetid: 7de6447a-a751-49d8-87e2-951cee77b536
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ff240a80d2910dcb050cc022257c6eba166bbdc5
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57465927"
---
# <a name="imetadataemitgettokenfromtypespec-method"></a><span data-ttu-id="ca5d7-102">Método IMetaDataEmit::GetTokenFromTypeSpec</span><span class="sxs-lookup"><span data-stu-id="ca5d7-102">IMetaDataEmit::GetTokenFromTypeSpec Method</span></span>
<span data-ttu-id="ca5d7-103">Obtém os metadados de um token para o tipo com a assinatura de metadados especificado.</span><span class="sxs-lookup"><span data-stu-id="ca5d7-103">Gets a metadata token for the type with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca5d7-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ca5d7-104">Syntax</span></span>  
  
```  
HRESULT GetTokenFromTypeSpec (   
    [in]  PCCOR_SIGNATURE       pvSig,   
    [in]  ULONG                 cbSig,   
    [out] mdTypeSpec            *ptypespec   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ca5d7-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ca5d7-105">Parameters</span></span>  
 `pvSig`  
 <span data-ttu-id="ca5d7-106">[in] A assinatura que está sendo definida.</span><span class="sxs-lookup"><span data-stu-id="ca5d7-106">[in] The signature being defined.</span></span>  
  
 `cbSig`  
 <span data-ttu-id="ca5d7-107">[in] A contagem de bytes em `pvSig`.</span><span class="sxs-lookup"><span data-stu-id="ca5d7-107">[in] The count of bytes in `pvSig`.</span></span>  
  
 `ptypespec`  
 <span data-ttu-id="ca5d7-108">[out] O `mdTypeSpec` token atribuído.</span><span class="sxs-lookup"><span data-stu-id="ca5d7-108">[out] The `mdTypeSpec` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ca5d7-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ca5d7-109">Requirements</span></span>  
 <span data-ttu-id="ca5d7-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ca5d7-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ca5d7-111">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="ca5d7-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ca5d7-112">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="ca5d7-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ca5d7-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ca5d7-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca5d7-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ca5d7-114">See also</span></span>
- [<span data-ttu-id="ca5d7-115">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="ca5d7-115">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="ca5d7-116">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="ca5d7-116">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
