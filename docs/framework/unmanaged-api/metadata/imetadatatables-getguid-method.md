---
title: Método IMetaDataTables::GetGuid
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetGuid
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetGuid
helpviewer_keywords:
- GetGuid method [.NET Framework metadata]
- IMetaDataTables::GetGuid method [.NET Framework metadata]
ms.assetid: a3546316-e24d-417f-9909-e45d42c9d471
topic_type:
- apiref
ms.openlocfilehash: 57df124f15f78daad053d9634e1baa969a65cc35
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175272"
---
# <a name="imetadatatablesgetguid-method"></a><span data-ttu-id="17bd4-102">Método IMetaDataTables::GetGuid</span><span class="sxs-lookup"><span data-stu-id="17bd4-102">IMetaDataTables::GetGuid Method</span></span>
<span data-ttu-id="17bd4-103">Obtém um GUID da linha no índice especificado.</span><span class="sxs-lookup"><span data-stu-id="17bd4-103">Gets a GUID from the row at the specified index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="17bd4-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="17bd4-104">Syntax</span></span>  
  
```cpp  
HRESULT GetGuid (
    [in]  ULONG       ixGuid,  
    [out] const GUID  **ppGUID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="17bd4-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="17bd4-105">Parameters</span></span>  
 `ixGuid`  
 <span data-ttu-id="17bd4-106">[em] O índice da linha a partir do qual obter o GUID.</span><span class="sxs-lookup"><span data-stu-id="17bd4-106">[in] The index of the row from which to get the GUID.</span></span>  
  
 `ppGuid`  
 <span data-ttu-id="17bd4-107">[fora] Um ponteiro para um ponteiro para o GUID.</span><span class="sxs-lookup"><span data-stu-id="17bd4-107">[out] A pointer to a pointer to the GUID.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="17bd4-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="17bd4-108">Remarks</span></span>  

  <span data-ttu-id="17bd4-109">Não recomendamos o uso deste método, pois ele não retorna resultados consistentes.</span><span class="sxs-lookup"><span data-stu-id="17bd4-109">We do not recommend the use of this method, because it does not return consistent results.</span></span> <span data-ttu-id="17bd4-110">Para obter informações sobre a tabela GUID, consulte a documentação da Infra-estrutura de linguagem comum (CLI), especialmente "Partição II: Definição de Metadados e Semântica".</span><span class="sxs-lookup"><span data-stu-id="17bd4-110">For information about the GUID table, see the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics".</span></span> <span data-ttu-id="17bd4-111">A documentação está disponível online; consulte [ECMA C# e Padrões de infra-estrutura de linguagem comum](../../../standard/components.md#applicable-standards) e [Padrão ECMA-335 - Infra-estrutura de linguagem comum (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm).</span><span class="sxs-lookup"><span data-stu-id="17bd4-111">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](../../../standard/components.md#applicable-standards) and [Standard ECMA-335 - Common Language Infrastructure (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="17bd4-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="17bd4-112">Requirements</span></span>  
 <span data-ttu-id="17bd4-113">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="17bd4-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="17bd4-114">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="17bd4-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="17bd4-115">**Biblioteca:** Usado como recurso em MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="17bd4-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="17bd4-116">**.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="17bd4-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17bd4-117">Confira também</span><span class="sxs-lookup"><span data-stu-id="17bd4-117">See also</span></span>

- [<span data-ttu-id="17bd4-118">Interface IMetaDataTables</span><span class="sxs-lookup"><span data-stu-id="17bd4-118">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="17bd4-119">Interface IMetaDataTables2</span><span class="sxs-lookup"><span data-stu-id="17bd4-119">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
