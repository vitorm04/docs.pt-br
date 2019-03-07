---
title: Método IMetaDataTables::GetNextGuid
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetNextGuid
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetNextGuid
helpviewer_keywords:
- GetNextGuid method [.NET Framework metadata]
- IMetaDataTables::GetNextGuid method [.NET Framework metadata]
ms.assetid: 68f6ea4d-9112-4d6b-93d9-e34f1e2f2496
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 872f5a9eaa17a777cfbb14fea34cc80e0b7c04ad
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57487468"
---
# <a name="imetadatatablesgetnextguid-method"></a><span data-ttu-id="c6da2-102">Método IMetaDataTables::GetNextGuid</span><span class="sxs-lookup"><span data-stu-id="c6da2-102">IMetaDataTables::GetNextGuid Method</span></span>
<span data-ttu-id="c6da2-103">Obtém o índice do próximo valor GUID na coluna da tabela atual.</span><span class="sxs-lookup"><span data-stu-id="c6da2-103">Gets the index of the next GUID value in the current table column.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c6da2-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c6da2-104">Syntax</span></span>  
  
```  
HRESULT GetNextGuid (  
    [in]  ULONG   ixGuid,  
    [out] ULONG   *pNext  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c6da2-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c6da2-105">Parameters</span></span>  
 `ixGuid`  
 <span data-ttu-id="c6da2-106">[in] O valor de índice de uma coluna de tabela do GUID.</span><span class="sxs-lookup"><span data-stu-id="c6da2-106">[in] The index value from a GUID table column.</span></span>  
  
 `pNext`  
 <span data-ttu-id="c6da2-107">[out] Um ponteiro para o índice do próximo valor GUID.</span><span class="sxs-lookup"><span data-stu-id="c6da2-107">[out] A pointer to the index of the next GUID value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c6da2-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="c6da2-108">Remarks</span></span>  
 <span data-ttu-id="c6da2-109">Não recomendamos o uso desse método, porque ele não retorna resultados consistentes.</span><span class="sxs-lookup"><span data-stu-id="c6da2-109">We do not recommend the use of this method, because it does not return consistent results.</span></span> <span data-ttu-id="c6da2-110">Para obter informações sobre a tabela GUID, consulte a documentação de Common Language Infrastructure (CLI), especialmente "partição II: Definição de metadados e semântica".</span><span class="sxs-lookup"><span data-stu-id="c6da2-110">For information about the GUID table, see the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics".</span></span> <span data-ttu-id="c6da2-111">A documentação está disponível online; confira [ECMA C# and Common Language Infrastructure Standards](https://go.microsoft.com/fwlink/?LinkID=99212), no MSDN, e [Standard ECMA-335 - Common Language Infrastructure (CLI)](https://go.microsoft.com/fwlink/?LinkID=65552), no site internacional da Ecma.</span><span class="sxs-lookup"><span data-stu-id="c6da2-111">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](https://go.microsoft.com/fwlink/?LinkID=99212) on MSDN and [Standard ECMA-335 - Common Language Infrastructure (CLI)](https://go.microsoft.com/fwlink/?LinkID=65552) on the Ecma International Web site.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c6da2-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c6da2-112">Requirements</span></span>  
 <span data-ttu-id="c6da2-113">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c6da2-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c6da2-114">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="c6da2-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c6da2-115">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="c6da2-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c6da2-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c6da2-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6da2-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c6da2-117">See also</span></span>
- [<span data-ttu-id="c6da2-118">Interface IMetaDataTables</span><span class="sxs-lookup"><span data-stu-id="c6da2-118">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="c6da2-119">Interface IMetaDataTables2</span><span class="sxs-lookup"><span data-stu-id="c6da2-119">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
