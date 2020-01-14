---
title: Método IMetaDataTables::GetTableIndex
ms.date: 03/30/2017
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
ms.openlocfilehash: d3e056bc93c2faf2b1509536b8d8d4df6886dd20
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937376"
---
# <a name="imetadatatablesgettableindex-method"></a><span data-ttu-id="5ddac-102">Método IMetaDataTables::GetTableIndex</span><span class="sxs-lookup"><span data-stu-id="5ddac-102">IMetaDataTables::GetTableIndex Method</span></span>
<span data-ttu-id="5ddac-103">Obtém o índice da tabela referenciada pelo token especificado.</span><span class="sxs-lookup"><span data-stu-id="5ddac-103">Gets the index for the table referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ddac-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5ddac-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTableIndex (  
    [in]  ULONG   token,  
    [out] ULONG   *pixTbl  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5ddac-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5ddac-105">Parameters</span></span>  
 `token`  
 <span data-ttu-id="5ddac-106">no O token que faz referência à tabela.</span><span class="sxs-lookup"><span data-stu-id="5ddac-106">[in] The token that references the table.</span></span>  
  
 `pixTbl`  
 <span data-ttu-id="5ddac-107">fora Um ponteiro para o índice retornado para a tabela referenciada.</span><span class="sxs-lookup"><span data-stu-id="5ddac-107">[out] A pointer to the returned index for the referenced table.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5ddac-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="5ddac-108">Remarks</span></span>  
 <span data-ttu-id="5ddac-109">Não recomendamos o uso desse método, pois ele não retorna resultados consistentes.</span><span class="sxs-lookup"><span data-stu-id="5ddac-109">We do not recommend the use of this method, because it does not return consistent results.</span></span> <span data-ttu-id="5ddac-110">Para obter informações sobre a tabela de GUID, consulte a documentação de Common Language Infrastructure (CLI), especialmente "partição II: definição de metadados e semântica".</span><span class="sxs-lookup"><span data-stu-id="5ddac-110">For information about the GUID table, see the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics".</span></span> <span data-ttu-id="5ddac-111">A documentação está disponível online; consulte [padrões C# ECMA e Common Language Infrastructure](../../../standard/components.md#applicable-standards) e [a CLI (Standard ECMA-335-Common Language Infrastructure)](http://www.ecma-international.org/publications/standards/Ecma-335.htm).</span><span class="sxs-lookup"><span data-stu-id="5ddac-111">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](../../../standard/components.md#applicable-standards) and [Standard ECMA-335 - Common Language Infrastructure (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5ddac-112">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="5ddac-112">Requirements</span></span>  
 <span data-ttu-id="5ddac-113">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5ddac-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5ddac-114">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="5ddac-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5ddac-115">**Biblioteca:** Usado como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="5ddac-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="5ddac-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5ddac-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ddac-117">Veja também</span><span class="sxs-lookup"><span data-stu-id="5ddac-117">See also</span></span>

- [<span data-ttu-id="5ddac-118">Interface IMetaDataTables</span><span class="sxs-lookup"><span data-stu-id="5ddac-118">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="5ddac-119">Interface IMetaDataTables2</span><span class="sxs-lookup"><span data-stu-id="5ddac-119">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
