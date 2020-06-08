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
ms.openlocfilehash: 13d514157382c75a2eb9799837f9355d0e469c99
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84489893"
---
# <a name="imetadatatablesgetrow-method"></a><span data-ttu-id="c13b2-102">Método IMetaDataTables::GetRow</span><span class="sxs-lookup"><span data-stu-id="c13b2-102">IMetaDataTables::GetRow Method</span></span>
<span data-ttu-id="c13b2-103">Obtém a linha no índice de linha especificado, na tabela no índice de tabela especificado.</span><span class="sxs-lookup"><span data-stu-id="c13b2-103">Gets the row at the specified row index, in the table at the specified table index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c13b2-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c13b2-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRow (
    [in]  ULONG   ixTbl,  
    [in]  ULONG   rid,  
    [out] void    **ppRow  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c13b2-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c13b2-105">Parameters</span></span>  
 `ixTbl`  
 <span data-ttu-id="c13b2-106">no O índice da tabela da qual a linha será recuperada.</span><span class="sxs-lookup"><span data-stu-id="c13b2-106">[in] The index of the table from which the row will be retrieved.</span></span>  
  
 `rid`  
 <span data-ttu-id="c13b2-107">no O índice da linha a ser obtido.</span><span class="sxs-lookup"><span data-stu-id="c13b2-107">[in] The index of the row to get.</span></span>  
  
 `ppRow`  
 <span data-ttu-id="c13b2-108">fora Um ponteiro para um ponteiro para a linha.</span><span class="sxs-lookup"><span data-stu-id="c13b2-108">[out] A pointer to a pointer to the row.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c13b2-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="c13b2-109">Remarks</span></span>  

  <span data-ttu-id="c13b2-110">Não recomendamos o uso desse método, pois ele não retorna resultados consistentes.</span><span class="sxs-lookup"><span data-stu-id="c13b2-110">We do not recommend the use of this method, because it does not return consistent results.</span></span> <span data-ttu-id="c13b2-111">Para obter informações sobre a tabela de GUID, consulte a documentação de Common Language Infrastructure (CLI), especialmente "partição II: definição de metadados e semântica".</span><span class="sxs-lookup"><span data-stu-id="c13b2-111">For information about the GUID table, see the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics".</span></span> <span data-ttu-id="c13b2-112">A documentação está disponível online; consulte [padrões ECMA C# e Common Language Infrastructure](../../../standard/components.md#applicable-standards) e o [padrão ECMA-335-Common Language Infrastructure (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm).</span><span class="sxs-lookup"><span data-stu-id="c13b2-112">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](../../../standard/components.md#applicable-standards) and [Standard ECMA-335 - Common Language Infrastructure (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c13b2-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c13b2-113">Requirements</span></span>  
 <span data-ttu-id="c13b2-114">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c13b2-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c13b2-115">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="c13b2-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c13b2-116">**Biblioteca:** Usado como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="c13b2-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c13b2-117">**Versões do .NET Framework**  [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c13b2-117">**.NET Framework Versions**  [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c13b2-118">Confira também</span><span class="sxs-lookup"><span data-stu-id="c13b2-118">See also</span></span>

- [<span data-ttu-id="c13b2-119">Interface IMetaDataTables</span><span class="sxs-lookup"><span data-stu-id="c13b2-119">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="c13b2-120">Interface IMetaDataTables2</span><span class="sxs-lookup"><span data-stu-id="c13b2-120">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
