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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0a56d874e5e7ef491c24b0aef2ace700087de677
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33447405"
---
# <a name="imetadataassemblyimportenumassemblyrefs-method"></a><span data-ttu-id="86452-102">Método IMetaDataAssemblyImport::EnumAssemblyRefs</span><span class="sxs-lookup"><span data-stu-id="86452-102">IMetaDataAssemblyImport::EnumAssemblyRefs Method</span></span>
<span data-ttu-id="86452-103">Enumera o `mdAssemblyRef` instâncias que são definidas no manifesto do assembly.</span><span class="sxs-lookup"><span data-stu-id="86452-103">Enumerates the `mdAssemblyRef` instances that are defined in the assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86452-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="86452-104">Syntax</span></span>  
  
```  
HRESULT EnumAssemblyRefs (  
    [in, out] HCORENUM        *phEnum,   
    [out]     mdAssemblyRef   rAssemblyRefs[],   
    [in]      ULONG           cMax,   
    [out]     ULONG           *pcTokens  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="86452-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="86452-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="86452-106">[out no] Um ponteiro para o enumerador.</span><span class="sxs-lookup"><span data-stu-id="86452-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="86452-107">Isso deve ser nulo quando o `EnumAssemblyRefs` método é chamado pela primeira vez.</span><span class="sxs-lookup"><span data-stu-id="86452-107">This must be a null value when the `EnumAssemblyRefs` method is called for the first time.</span></span>  
  
 `rAssemblyRefs`  
 <span data-ttu-id="86452-108">[out] A enumeração de `mdAssemblyRef` tokens de metadados.</span><span class="sxs-lookup"><span data-stu-id="86452-108">[out] The enumeration of `mdAssemblyRef` metadata tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="86452-109">[in] O número máximo de tokens que podem ser colocadas no `rAssemblyRefs` matriz.</span><span class="sxs-lookup"><span data-stu-id="86452-109">[in] The maximum number of tokens that can be placed in the `rAssemblyRefs` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="86452-110">[out] O número de tokens, na verdade, colocados em `rAssemblyRefs`.</span><span class="sxs-lookup"><span data-stu-id="86452-110">[out] The number of tokens actually placed in `rAssemblyRefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="86452-111">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="86452-111">Return Value</span></span>  
  
|<span data-ttu-id="86452-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="86452-112">HRESULT</span></span>|<span data-ttu-id="86452-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="86452-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="86452-114">`EnumAssemblyRefs` retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="86452-114">`EnumAssemblyRefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="86452-115">Não há nenhum tokens para enumerar.</span><span class="sxs-lookup"><span data-stu-id="86452-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="86452-116">Nesse caso, `pcTokens` é definido como zero.</span><span class="sxs-lookup"><span data-stu-id="86452-116">In this case, `pcTokens` is set to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="86452-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="86452-117">Requirements</span></span>  
 <span data-ttu-id="86452-118">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="86452-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="86452-119">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="86452-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="86452-120">**Biblioteca:** usado como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="86452-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="86452-121">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="86452-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86452-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="86452-122">See Also</span></span>  
 [<span data-ttu-id="86452-123">Interface IMetaDataAssemblyImport</span><span class="sxs-lookup"><span data-stu-id="86452-123">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
