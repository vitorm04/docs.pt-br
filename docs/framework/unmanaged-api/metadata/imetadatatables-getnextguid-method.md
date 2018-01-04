---
title: "Método IMetaDataTables::GetNextGuid"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataTables.GetNextGuid
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataTables::GetNextGuid
helpviewer_keywords:
- GetNextGuid method [.NET Framework metadata]
- IMetaDataTables::GetNextGuid method [.NET Framework metadata]
ms.assetid: 68f6ea4d-9112-4d6b-93d9-e34f1e2f2496
topic_type: apiref
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8d3585778d9076cb313ffed69a0e126891c4ce49
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadatatablesgetnextguid-method"></a><span data-ttu-id="c9f9b-102">Método IMetaDataTables::GetNextGuid</span><span class="sxs-lookup"><span data-stu-id="c9f9b-102">IMetaDataTables::GetNextGuid Method</span></span>
<span data-ttu-id="c9f9b-103">Obtém o índice do próximo valor GUID na coluna da tabela atual.</span><span class="sxs-lookup"><span data-stu-id="c9f9b-103">Gets the index of the next GUID value in the current table column.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9f9b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c9f9b-104">Syntax</span></span>  
  
```  
HRESULT GetNextGuid (  
    [in]  ULONG   ixGuid,  
    [out] ULONG   *pNext  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c9f9b-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c9f9b-105">Parameters</span></span>  
 `ixGuid`  
 <span data-ttu-id="c9f9b-106">[in] O valor de índice de uma coluna de tabela GUID.</span><span class="sxs-lookup"><span data-stu-id="c9f9b-106">[in] The index value from a GUID table column.</span></span>  
  
 `pNext`  
 <span data-ttu-id="c9f9b-107">[out] Um ponteiro para o índice do próximo valor GUID.</span><span class="sxs-lookup"><span data-stu-id="c9f9b-107">[out] A pointer to the index of the next GUID value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c9f9b-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="c9f9b-108">Remarks</span></span>  
 <span data-ttu-id="c9f9b-109">Não recomendamos o uso desse método, porque ele não retorna resultados consistentes.</span><span class="sxs-lookup"><span data-stu-id="c9f9b-109">We do not recommend the use of this method, because it does not return consistent results.</span></span> <span data-ttu-id="c9f9b-110">Para obter informações sobre a tabela GUID, consulte a documentação de infra-estrutura de linguagem comum (CLI), especialmente "partição II: metadados definição e semântica".</span><span class="sxs-lookup"><span data-stu-id="c9f9b-110">For information about the GUID table, see the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics".</span></span> <span data-ttu-id="c9f9b-111">A documentação está disponível online; confira [ECMA C# and Common Language Infrastructure Standards](http://go.microsoft.com/fwlink/?LinkID=99212), no MSDN, e [Standard ECMA-335 - Common Language Infrastructure (CLI)](http://go.microsoft.com/fwlink/?LinkID=65552), no site internacional da Ecma.</span><span class="sxs-lookup"><span data-stu-id="c9f9b-111">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](http://go.microsoft.com/fwlink/?LinkID=99212) on MSDN and [Standard ECMA-335 - Common Language Infrastructure (CLI)](http://go.microsoft.com/fwlink/?LinkID=65552) on the Ecma International Web site.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c9f9b-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c9f9b-112">Requirements</span></span>  
 <span data-ttu-id="c9f9b-113">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c9f9b-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c9f9b-114">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="c9f9b-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c9f9b-115">**Biblioteca:** usado como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="c9f9b-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c9f9b-116">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c9f9b-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9f9b-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c9f9b-117">See Also</span></span>  
 [<span data-ttu-id="c9f9b-118">Interface IMetaDataTables</span><span class="sxs-lookup"><span data-stu-id="c9f9b-118">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 [<span data-ttu-id="c9f9b-119">Interface IMetaDataTables2</span><span class="sxs-lookup"><span data-stu-id="c9f9b-119">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
