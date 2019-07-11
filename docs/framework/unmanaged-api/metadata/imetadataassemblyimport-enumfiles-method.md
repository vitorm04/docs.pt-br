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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b32c402b20f9d7f0d370cfa6ec8376603efa8c3f
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777995"
---
# <a name="imetadataassemblyimportenumfiles-method"></a><span data-ttu-id="a7f19-102">Método IMetaDataAssemblyImport::EnumFiles</span><span class="sxs-lookup"><span data-stu-id="a7f19-102">IMetaDataAssemblyImport::EnumFiles Method</span></span>
<span data-ttu-id="a7f19-103">Enumera os arquivos referenciados no manifesto do assembly atual.</span><span class="sxs-lookup"><span data-stu-id="a7f19-103">Enumerates the files referenced in the current assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7f19-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a7f19-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumFiles (  
    [in, out] HCORENUM    *phEnum,   
    [out] mdFile          rFiles[],   
    [in]  ULONG           cMax,   
    [out] ULONG           *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a7f19-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a7f19-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="a7f19-106">[no, out] Um ponteiro para o enumerador.</span><span class="sxs-lookup"><span data-stu-id="a7f19-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="a7f19-107">Isso deve ser um valor nulo para a primeira chamada desse método.</span><span class="sxs-lookup"><span data-stu-id="a7f19-107">This must be a null value for the first call of this method.</span></span>  
  
 `rFiles`  
 <span data-ttu-id="a7f19-108">[out] A matriz usada para armazenar o `mdFile` tokens de metadados.</span><span class="sxs-lookup"><span data-stu-id="a7f19-108">[out] The array used to store the `mdFile` metadata tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="a7f19-109">[in] O número máximo de `mdFile` tokens que podem ser colocadas em `rFiles`.</span><span class="sxs-lookup"><span data-stu-id="a7f19-109">[in] The maximum number of `mdFile` tokens that can be placed in `rFiles`.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="a7f19-110">[out] O número de `mdFile` tokens realmente colocados nos `rFiles`.</span><span class="sxs-lookup"><span data-stu-id="a7f19-110">[out] The number of `mdFile` tokens actually placed in `rFiles`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a7f19-111">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="a7f19-111">Return Value</span></span>  
  
|<span data-ttu-id="a7f19-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a7f19-112">HRESULT</span></span>|<span data-ttu-id="a7f19-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="a7f19-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="a7f19-114">`EnumFiles` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="a7f19-114">`EnumFiles` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="a7f19-115">Não há nenhum token para enumerar.</span><span class="sxs-lookup"><span data-stu-id="a7f19-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="a7f19-116">Nesse caso, `pcTokens` é definido como zero.</span><span class="sxs-lookup"><span data-stu-id="a7f19-116">In this case, `pcTokens` is set to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a7f19-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a7f19-117">Requirements</span></span>  
 <span data-ttu-id="a7f19-118">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a7f19-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a7f19-119">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="a7f19-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a7f19-120">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="a7f19-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a7f19-121">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a7f19-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7f19-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a7f19-122">See also</span></span>

- [<span data-ttu-id="a7f19-123">Interface IMetaDataAssemblyImport</span><span class="sxs-lookup"><span data-stu-id="a7f19-123">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
