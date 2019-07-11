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
ms.openlocfilehash: c50740e59019edb44f6e8c2cee1b823fa047a039
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781434"
---
# <a name="imetadatatablesgetnextuserstring-method"></a><span data-ttu-id="0347e-102">Método IMetaDataTables::GetNextUserString</span><span class="sxs-lookup"><span data-stu-id="0347e-102">IMetaDataTables::GetNextUserString Method</span></span>
<span data-ttu-id="0347e-103">Obtém o índice da linha que contém a cadeia de caracteres embutidos Avançar na coluna da tabela atual.</span><span class="sxs-lookup"><span data-stu-id="0347e-103">Gets the index of the row that contains the next hard-coded string in the current table column.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0347e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0347e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNextUserString (  
    [in]  ULONG   ixUserString,  
    [out] ULONG   *pNext  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0347e-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0347e-105">Parameters</span></span>  
 `ixUserString`  
 <span data-ttu-id="0347e-106">[in] Um valor de índice da coluna de cadeia de caracteres atual.</span><span class="sxs-lookup"><span data-stu-id="0347e-106">[in] An index value from the current string column.</span></span>  
  
 `pNext`  
 <span data-ttu-id="0347e-107">[out] Um ponteiro para o índice da linha da próxima cadeia de caracteres na coluna.</span><span class="sxs-lookup"><span data-stu-id="0347e-107">[out] A pointer to the row index of the next string in the column.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0347e-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="0347e-108">Remarks</span></span>  
 <span data-ttu-id="0347e-109">Não recomendamos o uso desse método, porque ele não retorna resultados consistentes.</span><span class="sxs-lookup"><span data-stu-id="0347e-109">We do not recommend the use of this method, because it does not return consistent results.</span></span> <span data-ttu-id="0347e-110">Para obter informações sobre a tabela GUID, consulte a documentação de Common Language Infrastructure (CLI), especialmente "partição II: Definição de metadados e semântica".</span><span class="sxs-lookup"><span data-stu-id="0347e-110">For information about the GUID table, see the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics".</span></span> <span data-ttu-id="0347e-111">A documentação está disponível online; confira [ECMA C# and Common Language Infrastructure Standards](https://go.microsoft.com/fwlink/?LinkID=99212), no MSDN, e [Standard ECMA-335 - Common Language Infrastructure (CLI)](https://go.microsoft.com/fwlink/?LinkID=65552), no site internacional da Ecma.</span><span class="sxs-lookup"><span data-stu-id="0347e-111">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](https://go.microsoft.com/fwlink/?LinkID=99212) on MSDN and [Standard ECMA-335 - Common Language Infrastructure (CLI)](https://go.microsoft.com/fwlink/?LinkID=65552) on the Ecma International Web site.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0347e-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0347e-112">Requirements</span></span>  
 <span data-ttu-id="0347e-113">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0347e-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0347e-114">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="0347e-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0347e-115">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="0347e-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0347e-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0347e-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0347e-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0347e-117">See also</span></span>

- [<span data-ttu-id="0347e-118">Interface IMetaDataTables</span><span class="sxs-lookup"><span data-stu-id="0347e-118">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="0347e-119">Interface IMetaDataTables2</span><span class="sxs-lookup"><span data-stu-id="0347e-119">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
