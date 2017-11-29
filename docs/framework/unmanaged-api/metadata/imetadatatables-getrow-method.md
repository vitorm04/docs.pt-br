---
title: "Método IMetaDataTables::GetRow"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataTables.GetRow
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataTables::GetRow
helpviewer_keywords:
- IMetaDataTables::GetRow method [.NET Framework metadata]
- GetRow method [.NET Framework metadata]
ms.assetid: a7408d51-0bce-45a2-b58f-da4660bbc039
topic_type: apiref
caps.latest.revision: "16"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 281824ace7696ab0fc6b3a96e0cdf307a9419313
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadatatablesgetrow-method"></a><span data-ttu-id="352c4-102">Método IMetaDataTables::GetRow</span><span class="sxs-lookup"><span data-stu-id="352c4-102">IMetaDataTables::GetRow Method</span></span>
<span data-ttu-id="352c4-103">Obtém a linha no índice de linha especificada na tabela do índice da tabela especificada.</span><span class="sxs-lookup"><span data-stu-id="352c4-103">Gets the row at the specified row index, in the table at the specified table index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="352c4-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="352c4-104">Syntax</span></span>  
  
```  
HRESULT GetRow (   
    [in]  ULONG   ixTbl,  
    [in]  ULONG   rid,  
    [out] void    **ppRow  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="352c4-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="352c4-105">Parameters</span></span>  
 `ixTbl`  
 <span data-ttu-id="352c4-106">[in] O índice da tabela da qual a linha será recuperada.</span><span class="sxs-lookup"><span data-stu-id="352c4-106">[in] The index of the table from which the row will be retrieved.</span></span>  
  
 `rid`  
 <span data-ttu-id="352c4-107">[in] O índice da linha para obter.</span><span class="sxs-lookup"><span data-stu-id="352c4-107">[in] The index of the row to get.</span></span>  
  
 `ppRow`  
 <span data-ttu-id="352c4-108">[out] Um ponteiro para um ponteiro para a linha.</span><span class="sxs-lookup"><span data-stu-id="352c4-108">[out] A pointer to a pointer to the row.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="352c4-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="352c4-109">Remarks</span></span>  
 <span data-ttu-id="352c4-110">Não recomendamos o uso desse método, porque ele não retorna resultados consistentes.</span><span class="sxs-lookup"><span data-stu-id="352c4-110">We do not recommend the use of this method, because it does not return consistent results.</span></span> <span data-ttu-id="352c4-111">Para obter informações sobre a tabela GUID, consulte a documentação de infra-estrutura de linguagem comum (CLI), especialmente "partição II: metadados definição e semântica".</span><span class="sxs-lookup"><span data-stu-id="352c4-111">For information about the GUID table, see the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics".</span></span> <span data-ttu-id="352c4-112">A documentação está disponível online; confira [ECMA C# and Common Language Infrastructure Standards](http://go.microsoft.com/fwlink/?LinkID=99212), no MSDN, e [Standard ECMA-335 - Common Language Infrastructure (CLI)](http://go.microsoft.com/fwlink/?LinkID=65552), no site internacional da Ecma.</span><span class="sxs-lookup"><span data-stu-id="352c4-112">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](http://go.microsoft.com/fwlink/?LinkID=99212) on MSDN and [Standard ECMA-335 - Common Language Infrastructure (CLI)](http://go.microsoft.com/fwlink/?LinkID=65552) on the Ecma International Web site.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="352c4-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="352c4-113">Requirements</span></span>  
 <span data-ttu-id="352c4-114">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="352c4-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="352c4-115">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="352c4-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="352c4-116">**Biblioteca:** usado como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="352c4-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="352c4-117">**Versões do .NET framework**  [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="352c4-117">**.NET Framework Versions**  [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="352c4-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="352c4-118">See Also</span></span>  
 [<span data-ttu-id="352c4-119">Interface IMetaDataTables</span><span class="sxs-lookup"><span data-stu-id="352c4-119">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 [<span data-ttu-id="352c4-120">Interface IMetaDataTables2</span><span class="sxs-lookup"><span data-stu-id="352c4-120">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
