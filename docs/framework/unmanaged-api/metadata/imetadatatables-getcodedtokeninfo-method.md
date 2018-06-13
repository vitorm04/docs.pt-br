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
ms.openlocfilehash: a7a36d14b67efb3934089dc16de41a3b80ea0c0e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33447984"
---
# <a name="imetadatatablesgetcodedtokeninfo-method"></a><span data-ttu-id="817a2-102">Método IMetaDataTables::GetCodedTokenInfo</span><span class="sxs-lookup"><span data-stu-id="817a2-102">IMetaDataTables::GetCodedTokenInfo Method</span></span>
<span data-ttu-id="817a2-103">Obtém um ponteiro para uma matriz de tokens associada ao índice de linha especificado.</span><span class="sxs-lookup"><span data-stu-id="817a2-103">Gets a pointer to an array of tokens associated with the specified row index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="817a2-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="817a2-104">Syntax</span></span>  
  
```  
HRESULT GetCodedTokenInfo (   
    [in]  ULONG       ixCdTkn,  
    [out] ULONG       *pcTokens,  
    [out] ULONG       **ppTokens,  
    [out] const char  **ppName  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="817a2-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="817a2-105">Parameters</span></span>  
 `ixCdTkn`  
 <span data-ttu-id="817a2-106">[in] O tipo de token codificado a ser retornado.</span><span class="sxs-lookup"><span data-stu-id="817a2-106">[in] The kind of coded token to return.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="817a2-107">[out] Um ponteiro para o comprimento de `ppTokens`.</span><span class="sxs-lookup"><span data-stu-id="817a2-107">[out] A pointer to the length of `ppTokens`.</span></span>  
  
 `ppTokens`  
 <span data-ttu-id="817a2-108">[out] Um ponteiro para um ponteiro para uma matriz que contém a lista de tokens retornados.</span><span class="sxs-lookup"><span data-stu-id="817a2-108">[out] A pointer to a pointer to an array that contains the list of returned tokens.</span></span>  
  
 `ppName`  
 <span data-ttu-id="817a2-109">[out] Um ponteiro para um ponteiro para o nome do token no `ixCdTkn`.</span><span class="sxs-lookup"><span data-stu-id="817a2-109">[out] A pointer to a pointer to the name of the token at `ixCdTkn`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="817a2-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="817a2-110">Requirements</span></span>  
 <span data-ttu-id="817a2-111">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="817a2-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="817a2-112">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="817a2-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="817a2-113">**Biblioteca:** usado como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="817a2-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="817a2-114">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="817a2-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="817a2-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="817a2-115">See Also</span></span>  
 [<span data-ttu-id="817a2-116">Interface IMetaDataTables</span><span class="sxs-lookup"><span data-stu-id="817a2-116">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 [<span data-ttu-id="817a2-117">Interface IMetaDataTables2</span><span class="sxs-lookup"><span data-stu-id="817a2-117">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
