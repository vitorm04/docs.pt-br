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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6f5e4a36f633b215faaf5930cd2487c26c1d5ce3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54696224"
---
# <a name="imetadatatablesgetnextuserstring-method"></a><span data-ttu-id="13684-102">Método IMetaDataTables::GetNextUserString</span><span class="sxs-lookup"><span data-stu-id="13684-102">IMetaDataTables::GetNextUserString Method</span></span>
<span data-ttu-id="13684-103">Obtém o índice da linha que contém a cadeia de caracteres embutidos Avançar na coluna da tabela atual.</span><span class="sxs-lookup"><span data-stu-id="13684-103">Gets the index of the row that contains the next hard-coded string in the current table column.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13684-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="13684-104">Syntax</span></span>  
  
```  
HRESULT GetNextUserString (  
    [in]  ULONG   ixUserString,  
    [out] ULONG   *pNext  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="13684-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="13684-105">Parameters</span></span>  
 `ixUserString`  
 <span data-ttu-id="13684-106">[in] Um valor de índice da coluna de cadeia de caracteres atual.</span><span class="sxs-lookup"><span data-stu-id="13684-106">[in] An index value from the current string column.</span></span>  
  
 `pNext`  
 <span data-ttu-id="13684-107">[out] Um ponteiro para o índice da linha da próxima cadeia de caracteres na coluna.</span><span class="sxs-lookup"><span data-stu-id="13684-107">[out] A pointer to the row index of the next string in the column.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="13684-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="13684-108">Remarks</span></span>  
 <span data-ttu-id="13684-109">Não recomendamos o uso desse método, porque ele não retorna resultados consistentes.</span><span class="sxs-lookup"><span data-stu-id="13684-109">We do not recommend the use of this method, because it does not return consistent results.</span></span> <span data-ttu-id="13684-110">Para obter informações sobre a tabela GUID, consulte a documentação de Common Language Infrastructure (CLI), especialmente "partição II: Definição de metadados e semântica".</span><span class="sxs-lookup"><span data-stu-id="13684-110">For information about the GUID table, see the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics".</span></span> <span data-ttu-id="13684-111">A documentação está disponível online; confira [ECMA C# and Common Language Infrastructure Standards](https://go.microsoft.com/fwlink/?LinkID=99212), no MSDN, e [Standard ECMA-335 - Common Language Infrastructure (CLI)](https://go.microsoft.com/fwlink/?LinkID=65552), no site internacional da Ecma.</span><span class="sxs-lookup"><span data-stu-id="13684-111">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](https://go.microsoft.com/fwlink/?LinkID=99212) on MSDN and [Standard ECMA-335 - Common Language Infrastructure (CLI)](https://go.microsoft.com/fwlink/?LinkID=65552) on the Ecma International Web site.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="13684-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="13684-112">Requirements</span></span>  
 <span data-ttu-id="13684-113">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="13684-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="13684-114">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="13684-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="13684-115">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="13684-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="13684-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="13684-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13684-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="13684-117">See also</span></span>
- [<span data-ttu-id="13684-118">Interface IMetaDataTables</span><span class="sxs-lookup"><span data-stu-id="13684-118">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="13684-119">Interface IMetaDataTables2</span><span class="sxs-lookup"><span data-stu-id="13684-119">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
