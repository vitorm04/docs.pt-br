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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61905327"
---
# <a name="imetadataassemblyimportenumfiles-method"></a><span data-ttu-id="a0542-102">Método IMetaDataAssemblyImport::EnumFiles</span><span class="sxs-lookup"><span data-stu-id="a0542-102">IMetaDataAssemblyImport::EnumFiles Method</span></span>
<span data-ttu-id="a0542-103">Enumera os arquivos referenciados no manifesto do assembly atual.</span><span class="sxs-lookup"><span data-stu-id="a0542-103">Enumerates the files referenced in the current assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a0542-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a0542-104">Syntax</span></span>  
  
```  
HRESULT EnumFiles (  
    [in, out] HCORENUM    *phEnum,   
    [out] mdFile          rFiles[],   
    [in]  ULONG           cMax,   
    [out] ULONG           *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a0542-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a0542-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="a0542-106">[no, out] Um ponteiro para o enumerador.</span><span class="sxs-lookup"><span data-stu-id="a0542-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="a0542-107">Isso deve ser um valor nulo para a primeira chamada desse método.</span><span class="sxs-lookup"><span data-stu-id="a0542-107">This must be a null value for the first call of this method.</span></span>  
  
 `rFiles`  
 <span data-ttu-id="a0542-108">[out] A matriz usada para armazenar o `mdFile` tokens de metadados.</span><span class="sxs-lookup"><span data-stu-id="a0542-108">[out] The array used to store the `mdFile` metadata tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="a0542-109">[in] O número máximo de `mdFile` tokens que podem ser colocadas em `rFiles`.</span><span class="sxs-lookup"><span data-stu-id="a0542-109">[in] The maximum number of `mdFile` tokens that can be placed in `rFiles`.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="a0542-110">[out] O número de `mdFile` tokens realmente colocados nos `rFiles`.</span><span class="sxs-lookup"><span data-stu-id="a0542-110">[out] The number of `mdFile` tokens actually placed in `rFiles`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a0542-111">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="a0542-111">Return Value</span></span>  
  
|<span data-ttu-id="a0542-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a0542-112">HRESULT</span></span>|<span data-ttu-id="a0542-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="a0542-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="a0542-114">`EnumFiles` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="a0542-114">`EnumFiles` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="a0542-115">Não há nenhum token para enumerar.</span><span class="sxs-lookup"><span data-stu-id="a0542-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="a0542-116">Nesse caso, `pcTokens` é definido como zero.</span><span class="sxs-lookup"><span data-stu-id="a0542-116">In this case, `pcTokens` is set to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a0542-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a0542-117">Requirements</span></span>  
 <span data-ttu-id="a0542-118">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a0542-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a0542-119">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="a0542-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a0542-120">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="a0542-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a0542-121">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a0542-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0542-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a0542-122">See also</span></span>

- [<span data-ttu-id="a0542-123">Interface IMetaDataAssemblyImport</span><span class="sxs-lookup"><span data-stu-id="a0542-123">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
