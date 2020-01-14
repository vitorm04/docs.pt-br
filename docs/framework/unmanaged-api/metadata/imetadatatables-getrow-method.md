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
ms.openlocfilehash: 9ac6eba18ae23dc80a8dc90383aa67cfe41b39ff
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937400"
---
# <a name="imetadatatablesgetrow-method"></a><span data-ttu-id="067f0-102">Método IMetaDataTables::GetRow</span><span class="sxs-lookup"><span data-stu-id="067f0-102">IMetaDataTables::GetRow Method</span></span>
<span data-ttu-id="067f0-103">Obtém a linha no índice de linha especificado, na tabela no índice de tabela especificado.</span><span class="sxs-lookup"><span data-stu-id="067f0-103">Gets the row at the specified row index, in the table at the specified table index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="067f0-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="067f0-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRow (   
    [in]  ULONG   ixTbl,  
    [in]  ULONG   rid,  
    [out] void    **ppRow  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="067f0-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="067f0-105">Parameters</span></span>  
 `ixTbl`  
 <span data-ttu-id="067f0-106">no O índice da tabela da qual a linha será recuperada.</span><span class="sxs-lookup"><span data-stu-id="067f0-106">[in] The index of the table from which the row will be retrieved.</span></span>  
  
 `rid`  
 <span data-ttu-id="067f0-107">no O índice da linha a ser obtido.</span><span class="sxs-lookup"><span data-stu-id="067f0-107">[in] The index of the row to get.</span></span>  
  
 `ppRow`  
 <span data-ttu-id="067f0-108">fora Um ponteiro para um ponteiro para a linha.</span><span class="sxs-lookup"><span data-stu-id="067f0-108">[out] A pointer to a pointer to the row.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="067f0-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="067f0-109">Remarks</span></span>  

  <span data-ttu-id="067f0-110">Não recomendamos o uso desse método, pois ele não retorna resultados consistentes.</span><span class="sxs-lookup"><span data-stu-id="067f0-110">We do not recommend the use of this method, because it does not return consistent results.</span></span> <span data-ttu-id="067f0-111">Para obter informações sobre a tabela de GUID, consulte a documentação de Common Language Infrastructure (CLI), especialmente "partição II: definição de metadados e semântica".</span><span class="sxs-lookup"><span data-stu-id="067f0-111">For information about the GUID table, see the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics".</span></span> <span data-ttu-id="067f0-112">A documentação está disponível online; consulte [padrões C# ECMA e Common Language Infrastructure](../../../standard/components.md#applicable-standards) e [a CLI (Standard ECMA-335-Common Language Infrastructure)](http://www.ecma-international.org/publications/standards/Ecma-335.htm).</span><span class="sxs-lookup"><span data-stu-id="067f0-112">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](../../../standard/components.md#applicable-standards) and [Standard ECMA-335 - Common Language Infrastructure (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="067f0-113">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="067f0-113">Requirements</span></span>  
 <span data-ttu-id="067f0-114">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="067f0-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="067f0-115">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="067f0-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="067f0-116">**Biblioteca:** Usado como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="067f0-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="067f0-117">**Versões de .NET Framework**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="067f0-117">**.NET Framework Versions**  [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="067f0-118">Veja também</span><span class="sxs-lookup"><span data-stu-id="067f0-118">See also</span></span>

- [<span data-ttu-id="067f0-119">Interface IMetaDataTables</span><span class="sxs-lookup"><span data-stu-id="067f0-119">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="067f0-120">Interface IMetaDataTables2</span><span class="sxs-lookup"><span data-stu-id="067f0-120">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
