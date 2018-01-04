---
title: "Método IMetaDataTables::GetColumn"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataTables.GetColumn
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataTables::GetColumn
helpviewer_keywords:
- IMetaDataTables::GetColumn method [.NET Framework metadata]
- GetColumn method [.NET Framework metadata]
ms.assetid: 1032055b-cabb-45c5-a50e-7e853201b175
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 162162b972ab0e1f3de55d56c18372f2475c9846
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadatatablesgetcolumn-method"></a><span data-ttu-id="27a7a-102">Método IMetaDataTables::GetColumn</span><span class="sxs-lookup"><span data-stu-id="27a7a-102">IMetaDataTables::GetColumn Method</span></span>
<span data-ttu-id="27a7a-103">Obtém um ponteiro para o valor contido na célula da coluna especificada e a linha na tabela específica.</span><span class="sxs-lookup"><span data-stu-id="27a7a-103">Gets a pointer to the value contained in the cell of the specified column and row in the given table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27a7a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="27a7a-104">Syntax</span></span>  
  
```  
HRESULT GetColumn (   
    [in]  ULONG   ixTbl,  
    [in]  ULONG   ixCol,  
    [in]  ULONG   rid,  
    [out] ULONG   *pVal  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="27a7a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="27a7a-105">Parameters</span></span>  
 `ixTbl`  
 <span data-ttu-id="27a7a-106">[in] O índice da tabela.</span><span class="sxs-lookup"><span data-stu-id="27a7a-106">[in] The index of the table.</span></span>  
  
 `ixCol`  
 <span data-ttu-id="27a7a-107">[in] O índice da coluna na tabela.</span><span class="sxs-lookup"><span data-stu-id="27a7a-107">[in] The index of the column in the table.</span></span>  
  
 `rid`  
 <span data-ttu-id="27a7a-108">[in] O índice da linha na tabela.</span><span class="sxs-lookup"><span data-stu-id="27a7a-108">[in] The index of the row in the table.</span></span>  
  
 `pVal`  
 <span data-ttu-id="27a7a-109">[out] Um ponteiro para o valor da célula.</span><span class="sxs-lookup"><span data-stu-id="27a7a-109">[out] A pointer to the value in the cell.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="27a7a-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="27a7a-110">Requirements</span></span>  
 <span data-ttu-id="27a7a-111">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="27a7a-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="27a7a-112">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="27a7a-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="27a7a-113">**Biblioteca:** usado como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="27a7a-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="27a7a-114">**Versões do .NET framework**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="27a7a-114">**.NET Framework Versions** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27a7a-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="27a7a-115">See Also</span></span>  
 [<span data-ttu-id="27a7a-116">Interface IMetaDataTables</span><span class="sxs-lookup"><span data-stu-id="27a7a-116">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 [<span data-ttu-id="27a7a-117">Interface IMetaDataTables2</span><span class="sxs-lookup"><span data-stu-id="27a7a-117">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
