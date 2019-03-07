---
title: Método IMetaDataTables::GetBlob
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetBlob
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetBlob
helpviewer_keywords:
- GetBlob method [.NET Framework metadata]
- IMetaDataTables::GetBlob method [.NET Framework metadata]
ms.assetid: 94667c1c-6d58-4aa7-b74e-530b11e2a276
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: be7e375f2683ef7f37f2e1e141e1c8a3b00da09a
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57497035"
---
# <a name="imetadatatablesgetblob-method"></a><span data-ttu-id="49114-102">Método IMetaDataTables::GetBlob</span><span class="sxs-lookup"><span data-stu-id="49114-102">IMetaDataTables::GetBlob Method</span></span>
<span data-ttu-id="49114-103">Obtém um ponteiro para o objeto binário grande (BLOB) do índice da coluna especificada.</span><span class="sxs-lookup"><span data-stu-id="49114-103">Gets a pointer to the binary large object (BLOB) at the specified column index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="49114-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="49114-104">Syntax</span></span>  
  
```  
HRESULT GetBlob (  
    [in]  ULONG          ixBlob,  
    [out] ULONG          *pcbData,  
    [out] const void     **ppData  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="49114-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="49114-105">Parameters</span></span>  
 `ixBlob`  
 <span data-ttu-id="49114-106">[in] O endereço de memória do qual obter `ppData`.</span><span class="sxs-lookup"><span data-stu-id="49114-106">[in] The memory address from which to get `ppData`.</span></span>  
  
 `pcbData`  
 <span data-ttu-id="49114-107">[out] Um ponteiro para o tamanho, em bytes, do `ppData`.</span><span class="sxs-lookup"><span data-stu-id="49114-107">[out] A pointer to the size, in bytes, of `ppData`.</span></span>  
  
 `ppData`  
 <span data-ttu-id="49114-108">[out] Recuperar um ponteiro para um ponteiro para os dados binários.</span><span class="sxs-lookup"><span data-stu-id="49114-108">[out] A pointer to a pointer to the binary data retrieved.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="49114-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="49114-109">Requirements</span></span>  
 <span data-ttu-id="49114-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="49114-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="49114-111">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="49114-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="49114-112">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="49114-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="49114-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="49114-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49114-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="49114-114">See also</span></span>
- [<span data-ttu-id="49114-115">Interface IMetaDataTables</span><span class="sxs-lookup"><span data-stu-id="49114-115">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="49114-116">Interface IMetaDataTables2</span><span class="sxs-lookup"><span data-stu-id="49114-116">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
