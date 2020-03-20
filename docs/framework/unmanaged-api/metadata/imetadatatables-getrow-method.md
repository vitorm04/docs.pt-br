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
ms.openlocfilehash: 71f6c496816fec1a7537f5ccdfdc1b47d17da871
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177111"
---
# <a name="imetadatatablesgetrow-method"></a><span data-ttu-id="e7279-102">Método IMetaDataTables::GetRow</span><span class="sxs-lookup"><span data-stu-id="e7279-102">IMetaDataTables::GetRow Method</span></span>
<span data-ttu-id="e7279-103">Obtém a linha no índice de linha especificado, na tabela no índice de tabela especificado.</span><span class="sxs-lookup"><span data-stu-id="e7279-103">Gets the row at the specified row index, in the table at the specified table index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e7279-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e7279-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRow (
    [in]  ULONG   ixTbl,  
    [in]  ULONG   rid,  
    [out] void    **ppRow  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e7279-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="e7279-105">Parameters</span></span>  
 `ixTbl`  
 <span data-ttu-id="e7279-106">[em] O índice da tabela da qual a linha será recuperada.</span><span class="sxs-lookup"><span data-stu-id="e7279-106">[in] The index of the table from which the row will be retrieved.</span></span>  
  
 `rid`  
 <span data-ttu-id="e7279-107">[em] O índice da linha para obter.</span><span class="sxs-lookup"><span data-stu-id="e7279-107">[in] The index of the row to get.</span></span>  
  
 `ppRow`  
 <span data-ttu-id="e7279-108">[fora] Um ponteiro para um ponteiro para a linha.</span><span class="sxs-lookup"><span data-stu-id="e7279-108">[out] A pointer to a pointer to the row.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e7279-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="e7279-109">Remarks</span></span>  

  <span data-ttu-id="e7279-110">Não recomendamos o uso deste método, pois ele não retorna resultados consistentes.</span><span class="sxs-lookup"><span data-stu-id="e7279-110">We do not recommend the use of this method, because it does not return consistent results.</span></span> <span data-ttu-id="e7279-111">Para obter informações sobre a tabela GUID, consulte a documentação da Infra-estrutura de linguagem comum (CLI), especialmente "Partição II: Definição de Metadados e Semântica".</span><span class="sxs-lookup"><span data-stu-id="e7279-111">For information about the GUID table, see the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics".</span></span> <span data-ttu-id="e7279-112">A documentação está disponível online; consulte [ECMA C# e Padrões de infra-estrutura de linguagem comum](../../../standard/components.md#applicable-standards) e [Padrão ECMA-335 - Infra-estrutura de linguagem comum (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm).</span><span class="sxs-lookup"><span data-stu-id="e7279-112">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](../../../standard/components.md#applicable-standards) and [Standard ECMA-335 - Common Language Infrastructure (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e7279-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e7279-113">Requirements</span></span>  
 <span data-ttu-id="e7279-114">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e7279-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e7279-115">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="e7279-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e7279-116">**Biblioteca:** Usado como recurso em MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e7279-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e7279-117">**.NET Framework Versions**  [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e7279-117">**.NET Framework Versions**  [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7279-118">Confira também</span><span class="sxs-lookup"><span data-stu-id="e7279-118">See also</span></span>

- [<span data-ttu-id="e7279-119">Interface IMetaDataTables</span><span class="sxs-lookup"><span data-stu-id="e7279-119">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="e7279-120">Interface IMetaDataTables2</span><span class="sxs-lookup"><span data-stu-id="e7279-120">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
