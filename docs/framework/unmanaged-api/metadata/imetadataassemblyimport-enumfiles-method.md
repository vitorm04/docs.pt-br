---
title: "Método IMetaDataAssemblyImport::EnumFiles"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataAssemblyImport.EnumFiles
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataAssemblyImport::EnumFiles
helpviewer_keywords:
- IMetaDataAssemblyImport::EnumFiles method [.NET Framework metadata]
- EnumFiles method [.NET Framework metadata]
ms.assetid: f0d721e2-b946-426d-8e20-9124bd04e4cb
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: dfe8f1c9080a963458f6dc429475a1fd0407bb2e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="imetadataassemblyimportenumfiles-method"></a><span data-ttu-id="d6ba6-102">Método IMetaDataAssemblyImport::EnumFiles</span><span class="sxs-lookup"><span data-stu-id="d6ba6-102">IMetaDataAssemblyImport::EnumFiles Method</span></span>
<span data-ttu-id="d6ba6-103">Enumera os arquivos referenciados no manifesto do assembly atual.</span><span class="sxs-lookup"><span data-stu-id="d6ba6-103">Enumerates the files referenced in the current assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6ba6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d6ba6-104">Syntax</span></span>  
  
```  
HRESULT EnumFiles (  
    [in, out] HCORENUM    *phEnum,   
    [out] mdFile          rFiles[],   
    [in]  ULONG           cMax,   
    [out] ULONG           *pcTokens  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d6ba6-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d6ba6-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="d6ba6-106">[out no] Um ponteiro para o enumerador.</span><span class="sxs-lookup"><span data-stu-id="d6ba6-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="d6ba6-107">Isso deve ser um valor nulo para a primeira chamada do método.</span><span class="sxs-lookup"><span data-stu-id="d6ba6-107">This must be a null value for the first call of this method.</span></span>  
  
 `rFiles`  
 <span data-ttu-id="d6ba6-108">[out] A matriz usada para armazenar o `mdFile` tokens de metadados.</span><span class="sxs-lookup"><span data-stu-id="d6ba6-108">[out] The array used to store the `mdFile` metadata tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="d6ba6-109">[in] O número máximo de `mdFile` tokens que podem ser colocados em `rFiles`.</span><span class="sxs-lookup"><span data-stu-id="d6ba6-109">[in] The maximum number of `mdFile` tokens that can be placed in `rFiles`.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="d6ba6-110">[out] O número de `mdFile` tokens realmente realizada em `rFiles`.</span><span class="sxs-lookup"><span data-stu-id="d6ba6-110">[out] The number of `mdFile` tokens actually placed in `rFiles`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d6ba6-111">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="d6ba6-111">Return Value</span></span>  
  
|<span data-ttu-id="d6ba6-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d6ba6-112">HRESULT</span></span>|<span data-ttu-id="d6ba6-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="d6ba6-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="d6ba6-114">`EnumFiles`retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="d6ba6-114">`EnumFiles` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="d6ba6-115">Não há nenhum tokens para enumerar.</span><span class="sxs-lookup"><span data-stu-id="d6ba6-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="d6ba6-116">Nesse caso, `pcTokens` é definido como zero.</span><span class="sxs-lookup"><span data-stu-id="d6ba6-116">In this case, `pcTokens` is set to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d6ba6-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d6ba6-117">Requirements</span></span>  
 <span data-ttu-id="d6ba6-118">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d6ba6-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d6ba6-119">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="d6ba6-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d6ba6-120">**Biblioteca:** usado como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="d6ba6-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d6ba6-121">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d6ba6-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6ba6-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d6ba6-122">See Also</span></span>  
 [<span data-ttu-id="d6ba6-123">Interface IMetaDataAssemblyImport</span><span class="sxs-lookup"><span data-stu-id="d6ba6-123">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
