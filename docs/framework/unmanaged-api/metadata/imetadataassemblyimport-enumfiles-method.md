---
title: Método IMetaDataAssemblyImport::EnumFiles
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.EnumFiles
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::EnumFiles
helpviewer_keywords:
- IMetaDataAssemblyImport::EnumFiles method [.NET Framework metadata]
- EnumFiles method [.NET Framework metadata]
ms.assetid: f0d721e2-b946-426d-8e20-9124bd04e4cb
topic_type:
- apiref
ms.openlocfilehash: 70f76318f51047cb81262f744a6fbed5fe401692
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177809"
---
# <a name="imetadataassemblyimportenumfiles-method"></a><span data-ttu-id="75e81-102">Método IMetaDataAssemblyImport::EnumFiles</span><span class="sxs-lookup"><span data-stu-id="75e81-102">IMetaDataAssemblyImport::EnumFiles Method</span></span>
<span data-ttu-id="75e81-103">Enumera os arquivos referenciados no manifesto de montagem atual.</span><span class="sxs-lookup"><span data-stu-id="75e81-103">Enumerates the files referenced in the current assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="75e81-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="75e81-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumFiles (  
    [in, out] HCORENUM    *phEnum,
    [out] mdFile          rFiles[],
    [in]  ULONG           cMax,
    [out] ULONG           *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="75e81-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="75e81-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="75e81-106">[dentro, fora] Um ponteiro para o enumerador.</span><span class="sxs-lookup"><span data-stu-id="75e81-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="75e81-107">Este deve ser um valor nulo para a primeira chamada deste método.</span><span class="sxs-lookup"><span data-stu-id="75e81-107">This must be a null value for the first call of this method.</span></span>  
  
 `rFiles`  
 <span data-ttu-id="75e81-108">[fora] A matriz usada `mdFile` para armazenar os tokens de metadados.</span><span class="sxs-lookup"><span data-stu-id="75e81-108">[out] The array used to store the `mdFile` metadata tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="75e81-109">[em] O número `mdFile` máximo de tokens `rFiles`que podem ser colocados em .</span><span class="sxs-lookup"><span data-stu-id="75e81-109">[in] The maximum number of `mdFile` tokens that can be placed in `rFiles`.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="75e81-110">[fora] O número `mdFile` de tokens `rFiles`realmente colocados em .</span><span class="sxs-lookup"><span data-stu-id="75e81-110">[out] The number of `mdFile` tokens actually placed in `rFiles`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="75e81-111">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="75e81-111">Return Value</span></span>  
  
|<span data-ttu-id="75e81-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="75e81-112">HRESULT</span></span>|<span data-ttu-id="75e81-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="75e81-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="75e81-114">`EnumFiles`retornou com sucesso.</span><span class="sxs-lookup"><span data-stu-id="75e81-114">`EnumFiles` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="75e81-115">Não há tokens para enumerar.</span><span class="sxs-lookup"><span data-stu-id="75e81-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="75e81-116">Neste caso, `pcTokens` está definido como zero.</span><span class="sxs-lookup"><span data-stu-id="75e81-116">In this case, `pcTokens` is set to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="75e81-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="75e81-117">Requirements</span></span>  
 <span data-ttu-id="75e81-118">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="75e81-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="75e81-119">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="75e81-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="75e81-120">**Biblioteca:** Usado como recurso em MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="75e81-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="75e81-121">**.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="75e81-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75e81-122">Confira também</span><span class="sxs-lookup"><span data-stu-id="75e81-122">See also</span></span>

- [<span data-ttu-id="75e81-123">Interface IMetaDataAssemblyImport</span><span class="sxs-lookup"><span data-stu-id="75e81-123">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
