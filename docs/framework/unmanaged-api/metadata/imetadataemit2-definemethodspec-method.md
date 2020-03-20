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
ms.openlocfilehash: a5d9342b8bfe650106ccf9daf2a91dfbcd575446
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175532"
---
# <a name="imetadataemit2definemethodspec-method"></a><span data-ttu-id="a99c8-102">Método IMetaDataEmit2::DefineMethodSpec</span><span class="sxs-lookup"><span data-stu-id="a99c8-102">IMetaDataEmit2::DefineMethodSpec Method</span></span>
<span data-ttu-id="a99c8-103">Cria uma instância genérica de um método e obtém um token para a definição.</span><span class="sxs-lookup"><span data-stu-id="a99c8-103">Creates a generic instance of a method, and gets a token to the definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a99c8-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a99c8-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineMethodSpec (  
    [in]  mdToken           tkParent,
    [in]  PCCOR_SIGNATURE   pvSigBlob,
    [in]  ULONG             cbSigBlob,
    [out] mdMethodSpec      *pmi  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a99c8-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="a99c8-105">Parameters</span></span>  
 `tkParent`  
 <span data-ttu-id="a99c8-106">[em] Um token para o método de criar a instância genérica.</span><span class="sxs-lookup"><span data-stu-id="a99c8-106">[in] A token for the method of which to create the generic instance.</span></span> <span data-ttu-id="a99c8-107">O token deve `mdMethodDef` ser `mdMemberRef`do tipo ou .</span><span class="sxs-lookup"><span data-stu-id="a99c8-107">The token must be of type `mdMethodDef` or `mdMemberRef`.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="a99c8-108">[em] Um ponteiro para a assinatura binária COM+ do método.</span><span class="sxs-lookup"><span data-stu-id="a99c8-108">[in] A pointer to the binary COM+ signature of the method.</span></span>  
  
 `cbSibBlob`  
 <span data-ttu-id="a99c8-109">[em] O tamanho, em bytes, de `pvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="a99c8-109">[in] The size, in bytes, of `pvSigBlob`.</span></span>  
  
 `pmi`  
 <span data-ttu-id="a99c8-110">[fora] Um token para a definição de assinatura de metadados do método.</span><span class="sxs-lookup"><span data-stu-id="a99c8-110">[out] A token to the metadata signature definition of the method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a99c8-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a99c8-111">Requirements</span></span>  
 <span data-ttu-id="a99c8-112">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a99c8-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a99c8-113">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="a99c8-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a99c8-114">**Biblioteca:** Usado como recurso em MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a99c8-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a99c8-115">**.NET Framework Versions:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a99c8-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a99c8-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="a99c8-116">See also</span></span>

- [<span data-ttu-id="a99c8-117">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="a99c8-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [<span data-ttu-id="a99c8-118">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="a99c8-118">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
