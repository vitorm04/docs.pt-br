---
title: Método IMetaDataTables::GetNextBlob
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetNextBlob
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetNextBlob
helpviewer_keywords:
- IMetaDataTables::GetNextBlob method [.NET Framework metadata]
- GetNextBlob method [.NET Framework metadata]
ms.assetid: 017c8ab4-4c09-4754-9935-5b0b49cabecb
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9b8a91a2c1ef9b68dcfc293a870ce3e9b9499a8f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61946772"
---
# <a name="imetadatatablesgetnextblob-method"></a><span data-ttu-id="153df-102">Método IMetaDataTables::GetNextBlob</span><span class="sxs-lookup"><span data-stu-id="153df-102">IMetaDataTables::GetNextBlob Method</span></span>
<span data-ttu-id="153df-103">Obtém o índice do próximo grande objeto binário (BLOB) na tabela.</span><span class="sxs-lookup"><span data-stu-id="153df-103">Gets the index of the next binary large object (BLOB) in the table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="153df-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="153df-104">Syntax</span></span>  
  
```  
HRESULT GetNextBlob (  
    [in]  ULONG   ixBlob,  
    [out] ULONG   *pNext  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="153df-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="153df-105">Parameters</span></span>  
 `ixBlob`  
 <span data-ttu-id="153df-106">[in] O índice, conforme retornado de uma coluna de BLOBs.</span><span class="sxs-lookup"><span data-stu-id="153df-106">[in] The index, as returned from a column of BLOBs.</span></span>  
  
 `pNext`  
 <span data-ttu-id="153df-107">[out] Um ponteiro para o índice do próximo BLOB.</span><span class="sxs-lookup"><span data-stu-id="153df-107">[out] A pointer to the index of the next BLOB.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="153df-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="153df-108">Requirements</span></span>  
 <span data-ttu-id="153df-109">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="153df-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="153df-110">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="153df-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="153df-111">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="153df-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="153df-112">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="153df-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="153df-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="153df-113">See also</span></span>

- [<span data-ttu-id="153df-114">Interface IMetaDataTables</span><span class="sxs-lookup"><span data-stu-id="153df-114">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="153df-115">Interface IMetaDataTables2</span><span class="sxs-lookup"><span data-stu-id="153df-115">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
