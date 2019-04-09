---
title: Método IMetaDataTables::GetColumn
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetColumn
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetColumn
helpviewer_keywords:
- IMetaDataTables::GetColumn method [.NET Framework metadata]
- GetColumn method [.NET Framework metadata]
ms.assetid: 1032055b-cabb-45c5-a50e-7e853201b175
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 90ce56b3959c4768ef9cb6a9c551d53c5300a39e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59208352"
---
# <a name="imetadatatablesgetcolumn-method"></a><span data-ttu-id="25bf5-102">Método IMetaDataTables::GetColumn</span><span class="sxs-lookup"><span data-stu-id="25bf5-102">IMetaDataTables::GetColumn Method</span></span>
<span data-ttu-id="25bf5-103">Obtém um ponteiro para o valor contido na célula da coluna especificada e a linha da tabela fornecida.</span><span class="sxs-lookup"><span data-stu-id="25bf5-103">Gets a pointer to the value contained in the cell of the specified column and row in the given table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25bf5-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="25bf5-104">Syntax</span></span>  
  
```  
HRESULT GetColumn (   
    [in]  ULONG   ixTbl,  
    [in]  ULONG   ixCol,  
    [in]  ULONG   rid,  
    [out] ULONG   *pVal  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="25bf5-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="25bf5-105">Parameters</span></span>  
 `ixTbl`  
 <span data-ttu-id="25bf5-106">[in] O índice da tabela.</span><span class="sxs-lookup"><span data-stu-id="25bf5-106">[in] The index of the table.</span></span>  
  
 `ixCol`  
 <span data-ttu-id="25bf5-107">[in] O índice da coluna na tabela.</span><span class="sxs-lookup"><span data-stu-id="25bf5-107">[in] The index of the column in the table.</span></span>  
  
 `rid`  
 <span data-ttu-id="25bf5-108">[in] O índice da linha na tabela.</span><span class="sxs-lookup"><span data-stu-id="25bf5-108">[in] The index of the row in the table.</span></span>  
  
 `pVal`  
 <span data-ttu-id="25bf5-109">[out] Um ponteiro para o valor da célula.</span><span class="sxs-lookup"><span data-stu-id="25bf5-109">[out] A pointer to the value in the cell.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="25bf5-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="25bf5-110">Requirements</span></span>  
 <span data-ttu-id="25bf5-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="25bf5-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="25bf5-112">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="25bf5-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="25bf5-113">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="25bf5-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="25bf5-114">Versões do .NET framework</span><span class="sxs-lookup"><span data-stu-id="25bf5-114">.NET Framework Versions</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="25bf5-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="25bf5-115">See also</span></span>

- [<span data-ttu-id="25bf5-116">Interface IMetaDataTables</span><span class="sxs-lookup"><span data-stu-id="25bf5-116">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="25bf5-117">Interface IMetaDataTables2</span><span class="sxs-lookup"><span data-stu-id="25bf5-117">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
