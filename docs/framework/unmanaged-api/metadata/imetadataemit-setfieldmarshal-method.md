---
title: Método IMetaDataEmit::SetFieldMarshal
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetFieldMarshal
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetFieldMarshal
helpviewer_keywords:
- SetFieldMarshal method [.NET Framework metadata]
- IMetaDataEmit::SetFieldMarshal method [.NET Framework metadata]
ms.assetid: be232314-7f69-4855-bfab-63361bd22307
topic_type:
- apiref
ms.openlocfilehash: 1037cd4210605192870d43d88979b89af6536380
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175649"
---
# <a name="imetadataemitsetfieldmarshal-method"></a><span data-ttu-id="25772-102">Método IMetaDataEmit::SetFieldMarshal</span><span class="sxs-lookup"><span data-stu-id="25772-102">IMetaDataEmit::SetFieldMarshal Method</span></span>
<span data-ttu-id="25772-103">Define as informações de empacotamento do PInvoke para o campo, o retorno do método ou o parâmetro do método referenciado pelo token especificado.</span><span class="sxs-lookup"><span data-stu-id="25772-103">Sets the PInvoke marshaling information for the field, method return, or method parameter referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25772-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="25772-104">Syntax</span></span>  
  
```cpp  
HRESULT SetFieldMarshal (  
    [in]  mdToken          tk,
    [in]  PCCOR_SIGNATURE  pvNativeType,
    [in]  ULONG            cbNativeType
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="25772-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="25772-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="25772-106">[em] O token para o item de dados de destino.</span><span class="sxs-lookup"><span data-stu-id="25772-106">[in] The token for target data item.</span></span> <span data-ttu-id="25772-107">Isso é `mdFieldDef` um `mdParamDef` ou um símbolo.</span><span class="sxs-lookup"><span data-stu-id="25772-107">This is either a `mdFieldDef` or a `mdParamDef` token.</span></span>  
  
 `pvNativeType`  
 <span data-ttu-id="25772-108">[em] A assinatura para o tipo não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="25772-108">[in] The signature for unmanaged type.</span></span>  
  
 `cbNativeType`  
 <span data-ttu-id="25772-109">[em] A contagem de `pvNativeType`bytes em .</span><span class="sxs-lookup"><span data-stu-id="25772-109">[in] The count of bytes in `pvNativeType`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="25772-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="25772-110">Requirements</span></span>  
 <span data-ttu-id="25772-111">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="25772-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="25772-112">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="25772-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="25772-113">**Biblioteca:** Usado como recurso em MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="25772-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="25772-114">**.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="25772-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25772-115">Confira também</span><span class="sxs-lookup"><span data-stu-id="25772-115">See also</span></span>

- [<span data-ttu-id="25772-116">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="25772-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="25772-117">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="25772-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
