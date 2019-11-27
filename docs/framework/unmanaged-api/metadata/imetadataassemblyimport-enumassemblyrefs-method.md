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
ms.openlocfilehash: 06b81615565a04db7d6cfef4da9b5372a85afd68
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450352"
---
# <a name="imetadataassemblyimportenumassemblyrefs-method"></a><span data-ttu-id="aac07-102">Método IMetaDataAssemblyImport::EnumAssemblyRefs</span><span class="sxs-lookup"><span data-stu-id="aac07-102">IMetaDataAssemblyImport::EnumAssemblyRefs Method</span></span>
<span data-ttu-id="aac07-103">Enumera as instâncias de `mdAssemblyRef` que são definidas no manifesto do assembly.</span><span class="sxs-lookup"><span data-stu-id="aac07-103">Enumerates the `mdAssemblyRef` instances that are defined in the assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aac07-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="aac07-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumAssemblyRefs (  
    [in, out] HCORENUM        *phEnum,   
    [out]     mdAssemblyRef   rAssemblyRefs[],   
    [in]      ULONG           cMax,   
    [out]     ULONG           *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="aac07-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="aac07-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="aac07-106">[entrada, saída] Um ponteiro para o enumerador.</span><span class="sxs-lookup"><span data-stu-id="aac07-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="aac07-107">Esse deve ser um valor nulo quando o método `EnumAssemblyRefs` é chamado pela primeira vez.</span><span class="sxs-lookup"><span data-stu-id="aac07-107">This must be a null value when the `EnumAssemblyRefs` method is called for the first time.</span></span>  
  
 `rAssemblyRefs`  
 <span data-ttu-id="aac07-108">fora A enumeração de tokens de metadados de `mdAssemblyRef`.</span><span class="sxs-lookup"><span data-stu-id="aac07-108">[out] The enumeration of `mdAssemblyRef` metadata tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="aac07-109">no O número máximo de tokens que podem ser colocados na matriz de `rAssemblyRefs`.</span><span class="sxs-lookup"><span data-stu-id="aac07-109">[in] The maximum number of tokens that can be placed in the `rAssemblyRefs` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="aac07-110">fora O número de tokens realmente colocados em `rAssemblyRefs`.</span><span class="sxs-lookup"><span data-stu-id="aac07-110">[out] The number of tokens actually placed in `rAssemblyRefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="aac07-111">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="aac07-111">Return Value</span></span>  
  
|<span data-ttu-id="aac07-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="aac07-112">HRESULT</span></span>|<span data-ttu-id="aac07-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="aac07-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="aac07-114">`EnumAssemblyRefs` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="aac07-114">`EnumAssemblyRefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="aac07-115">Não há tokens para enumerar.</span><span class="sxs-lookup"><span data-stu-id="aac07-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="aac07-116">Nesse caso, `pcTokens` é definido como zero.</span><span class="sxs-lookup"><span data-stu-id="aac07-116">In this case, `pcTokens` is set to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="aac07-117">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="aac07-117">Requirements</span></span>  
 <span data-ttu-id="aac07-118">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aac07-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aac07-119">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="aac07-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="aac07-120">**Biblioteca:** Usado como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="aac07-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="aac07-121">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aac07-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aac07-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="aac07-122">See also</span></span>

- [<span data-ttu-id="aac07-123">Interface IMetaDataAssemblyImport</span><span class="sxs-lookup"><span data-stu-id="aac07-123">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
