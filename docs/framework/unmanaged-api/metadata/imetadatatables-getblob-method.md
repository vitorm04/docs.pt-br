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
ms.openlocfilehash: babe098b16729cfcd41b48075a49b9ae9be7dfdc
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59117177"
---
# <a name="imetadatatablesgetblob-method"></a><span data-ttu-id="5e3f8-102">Método IMetaDataTables::GetBlob</span><span class="sxs-lookup"><span data-stu-id="5e3f8-102">IMetaDataTables::GetBlob Method</span></span>
<span data-ttu-id="5e3f8-103">Obtém um ponteiro para o objeto binário grande (BLOB) do índice da coluna especificada.</span><span class="sxs-lookup"><span data-stu-id="5e3f8-103">Gets a pointer to the binary large object (BLOB) at the specified column index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e3f8-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5e3f8-104">Syntax</span></span>  
  
```  
HRESULT GetBlob (  
    [in]  ULONG          ixBlob,  
    [out] ULONG          *pcbData,  
    [out] const void     **ppData  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5e3f8-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5e3f8-105">Parameters</span></span>  
 `ixBlob`  
 <span data-ttu-id="5e3f8-106">[in] O endereço de memória do qual obter `ppData`.</span><span class="sxs-lookup"><span data-stu-id="5e3f8-106">[in] The memory address from which to get `ppData`.</span></span>  
  
 `pcbData`  
 <span data-ttu-id="5e3f8-107">[out] Um ponteiro para o tamanho, em bytes, do `ppData`.</span><span class="sxs-lookup"><span data-stu-id="5e3f8-107">[out] A pointer to the size, in bytes, of `ppData`.</span></span>  
  
 `ppData`  
 <span data-ttu-id="5e3f8-108">[out] Recuperar um ponteiro para um ponteiro para os dados binários.</span><span class="sxs-lookup"><span data-stu-id="5e3f8-108">[out] A pointer to a pointer to the binary data retrieved.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5e3f8-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5e3f8-109">Requirements</span></span>  
 <span data-ttu-id="5e3f8-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5e3f8-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5e3f8-111">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="5e3f8-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5e3f8-112">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="5e3f8-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="5e3f8-113">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="5e3f8-113">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="5e3f8-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5e3f8-114">See also</span></span>

- [<span data-ttu-id="5e3f8-115">Interface IMetaDataTables</span><span class="sxs-lookup"><span data-stu-id="5e3f8-115">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="5e3f8-116">Interface IMetaDataTables2</span><span class="sxs-lookup"><span data-stu-id="5e3f8-116">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
