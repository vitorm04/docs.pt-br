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
ms.openlocfilehash: 577a4f6bb8315cfb1cb462703dd0cb9b23b60704
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74434059"
---
# <a name="imetadatatablesgetcodedtokeninfo-method"></a><span data-ttu-id="95861-102">Método IMetaDataTables::GetCodedTokenInfo</span><span class="sxs-lookup"><span data-stu-id="95861-102">IMetaDataTables::GetCodedTokenInfo Method</span></span>
<span data-ttu-id="95861-103">Obtém um ponteiro para uma matriz de tokens associados ao índice de linha especificado.</span><span class="sxs-lookup"><span data-stu-id="95861-103">Gets a pointer to an array of tokens associated with the specified row index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="95861-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="95861-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCodedTokenInfo (   
    [in]  ULONG       ixCdTkn,  
    [out] ULONG       *pcTokens,  
    [out] ULONG       **ppTokens,  
    [out] const char  **ppName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="95861-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="95861-105">Parameters</span></span>  
 `ixCdTkn`  
 <span data-ttu-id="95861-106">no O tipo de token codificado a ser retornado.</span><span class="sxs-lookup"><span data-stu-id="95861-106">[in] The kind of coded token to return.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="95861-107">fora Um ponteiro para o comprimento de `ppTokens`.</span><span class="sxs-lookup"><span data-stu-id="95861-107">[out] A pointer to the length of `ppTokens`.</span></span>  
  
 `ppTokens`  
 <span data-ttu-id="95861-108">fora Um ponteiro para um ponteiro para uma matriz que contém a lista de tokens retornados.</span><span class="sxs-lookup"><span data-stu-id="95861-108">[out] A pointer to a pointer to an array that contains the list of returned tokens.</span></span>  
  
 `ppName`  
 <span data-ttu-id="95861-109">fora Um ponteiro para um ponteiro para o nome do token em `ixCdTkn`.</span><span class="sxs-lookup"><span data-stu-id="95861-109">[out] A pointer to a pointer to the name of the token at `ixCdTkn`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="95861-110">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="95861-110">Requirements</span></span>  
 <span data-ttu-id="95861-111">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="95861-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="95861-112">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="95861-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="95861-113">**Biblioteca:** Usado como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="95861-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="95861-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="95861-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95861-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="95861-115">See also</span></span>

- [<span data-ttu-id="95861-116">Interface IMetaDataTables</span><span class="sxs-lookup"><span data-stu-id="95861-116">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="95861-117">Interface IMetaDataTables2</span><span class="sxs-lookup"><span data-stu-id="95861-117">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
