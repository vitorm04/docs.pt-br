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
ms.openlocfilehash: 3638ab12fc311ece9f24608cbb36219e10f01f2d
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501153"
---
# <a name="imetadatatablesgettableindex-method"></a><span data-ttu-id="11542-102">Método IMetaDataTables::GetTableIndex</span><span class="sxs-lookup"><span data-stu-id="11542-102">IMetaDataTables::GetTableIndex Method</span></span>
<span data-ttu-id="11542-103">Obtém o índice da tabela referenciada pelo token especificado.</span><span class="sxs-lookup"><span data-stu-id="11542-103">Gets the index for the table referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11542-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="11542-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTableIndex (  
    [in]  ULONG   token,  
    [out] ULONG   *pixTbl  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="11542-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="11542-105">Parameters</span></span>  
 `token`  
 <span data-ttu-id="11542-106">no O token que faz referência à tabela.</span><span class="sxs-lookup"><span data-stu-id="11542-106">[in] The token that references the table.</span></span>  
  
 `pixTbl`  
 <span data-ttu-id="11542-107">fora Um ponteiro para o índice retornado para a tabela referenciada.</span><span class="sxs-lookup"><span data-stu-id="11542-107">[out] A pointer to the returned index for the referenced table.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="11542-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="11542-108">Remarks</span></span>  
 <span data-ttu-id="11542-109">Não recomendamos o uso desse método, pois ele não retorna resultados consistentes.</span><span class="sxs-lookup"><span data-stu-id="11542-109">We do not recommend the use of this method, because it does not return consistent results.</span></span> <span data-ttu-id="11542-110">Para obter informações sobre a tabela de GUID, consulte a documentação de Common Language Infrastructure (CLI), especialmente "partição II: definição de metadados e semântica".</span><span class="sxs-lookup"><span data-stu-id="11542-110">For information about the GUID table, see the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics".</span></span> <span data-ttu-id="11542-111">A documentação está disponível online; consulte [padrões ECMA C# e Common Language Infrastructure](../../../standard/components.md#applicable-standards) e o [padrão ECMA-335-Common Language Infrastructure (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm).</span><span class="sxs-lookup"><span data-stu-id="11542-111">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](../../../standard/components.md#applicable-standards) and [Standard ECMA-335 - Common Language Infrastructure (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="11542-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="11542-112">Requirements</span></span>  
 <span data-ttu-id="11542-113">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="11542-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="11542-114">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="11542-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="11542-115">**Biblioteca:** Usado como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="11542-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="11542-116">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="11542-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11542-117">Confira também</span><span class="sxs-lookup"><span data-stu-id="11542-117">See also</span></span>

- [<span data-ttu-id="11542-118">Interface IMetaDataTables</span><span class="sxs-lookup"><span data-stu-id="11542-118">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="11542-119">Interface IMetaDataTables2</span><span class="sxs-lookup"><span data-stu-id="11542-119">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
