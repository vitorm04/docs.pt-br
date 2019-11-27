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
ms.openlocfilehash: 6e73160fb1927560ad381dbb85d03796296ba9a4
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74434296"
---
# <a name="imetadataemitgettokenfromtypespec-method"></a><span data-ttu-id="ef16b-102">Método IMetaDataEmit::GetTokenFromTypeSpec</span><span class="sxs-lookup"><span data-stu-id="ef16b-102">IMetaDataEmit::GetTokenFromTypeSpec Method</span></span>
<span data-ttu-id="ef16b-103">Obtém um token de metadados para o tipo com a assinatura de metadados especificada.</span><span class="sxs-lookup"><span data-stu-id="ef16b-103">Gets a metadata token for the type with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef16b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ef16b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTokenFromTypeSpec (   
    [in]  PCCOR_SIGNATURE       pvSig,   
    [in]  ULONG                 cbSig,   
    [out] mdTypeSpec            *ptypespec   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ef16b-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ef16b-105">Parameters</span></span>  
 `pvSig`  
 <span data-ttu-id="ef16b-106">no A assinatura que está sendo definida.</span><span class="sxs-lookup"><span data-stu-id="ef16b-106">[in] The signature being defined.</span></span>  
  
 `cbSig`  
 <span data-ttu-id="ef16b-107">no A contagem de bytes em `pvSig`.</span><span class="sxs-lookup"><span data-stu-id="ef16b-107">[in] The count of bytes in `pvSig`.</span></span>  
  
 `ptypespec`  
 <span data-ttu-id="ef16b-108">fora O token de `mdTypeSpec` atribuído.</span><span class="sxs-lookup"><span data-stu-id="ef16b-108">[out] The `mdTypeSpec` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ef16b-109">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="ef16b-109">Requirements</span></span>  
 <span data-ttu-id="ef16b-110">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ef16b-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ef16b-111">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="ef16b-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ef16b-112">**Biblioteca:** Usado como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="ef16b-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ef16b-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ef16b-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef16b-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ef16b-114">See also</span></span>

- [<span data-ttu-id="ef16b-115">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="ef16b-115">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="ef16b-116">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="ef16b-116">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
