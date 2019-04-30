---
title: Método IMetaDataTables::GetCodedTokenInfo
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetCodedTokenInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetCodedTokenInfo
helpviewer_keywords:
- GetCodedTokenInfo method [.NET Framework metadata]
- IMetaDataTables::GetCodedTokenInfo method [.NET Framework metadata]
ms.assetid: 31214d3a-715e-49af-92b3-0fd11e4f218a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 153aa7d6b8c35129638de3d47ffa6aff72f550c9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61946755"
---
# <a name="imetadatatablesgetcodedtokeninfo-method"></a><span data-ttu-id="2630a-102">Método IMetaDataTables::GetCodedTokenInfo</span><span class="sxs-lookup"><span data-stu-id="2630a-102">IMetaDataTables::GetCodedTokenInfo Method</span></span>
<span data-ttu-id="2630a-103">Obtém um ponteiro para uma matriz de tokens associados com o índice da linha especificada.</span><span class="sxs-lookup"><span data-stu-id="2630a-103">Gets a pointer to an array of tokens associated with the specified row index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2630a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2630a-104">Syntax</span></span>  
  
```  
HRESULT GetCodedTokenInfo (   
    [in]  ULONG       ixCdTkn,  
    [out] ULONG       *pcTokens,  
    [out] ULONG       **ppTokens,  
    [out] const char  **ppName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2630a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2630a-105">Parameters</span></span>  
 `ixCdTkn`  
 <span data-ttu-id="2630a-106">[in] O tipo de token codificado a ser retornado.</span><span class="sxs-lookup"><span data-stu-id="2630a-106">[in] The kind of coded token to return.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="2630a-107">[out] Um ponteiro para o comprimento de `ppTokens`.</span><span class="sxs-lookup"><span data-stu-id="2630a-107">[out] A pointer to the length of `ppTokens`.</span></span>  
  
 `ppTokens`  
 <span data-ttu-id="2630a-108">[out] Um ponteiro para um ponteiro para uma matriz que contém a lista de tokens retornados.</span><span class="sxs-lookup"><span data-stu-id="2630a-108">[out] A pointer to a pointer to an array that contains the list of returned tokens.</span></span>  
  
 `ppName`  
 <span data-ttu-id="2630a-109">[out] Um ponteiro para um ponteiro para o nome do token em `ixCdTkn`.</span><span class="sxs-lookup"><span data-stu-id="2630a-109">[out] A pointer to a pointer to the name of the token at `ixCdTkn`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2630a-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2630a-110">Requirements</span></span>  
 <span data-ttu-id="2630a-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2630a-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2630a-112">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="2630a-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2630a-113">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="2630a-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2630a-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2630a-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2630a-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2630a-115">See also</span></span>

- [<span data-ttu-id="2630a-116">Interface IMetaDataTables</span><span class="sxs-lookup"><span data-stu-id="2630a-116">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="2630a-117">Interface IMetaDataTables2</span><span class="sxs-lookup"><span data-stu-id="2630a-117">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
