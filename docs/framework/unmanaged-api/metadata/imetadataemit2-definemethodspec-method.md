---
title: Método IMetaDataEmit2::DefineMethodSpec
ms.date: 03/30/2017
api_name:
- IMetaDataEmit2.DefineMethodSpec
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit2::DefineMethodSpec
helpviewer_keywords:
- DefineMethodSpec method [.NET Framework metadata]
- IMetaDataEmit2::DefineMethodSpec method [.NET Framework metadata]
ms.assetid: 3c24e552-fc69-4971-b65a-a3e4b5f7f1e8
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a4185ec41fc9f7d1d919a79b57c02625210ad72a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777184"
---
# <a name="imetadataemit2definemethodspec-method"></a><span data-ttu-id="f93c0-102">Método IMetaDataEmit2::DefineMethodSpec</span><span class="sxs-lookup"><span data-stu-id="f93c0-102">IMetaDataEmit2::DefineMethodSpec Method</span></span>
<span data-ttu-id="f93c0-103">Cria uma instância genérica de um método e obtém um token para a definição.</span><span class="sxs-lookup"><span data-stu-id="f93c0-103">Creates a generic instance of a method, and gets a token to the definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f93c0-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f93c0-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineMethodSpec (  
    [in]  mdToken           tkParent,   
    [in]  PCCOR_SIGNATURE   pvSigBlob,   
    [in]  ULONG             cbSigBlob,   
    [out] mdMethodSpec      *pmi  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f93c0-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f93c0-105">Parameters</span></span>  
 `tkParent`  
 <span data-ttu-id="f93c0-106">[in] Um token para o método do qual criar a instância genérica.</span><span class="sxs-lookup"><span data-stu-id="f93c0-106">[in] A token for the method of which to create the generic instance.</span></span> <span data-ttu-id="f93c0-107">O token deve ser do tipo `mdMethodDef` ou `mdMemberRef`.</span><span class="sxs-lookup"><span data-stu-id="f93c0-107">The token must be of type `mdMethodDef` or `mdMemberRef`.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="f93c0-108">[in] Um ponteiro para o binário COM + assinatura do método.</span><span class="sxs-lookup"><span data-stu-id="f93c0-108">[in] A pointer to the binary COM+ signature of the method.</span></span>  
  
 `cbSibBlob`  
 <span data-ttu-id="f93c0-109">[in] O tamanho, em bytes, do `pvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="f93c0-109">[in] The size, in bytes, of `pvSigBlob`.</span></span>  
  
 `pmi`  
 <span data-ttu-id="f93c0-110">[out] Um token para a definição de metadados de assinatura do método.</span><span class="sxs-lookup"><span data-stu-id="f93c0-110">[out] A token to the metadata signature definition of the method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f93c0-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f93c0-111">Requirements</span></span>  
 <span data-ttu-id="f93c0-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f93c0-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f93c0-113">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="f93c0-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f93c0-114">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="f93c0-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f93c0-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f93c0-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f93c0-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f93c0-116">See also</span></span>

- [<span data-ttu-id="f93c0-117">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="f93c0-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [<span data-ttu-id="f93c0-118">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="f93c0-118">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
