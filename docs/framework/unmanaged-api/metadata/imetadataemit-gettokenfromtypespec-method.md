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
ms.openlocfilehash: b0b7d0364b6f58579ee8573d168d6c8180ac9dff
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33444571"
---
# <a name="imetadataemitgettokenfromtypespec-method"></a><span data-ttu-id="81c12-102">Método IMetaDataEmit::GetTokenFromTypeSpec</span><span class="sxs-lookup"><span data-stu-id="81c12-102">IMetaDataEmit::GetTokenFromTypeSpec Method</span></span>
<span data-ttu-id="81c12-103">Obtém os metadados de um token para o tipo com a assinatura de metadados especificado.</span><span class="sxs-lookup"><span data-stu-id="81c12-103">Gets a metadata token for the type with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81c12-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="81c12-104">Syntax</span></span>  
  
```  
HRESULT GetTokenFromTypeSpec (   
    [in]  PCCOR_SIGNATURE       pvSig,   
    [in]  ULONG                 cbSig,   
    [out] mdTypeSpec            *ptypespec   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="81c12-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="81c12-105">Parameters</span></span>  
 `pvSig`  
 <span data-ttu-id="81c12-106">[in] A assinatura está sendo definida.</span><span class="sxs-lookup"><span data-stu-id="81c12-106">[in] The signature being defined.</span></span>  
  
 `cbSig`  
 <span data-ttu-id="81c12-107">[in] A contagem de bytes em `pvSig`.</span><span class="sxs-lookup"><span data-stu-id="81c12-107">[in] The count of bytes in `pvSig`.</span></span>  
  
 `ptypespec`  
 <span data-ttu-id="81c12-108">[out] O `mdTypeSpec` token atribuído.</span><span class="sxs-lookup"><span data-stu-id="81c12-108">[out] The `mdTypeSpec` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="81c12-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="81c12-109">Requirements</span></span>  
 <span data-ttu-id="81c12-110">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="81c12-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="81c12-111">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="81c12-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="81c12-112">**Biblioteca:** usado como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="81c12-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="81c12-113">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="81c12-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81c12-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="81c12-114">See Also</span></span>  
 [<span data-ttu-id="81c12-115">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="81c12-115">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="81c12-116">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="81c12-116">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
