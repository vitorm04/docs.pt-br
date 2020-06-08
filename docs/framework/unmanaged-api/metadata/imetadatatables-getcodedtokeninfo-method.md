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
ms.openlocfilehash: 8ab16ad5b2b2838125e07511ef47be737f40671c
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501203"
---
# <a name="imetadatatablesgetcodedtokeninfo-method"></a><span data-ttu-id="cdb90-102">Método IMetaDataTables::GetCodedTokenInfo</span><span class="sxs-lookup"><span data-stu-id="cdb90-102">IMetaDataTables::GetCodedTokenInfo Method</span></span>
<span data-ttu-id="cdb90-103">Obtém um ponteiro para uma matriz de tokens associados ao índice de linha especificado.</span><span class="sxs-lookup"><span data-stu-id="cdb90-103">Gets a pointer to an array of tokens associated with the specified row index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cdb90-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cdb90-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCodedTokenInfo (
    [in]  ULONG       ixCdTkn,  
    [out] ULONG       *pcTokens,  
    [out] ULONG       **ppTokens,  
    [out] const char  **ppName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cdb90-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="cdb90-105">Parameters</span></span>  
 `ixCdTkn`  
 <span data-ttu-id="cdb90-106">no O tipo de token codificado a ser retornado.</span><span class="sxs-lookup"><span data-stu-id="cdb90-106">[in] The kind of coded token to return.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="cdb90-107">fora Um ponteiro para o comprimento de `ppTokens` .</span><span class="sxs-lookup"><span data-stu-id="cdb90-107">[out] A pointer to the length of `ppTokens`.</span></span>  
  
 `ppTokens`  
 <span data-ttu-id="cdb90-108">fora Um ponteiro para um ponteiro para uma matriz que contém a lista de tokens retornados.</span><span class="sxs-lookup"><span data-stu-id="cdb90-108">[out] A pointer to a pointer to an array that contains the list of returned tokens.</span></span>  
  
 `ppName`  
 <span data-ttu-id="cdb90-109">fora Um ponteiro para um ponteiro para o nome do token em `ixCdTkn` .</span><span class="sxs-lookup"><span data-stu-id="cdb90-109">[out] A pointer to a pointer to the name of the token at `ixCdTkn`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cdb90-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="cdb90-110">Requirements</span></span>  
 <span data-ttu-id="cdb90-111">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cdb90-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cdb90-112">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="cdb90-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="cdb90-113">**Biblioteca:** Usado como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="cdb90-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="cdb90-114">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cdb90-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cdb90-115">Confira também</span><span class="sxs-lookup"><span data-stu-id="cdb90-115">See also</span></span>

- [<span data-ttu-id="cdb90-116">Interface IMetaDataTables</span><span class="sxs-lookup"><span data-stu-id="cdb90-116">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="cdb90-117">Interface IMetaDataTables2</span><span class="sxs-lookup"><span data-stu-id="cdb90-117">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
