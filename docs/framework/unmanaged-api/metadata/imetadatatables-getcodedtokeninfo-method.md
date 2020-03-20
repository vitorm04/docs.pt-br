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
ms.openlocfilehash: 64c70fe0b657047ae35dccb763fa57120403deef
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177145"
---
# <a name="imetadatatablesgetcodedtokeninfo-method"></a><span data-ttu-id="8c162-102">Método IMetaDataTables::GetCodedTokenInfo</span><span class="sxs-lookup"><span data-stu-id="8c162-102">IMetaDataTables::GetCodedTokenInfo Method</span></span>
<span data-ttu-id="8c162-103">Obtém um ponteiro para uma matriz de tokens associados ao índice de linha especificado.</span><span class="sxs-lookup"><span data-stu-id="8c162-103">Gets a pointer to an array of tokens associated with the specified row index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c162-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8c162-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCodedTokenInfo (
    [in]  ULONG       ixCdTkn,  
    [out] ULONG       *pcTokens,  
    [out] ULONG       **ppTokens,  
    [out] const char  **ppName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8c162-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="8c162-105">Parameters</span></span>  
 `ixCdTkn`  
 <span data-ttu-id="8c162-106">[em] O tipo de token codificado para retornar.</span><span class="sxs-lookup"><span data-stu-id="8c162-106">[in] The kind of coded token to return.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="8c162-107">[fora] Um ponteiro para `ppTokens`o comprimento de .</span><span class="sxs-lookup"><span data-stu-id="8c162-107">[out] A pointer to the length of `ppTokens`.</span></span>  
  
 `ppTokens`  
 <span data-ttu-id="8c162-108">[fora] Um ponteiro para um ponteiro para uma matriz que contém a lista de tokens retornados.</span><span class="sxs-lookup"><span data-stu-id="8c162-108">[out] A pointer to a pointer to an array that contains the list of returned tokens.</span></span>  
  
 `ppName`  
 <span data-ttu-id="8c162-109">[fora] Um ponteiro para um ponteiro para o `ixCdTkn`nome do token em .</span><span class="sxs-lookup"><span data-stu-id="8c162-109">[out] A pointer to a pointer to the name of the token at `ixCdTkn`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8c162-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8c162-110">Requirements</span></span>  
 <span data-ttu-id="8c162-111">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8c162-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8c162-112">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="8c162-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8c162-113">**Biblioteca:** Usado como recurso em MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8c162-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8c162-114">**.NET Framework Versions:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8c162-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c162-115">Confira também</span><span class="sxs-lookup"><span data-stu-id="8c162-115">See also</span></span>

- [<span data-ttu-id="8c162-116">Interface IMetaDataTables</span><span class="sxs-lookup"><span data-stu-id="8c162-116">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="8c162-117">Interface IMetaDataTables2</span><span class="sxs-lookup"><span data-stu-id="8c162-117">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
