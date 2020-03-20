---
title: Método IMetaDataAssemblyImport::EnumAssemblyRefs
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.EnumAssemblyRefs
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::EnumAssemblyRefs
helpviewer_keywords:
- IMetaDataAssemblyImport::EnumAssemblyRefs method [.NET Framework metadata]
- EnumAssemblyRefs method [.NET Framework metadata]
ms.assetid: 8844d0dd-730e-4592-8a7b-c1462d312c70
topic_type:
- apiref
ms.openlocfilehash: 6a4489d094974eb872b39824ceb185b0cbe48625
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177821"
---
# <a name="imetadataassemblyimportenumassemblyrefs-method"></a><span data-ttu-id="e6979-102">Método IMetaDataAssemblyImport::EnumAssemblyRefs</span><span class="sxs-lookup"><span data-stu-id="e6979-102">IMetaDataAssemblyImport::EnumAssemblyRefs Method</span></span>
<span data-ttu-id="e6979-103">Enumera as `mdAssemblyRef` instâncias definidas no manifesto de montagem.</span><span class="sxs-lookup"><span data-stu-id="e6979-103">Enumerates the `mdAssemblyRef` instances that are defined in the assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6979-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e6979-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumAssemblyRefs (  
    [in, out] HCORENUM        *phEnum,
    [out]     mdAssemblyRef   rAssemblyRefs[],
    [in]      ULONG           cMax,
    [out]     ULONG           *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e6979-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="e6979-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="e6979-106">[dentro, fora] Um ponteiro para o enumerador.</span><span class="sxs-lookup"><span data-stu-id="e6979-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="e6979-107">Este deve ser um `EnumAssemblyRefs` valor nulo quando o método é chamado pela primeira vez.</span><span class="sxs-lookup"><span data-stu-id="e6979-107">This must be a null value when the `EnumAssemblyRefs` method is called for the first time.</span></span>  
  
 `rAssemblyRefs`  
 <span data-ttu-id="e6979-108">[fora] A enumeração `mdAssemblyRef` de tokens de metadados.</span><span class="sxs-lookup"><span data-stu-id="e6979-108">[out] The enumeration of `mdAssemblyRef` metadata tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="e6979-109">[em] O número máximo de tokens que `rAssemblyRefs` podem ser colocados na matriz.</span><span class="sxs-lookup"><span data-stu-id="e6979-109">[in] The maximum number of tokens that can be placed in the `rAssemblyRefs` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="e6979-110">[fora] O número de tokens `rAssemblyRefs`realmente colocados em .</span><span class="sxs-lookup"><span data-stu-id="e6979-110">[out] The number of tokens actually placed in `rAssemblyRefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e6979-111">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="e6979-111">Return Value</span></span>  
  
|<span data-ttu-id="e6979-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e6979-112">HRESULT</span></span>|<span data-ttu-id="e6979-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="e6979-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="e6979-114">`EnumAssemblyRefs`retornou com sucesso.</span><span class="sxs-lookup"><span data-stu-id="e6979-114">`EnumAssemblyRefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="e6979-115">Não há tokens para enumerar.</span><span class="sxs-lookup"><span data-stu-id="e6979-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="e6979-116">Neste caso, `pcTokens` está definido como zero.</span><span class="sxs-lookup"><span data-stu-id="e6979-116">In this case, `pcTokens` is set to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e6979-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e6979-117">Requirements</span></span>  
 <span data-ttu-id="e6979-118">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e6979-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e6979-119">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="e6979-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e6979-120">**Biblioteca:** Usado como recurso em MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e6979-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e6979-121">**.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e6979-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6979-122">Confira também</span><span class="sxs-lookup"><span data-stu-id="e6979-122">See also</span></span>

- [<span data-ttu-id="e6979-123">Interface IMetaDataAssemblyImport</span><span class="sxs-lookup"><span data-stu-id="e6979-123">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
