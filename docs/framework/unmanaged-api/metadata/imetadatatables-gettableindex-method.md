---
title: "Método IMetaDataTables::GetTableIndex"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IMetaDataTables.GetTableIndex
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetTableIndex
helpviewer_keywords:
- GetTableIndex method [.NET Framework metadata]
- IMetaDataTables::GetTableIndex method [.NET Framework metadata]
ms.assetid: c6ec3800-e0d9-4387-afb8-ddc0b818114c
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9d2e51b9975748642d66e5b5104dc24936b4a7e0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadatatablesgettableindex-method"></a><span data-ttu-id="9b6dd-102">Método IMetaDataTables::GetTableIndex</span><span class="sxs-lookup"><span data-stu-id="9b6dd-102">IMetaDataTables::GetTableIndex Method</span></span>
<span data-ttu-id="9b6dd-103">Obtém o índice para a tabela referenciada pelo token especificado.</span><span class="sxs-lookup"><span data-stu-id="9b6dd-103">Gets the index for the table referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b6dd-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9b6dd-104">Syntax</span></span>  
  
```  
HRESULT GetTableIndex (  
    [in]  ULONG   token,  
    [out] ULONG   *pixTbl  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9b6dd-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="9b6dd-105">Parameters</span></span>  
 `token`  
 <span data-ttu-id="9b6dd-106">[in] O token que faz referência à tabela.</span><span class="sxs-lookup"><span data-stu-id="9b6dd-106">[in] The token that references the table.</span></span>  
  
 `pixTbl`  
 <span data-ttu-id="9b6dd-107">[out] Um ponteiro para o índice retornado para a tabela referenciada.</span><span class="sxs-lookup"><span data-stu-id="9b6dd-107">[out] A pointer to the returned index for the referenced table.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9b6dd-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="9b6dd-108">Remarks</span></span>  
 <span data-ttu-id="9b6dd-109">Não recomendamos o uso desse método, porque ele não retorna resultados consistentes.</span><span class="sxs-lookup"><span data-stu-id="9b6dd-109">We do not recommend the use of this method, because it does not return consistent results.</span></span> <span data-ttu-id="9b6dd-110">Para obter informações sobre a tabela GUID, consulte a documentação de infra-estrutura de linguagem comum (CLI), especialmente "partição II: metadados definição e semântica".</span><span class="sxs-lookup"><span data-stu-id="9b6dd-110">For information about the GUID table, see the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics".</span></span> <span data-ttu-id="9b6dd-111">A documentação está disponível online; confira [ECMA C# and Common Language Infrastructure Standards](http://go.microsoft.com/fwlink/?LinkID=99212), no MSDN, e [Standard ECMA-335 - Common Language Infrastructure (CLI)](http://go.microsoft.com/fwlink/?LinkID=65552), no site internacional da Ecma.</span><span class="sxs-lookup"><span data-stu-id="9b6dd-111">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](http://go.microsoft.com/fwlink/?LinkID=99212) on MSDN and [Standard ECMA-335 - Common Language Infrastructure (CLI)](http://go.microsoft.com/fwlink/?LinkID=65552) on the Ecma International Web site.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9b6dd-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9b6dd-112">Requirements</span></span>  
 <span data-ttu-id="9b6dd-113">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9b6dd-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9b6dd-114">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="9b6dd-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9b6dd-115">**Biblioteca:** usado como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="9b6dd-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9b6dd-116">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9b6dd-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b6dd-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9b6dd-117">See Also</span></span>  
 [<span data-ttu-id="9b6dd-118">Interface IMetaDataTables</span><span class="sxs-lookup"><span data-stu-id="9b6dd-118">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 [<span data-ttu-id="9b6dd-119">Interface IMetaDataTables2</span><span class="sxs-lookup"><span data-stu-id="9b6dd-119">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
