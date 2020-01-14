---
title: Método IMetaDataTables::GetNextUserString
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetNextUserString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetNextUserString
helpviewer_keywords:
- GetNextUserString method [.NET Framework metadata]
- IMetaDataTables::GetNextUserString method [.NET Framework metadata]
ms.assetid: b7cb40ee-67b7-4f4e-8dcc-ee7ac8bc986b
topic_type:
- apiref
ms.openlocfilehash: 6522dbc8e49d612fc4c0d9597a9b5f12edb2cfe1
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937781"
---
# <a name="imetadatatablesgetnextuserstring-method"></a><span data-ttu-id="d6744-102">Método IMetaDataTables::GetNextUserString</span><span class="sxs-lookup"><span data-stu-id="d6744-102">IMetaDataTables::GetNextUserString Method</span></span>
<span data-ttu-id="d6744-103">Obtém o índice da linha que contém a próxima cadeia de caracteres embutida em código na coluna da tabela atual.</span><span class="sxs-lookup"><span data-stu-id="d6744-103">Gets the index of the row that contains the next hard-coded string in the current table column.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6744-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d6744-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNextUserString (  
    [in]  ULONG   ixUserString,  
    [out] ULONG   *pNext  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d6744-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d6744-105">Parameters</span></span>  
 `ixUserString`  
 <span data-ttu-id="d6744-106">no Um valor de índice da coluna de cadeia de caracteres atual.</span><span class="sxs-lookup"><span data-stu-id="d6744-106">[in] An index value from the current string column.</span></span>  
  
 `pNext`  
 <span data-ttu-id="d6744-107">fora Um ponteiro para o índice de linha da próxima cadeia de caracteres na coluna.</span><span class="sxs-lookup"><span data-stu-id="d6744-107">[out] A pointer to the row index of the next string in the column.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d6744-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="d6744-108">Remarks</span></span>  
 <span data-ttu-id="d6744-109">Não recomendamos o uso desse método, pois ele não retorna resultados consistentes.</span><span class="sxs-lookup"><span data-stu-id="d6744-109">We do not recommend the use of this method, because it does not return consistent results.</span></span> <span data-ttu-id="d6744-110">Para obter informações sobre a tabela de GUID, consulte a documentação de Common Language Infrastructure (CLI), especialmente "partição II: definição de metadados e semântica".</span><span class="sxs-lookup"><span data-stu-id="d6744-110">For information about the GUID table, see the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics".</span></span> <span data-ttu-id="d6744-111">A documentação está disponível online; consulte [padrões C# ECMA e Common Language Infrastructure](../../../standard/components.md#applicable-standards) e [a CLI (Standard ECMA-335-Common Language Infrastructure)](http://www.ecma-international.org/publications/standards/Ecma-335.htm).</span><span class="sxs-lookup"><span data-stu-id="d6744-111">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](../../../standard/components.md#applicable-standards) and [Standard ECMA-335 - Common Language Infrastructure (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d6744-112">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="d6744-112">Requirements</span></span>  
 <span data-ttu-id="d6744-113">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d6744-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d6744-114">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="d6744-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d6744-115">**Biblioteca:** Usado como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="d6744-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d6744-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d6744-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6744-117">Veja também</span><span class="sxs-lookup"><span data-stu-id="d6744-117">See also</span></span>

- [<span data-ttu-id="d6744-118">Interface IMetaDataTables</span><span class="sxs-lookup"><span data-stu-id="d6744-118">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="d6744-119">Interface IMetaDataTables2</span><span class="sxs-lookup"><span data-stu-id="d6744-119">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
