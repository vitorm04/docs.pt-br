---
title: Método IMetaDataTables::GetRow
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetRow
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetRow
helpviewer_keywords:
- IMetaDataTables::GetRow method [.NET Framework metadata]
- GetRow method [.NET Framework metadata]
ms.assetid: a7408d51-0bce-45a2-b58f-da4660bbc039
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 98fc95c618a7a06f5e6c219d7707af291770c06a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781408"
---
# <a name="imetadatatablesgetrow-method"></a><span data-ttu-id="58bc1-102">Método IMetaDataTables::GetRow</span><span class="sxs-lookup"><span data-stu-id="58bc1-102">IMetaDataTables::GetRow Method</span></span>
<span data-ttu-id="58bc1-103">Obtém a linha no índice de linha especificada na tabela do índice da tabela especificada.</span><span class="sxs-lookup"><span data-stu-id="58bc1-103">Gets the row at the specified row index, in the table at the specified table index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58bc1-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="58bc1-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRow (   
    [in]  ULONG   ixTbl,  
    [in]  ULONG   rid,  
    [out] void    **ppRow  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="58bc1-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="58bc1-105">Parameters</span></span>  
 `ixTbl`  
 <span data-ttu-id="58bc1-106">[in] O índice da tabela da qual a linha será recuperada.</span><span class="sxs-lookup"><span data-stu-id="58bc1-106">[in] The index of the table from which the row will be retrieved.</span></span>  
  
 `rid`  
 <span data-ttu-id="58bc1-107">[in] O índice da linha para obter.</span><span class="sxs-lookup"><span data-stu-id="58bc1-107">[in] The index of the row to get.</span></span>  
  
 `ppRow`  
 <span data-ttu-id="58bc1-108">[out] Um ponteiro para um ponteiro para a linha.</span><span class="sxs-lookup"><span data-stu-id="58bc1-108">[out] A pointer to a pointer to the row.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="58bc1-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="58bc1-109">Remarks</span></span>  
 <span data-ttu-id="58bc1-110">Não recomendamos o uso desse método, porque ele não retorna resultados consistentes.</span><span class="sxs-lookup"><span data-stu-id="58bc1-110">We do not recommend the use of this method, because it does not return consistent results.</span></span> <span data-ttu-id="58bc1-111">Para obter informações sobre a tabela GUID, consulte a documentação de Common Language Infrastructure (CLI), especialmente "partição II: Definição de metadados e semântica".</span><span class="sxs-lookup"><span data-stu-id="58bc1-111">For information about the GUID table, see the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics".</span></span> <span data-ttu-id="58bc1-112">A documentação está disponível online; confira [ECMA C# and Common Language Infrastructure Standards](https://go.microsoft.com/fwlink/?LinkID=99212), no MSDN, e [Standard ECMA-335 - Common Language Infrastructure (CLI)](https://go.microsoft.com/fwlink/?LinkID=65552), no site internacional da Ecma.</span><span class="sxs-lookup"><span data-stu-id="58bc1-112">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](https://go.microsoft.com/fwlink/?LinkID=99212) on MSDN and [Standard ECMA-335 - Common Language Infrastructure (CLI)](https://go.microsoft.com/fwlink/?LinkID=65552) on the Ecma International Web site.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="58bc1-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="58bc1-113">Requirements</span></span>  
 <span data-ttu-id="58bc1-114">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="58bc1-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="58bc1-115">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="58bc1-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="58bc1-116">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="58bc1-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="58bc1-117">**Versões do .NET framework**  [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="58bc1-117">**.NET Framework Versions**  [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58bc1-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="58bc1-118">See also</span></span>

- [<span data-ttu-id="58bc1-119">Interface IMetaDataTables</span><span class="sxs-lookup"><span data-stu-id="58bc1-119">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="58bc1-120">Interface IMetaDataTables2</span><span class="sxs-lookup"><span data-stu-id="58bc1-120">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
