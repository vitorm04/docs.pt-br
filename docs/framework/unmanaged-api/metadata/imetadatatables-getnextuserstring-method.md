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
ms.openlocfilehash: 7b9e729732175b7249e4d3be91996bc5e4050855
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33450200"
---
# <a name="imetadatatablesgetnextuserstring-method"></a><span data-ttu-id="1ad9b-102">Método IMetaDataTables::GetNextUserString</span><span class="sxs-lookup"><span data-stu-id="1ad9b-102">IMetaDataTables::GetNextUserString Method</span></span>
<span data-ttu-id="1ad9b-103">Obtém o índice da linha que contém a cadeia de caracteres codificada Avançar na coluna da tabela atual.</span><span class="sxs-lookup"><span data-stu-id="1ad9b-103">Gets the index of the row that contains the next hard-coded string in the current table column.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ad9b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1ad9b-104">Syntax</span></span>  
  
```  
HRESULT GetNextUserString (  
    [in]  ULONG   ixUserString,  
    [out] ULONG   *pNext  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1ad9b-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="1ad9b-105">Parameters</span></span>  
 `ixUserString`  
 <span data-ttu-id="1ad9b-106">[in] Um valor de índice da coluna de cadeia de caracteres atual.</span><span class="sxs-lookup"><span data-stu-id="1ad9b-106">[in] An index value from the current string column.</span></span>  
  
 `pNext`  
 <span data-ttu-id="1ad9b-107">[out] Um ponteiro para o índice de linha da próxima cadeia de caracteres na coluna.</span><span class="sxs-lookup"><span data-stu-id="1ad9b-107">[out] A pointer to the row index of the next string in the column.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1ad9b-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="1ad9b-108">Remarks</span></span>  
 <span data-ttu-id="1ad9b-109">Não recomendamos o uso desse método, porque ele não retorna resultados consistentes.</span><span class="sxs-lookup"><span data-stu-id="1ad9b-109">We do not recommend the use of this method, because it does not return consistent results.</span></span> <span data-ttu-id="1ad9b-110">Para obter informações sobre a tabela GUID, consulte a documentação de infra-estrutura de linguagem comum (CLI), especialmente "partição II: metadados definição e semântica".</span><span class="sxs-lookup"><span data-stu-id="1ad9b-110">For information about the GUID table, see the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics".</span></span> <span data-ttu-id="1ad9b-111">A documentação está disponível online; confira [ECMA C# and Common Language Infrastructure Standards](http://go.microsoft.com/fwlink/?LinkID=99212), no MSDN, e [Standard ECMA-335 - Common Language Infrastructure (CLI)](http://go.microsoft.com/fwlink/?LinkID=65552), no site internacional da Ecma.</span><span class="sxs-lookup"><span data-stu-id="1ad9b-111">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](http://go.microsoft.com/fwlink/?LinkID=99212) on MSDN and [Standard ECMA-335 - Common Language Infrastructure (CLI)](http://go.microsoft.com/fwlink/?LinkID=65552) on the Ecma International Web site.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1ad9b-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1ad9b-112">Requirements</span></span>  
 <span data-ttu-id="1ad9b-113">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1ad9b-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1ad9b-114">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="1ad9b-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1ad9b-115">**Biblioteca:** usado como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="1ad9b-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1ad9b-116">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1ad9b-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ad9b-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1ad9b-117">See Also</span></span>  
 [<span data-ttu-id="1ad9b-118">Interface IMetaDataTables</span><span class="sxs-lookup"><span data-stu-id="1ad9b-118">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 [<span data-ttu-id="1ad9b-119">Interface IMetaDataTables2</span><span class="sxs-lookup"><span data-stu-id="1ad9b-119">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
