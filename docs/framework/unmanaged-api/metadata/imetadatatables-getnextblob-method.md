---
title: "Método IMetaDataTables::GetNextBlob"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataTables.GetNextBlob
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataTables::GetNextBlob
helpviewer_keywords:
- IMetaDataTables::GetNextBlob method [.NET Framework metadata]
- GetNextBlob method [.NET Framework metadata]
ms.assetid: 017c8ab4-4c09-4754-9935-5b0b49cabecb
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 399cf6626e7a56584829b2a8417958ce7e608727
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadatatablesgetnextblob-method"></a><span data-ttu-id="cfbfc-102">Método IMetaDataTables::GetNextBlob</span><span class="sxs-lookup"><span data-stu-id="cfbfc-102">IMetaDataTables::GetNextBlob Method</span></span>
<span data-ttu-id="cfbfc-103">Obtém o índice do objeto binário grande (BLOB) Avançar na tabela.</span><span class="sxs-lookup"><span data-stu-id="cfbfc-103">Gets the index of the next binary large object (BLOB) in the table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cfbfc-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cfbfc-104">Syntax</span></span>  
  
```  
HRESULT GetNextBlob (  
    [in]  ULONG   ixBlob,  
    [out] ULONG   *pNext  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cfbfc-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="cfbfc-105">Parameters</span></span>  
 `ixBlob`  
 <span data-ttu-id="cfbfc-106">[in] O índice, conforme retornado de uma coluna de BLOBs.</span><span class="sxs-lookup"><span data-stu-id="cfbfc-106">[in] The index, as returned from a column of BLOBs.</span></span>  
  
 `pNext`  
 <span data-ttu-id="cfbfc-107">[out] Um ponteiro para o índice do próximo BLOB.</span><span class="sxs-lookup"><span data-stu-id="cfbfc-107">[out] A pointer to the index of the next BLOB.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cfbfc-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="cfbfc-108">Requirements</span></span>  
 <span data-ttu-id="cfbfc-109">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cfbfc-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cfbfc-110">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="cfbfc-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="cfbfc-111">**Biblioteca:** usado como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="cfbfc-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="cfbfc-112">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cfbfc-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cfbfc-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cfbfc-113">See Also</span></span>  
 [<span data-ttu-id="cfbfc-114">Interface IMetaDataTables</span><span class="sxs-lookup"><span data-stu-id="cfbfc-114">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 [<span data-ttu-id="cfbfc-115">Interface IMetaDataTables2</span><span class="sxs-lookup"><span data-stu-id="cfbfc-115">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
