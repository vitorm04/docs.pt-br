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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62049767"
---
# <a name="imetadatatablesgetcolumn-method"></a><span data-ttu-id="a922b-102">Método IMetaDataTables::GetColumn</span><span class="sxs-lookup"><span data-stu-id="a922b-102">IMetaDataTables::GetColumn Method</span></span>
<span data-ttu-id="a922b-103">Obtém um ponteiro para o valor contido na célula da coluna especificada e a linha da tabela fornecida.</span><span class="sxs-lookup"><span data-stu-id="a922b-103">Gets a pointer to the value contained in the cell of the specified column and row in the given table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a922b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a922b-104">Syntax</span></span>  
  
```  
HRESULT GetColumn (   
    [in]  ULONG   ixTbl,  
    [in]  ULONG   ixCol,  
    [in]  ULONG   rid,  
    [out] ULONG   *pVal  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a922b-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a922b-105">Parameters</span></span>  
 `ixTbl`  
 <span data-ttu-id="a922b-106">[in] O índice da tabela.</span><span class="sxs-lookup"><span data-stu-id="a922b-106">[in] The index of the table.</span></span>  
  
 `ixCol`  
 <span data-ttu-id="a922b-107">[in] O índice da coluna na tabela.</span><span class="sxs-lookup"><span data-stu-id="a922b-107">[in] The index of the column in the table.</span></span>  
  
 `rid`  
 <span data-ttu-id="a922b-108">[in] O índice da linha na tabela.</span><span class="sxs-lookup"><span data-stu-id="a922b-108">[in] The index of the row in the table.</span></span>  
  
 `pVal`  
 <span data-ttu-id="a922b-109">[out] Um ponteiro para o valor da célula.</span><span class="sxs-lookup"><span data-stu-id="a922b-109">[out] A pointer to the value in the cell.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a922b-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a922b-110">Requirements</span></span>  
 <span data-ttu-id="a922b-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a922b-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a922b-112">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="a922b-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a922b-113">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="a922b-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a922b-114">**Versões do .NET framework** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a922b-114">**.NET Framework Versions** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a922b-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a922b-115">See also</span></span>

- [<span data-ttu-id="a922b-116">Interface IMetaDataTables</span><span class="sxs-lookup"><span data-stu-id="a922b-116">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="a922b-117">Interface IMetaDataTables2</span><span class="sxs-lookup"><span data-stu-id="a922b-117">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
