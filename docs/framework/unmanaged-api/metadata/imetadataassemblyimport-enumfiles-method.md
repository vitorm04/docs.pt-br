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
ms.openlocfilehash: b2ab06419491093a2de41d2ef25d16c01c03ebaf
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59158841"
---
# <a name="imetadataassemblyimportenumfiles-method"></a><span data-ttu-id="23071-102">Método IMetaDataAssemblyImport::EnumFiles</span><span class="sxs-lookup"><span data-stu-id="23071-102">IMetaDataAssemblyImport::EnumFiles Method</span></span>
<span data-ttu-id="23071-103">Enumera os arquivos referenciados no manifesto do assembly atual.</span><span class="sxs-lookup"><span data-stu-id="23071-103">Enumerates the files referenced in the current assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="23071-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="23071-104">Syntax</span></span>  
  
```  
HRESULT EnumFiles (  
    [in, out] HCORENUM    *phEnum,   
    [out] mdFile          rFiles[],   
    [in]  ULONG           cMax,   
    [out] ULONG           *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="23071-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="23071-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="23071-106">[no, out] Um ponteiro para o enumerador.</span><span class="sxs-lookup"><span data-stu-id="23071-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="23071-107">Isso deve ser um valor nulo para a primeira chamada desse método.</span><span class="sxs-lookup"><span data-stu-id="23071-107">This must be a null value for the first call of this method.</span></span>  
  
 `rFiles`  
 <span data-ttu-id="23071-108">[out] A matriz usada para armazenar o `mdFile` tokens de metadados.</span><span class="sxs-lookup"><span data-stu-id="23071-108">[out] The array used to store the `mdFile` metadata tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="23071-109">[in] O número máximo de `mdFile` tokens que podem ser colocadas em `rFiles`.</span><span class="sxs-lookup"><span data-stu-id="23071-109">[in] The maximum number of `mdFile` tokens that can be placed in `rFiles`.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="23071-110">[out] O número de `mdFile` tokens realmente colocados nos `rFiles`.</span><span class="sxs-lookup"><span data-stu-id="23071-110">[out] The number of `mdFile` tokens actually placed in `rFiles`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="23071-111">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="23071-111">Return Value</span></span>  
  
|<span data-ttu-id="23071-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="23071-112">HRESULT</span></span>|<span data-ttu-id="23071-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="23071-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|`EnumFiles` <span data-ttu-id="23071-114">retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="23071-114">returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="23071-115">Não há nenhum token para enumerar.</span><span class="sxs-lookup"><span data-stu-id="23071-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="23071-116">Nesse caso, `pcTokens` é definido como zero.</span><span class="sxs-lookup"><span data-stu-id="23071-116">In this case, `pcTokens` is set to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="23071-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="23071-117">Requirements</span></span>  
 <span data-ttu-id="23071-118">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="23071-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="23071-119">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="23071-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="23071-120">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="23071-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="23071-121">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="23071-121">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="23071-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="23071-122">See also</span></span>

- [<span data-ttu-id="23071-123">Interface IMetaDataAssemblyImport</span><span class="sxs-lookup"><span data-stu-id="23071-123">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
