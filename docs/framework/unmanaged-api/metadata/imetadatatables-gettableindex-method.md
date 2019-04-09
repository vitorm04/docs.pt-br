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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: eebef02babdca5305deaa4ae11e4bca3bf8bf504
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59154395"
---
# <a name="imetadatatablesgettableindex-method"></a><span data-ttu-id="b9287-102">Método IMetaDataTables::GetTableIndex</span><span class="sxs-lookup"><span data-stu-id="b9287-102">IMetaDataTables::GetTableIndex Method</span></span>
<span data-ttu-id="b9287-103">Obtém o índice para a tabela referenciada pelo token especificado.</span><span class="sxs-lookup"><span data-stu-id="b9287-103">Gets the index for the table referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b9287-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b9287-104">Syntax</span></span>  
  
```  
HRESULT GetTableIndex (  
    [in]  ULONG   token,  
    [out] ULONG   *pixTbl  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b9287-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b9287-105">Parameters</span></span>  
 `token`  
 <span data-ttu-id="b9287-106">[in] O token que faz referência à tabela.</span><span class="sxs-lookup"><span data-stu-id="b9287-106">[in] The token that references the table.</span></span>  
  
 `pixTbl`  
 <span data-ttu-id="b9287-107">[out] Um ponteiro para o índice retornado para a tabela referenciada.</span><span class="sxs-lookup"><span data-stu-id="b9287-107">[out] A pointer to the returned index for the referenced table.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b9287-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="b9287-108">Remarks</span></span>  
 <span data-ttu-id="b9287-109">Não recomendamos o uso desse método, porque ele não retorna resultados consistentes.</span><span class="sxs-lookup"><span data-stu-id="b9287-109">We do not recommend the use of this method, because it does not return consistent results.</span></span> <span data-ttu-id="b9287-110">Para obter informações sobre a tabela GUID, consulte a documentação de Common Language Infrastructure (CLI), especialmente "partição II: Definição de metadados e semântica".</span><span class="sxs-lookup"><span data-stu-id="b9287-110">For information about the GUID table, see the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics".</span></span> <span data-ttu-id="b9287-111">A documentação está disponível online; confira [ECMA C# and Common Language Infrastructure Standards](https://go.microsoft.com/fwlink/?LinkID=99212), no MSDN, e [Standard ECMA-335 - Common Language Infrastructure (CLI)](https://go.microsoft.com/fwlink/?LinkID=65552), no site internacional da Ecma.</span><span class="sxs-lookup"><span data-stu-id="b9287-111">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](https://go.microsoft.com/fwlink/?LinkID=99212) on MSDN and [Standard ECMA-335 - Common Language Infrastructure (CLI)](https://go.microsoft.com/fwlink/?LinkID=65552) on the Ecma International Web site.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b9287-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b9287-112">Requirements</span></span>  
 <span data-ttu-id="b9287-113">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b9287-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b9287-114">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="b9287-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b9287-115">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="b9287-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="b9287-116">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="b9287-116">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="b9287-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b9287-117">See also</span></span>

- [<span data-ttu-id="b9287-118">Interface IMetaDataTables</span><span class="sxs-lookup"><span data-stu-id="b9287-118">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="b9287-119">Interface IMetaDataTables2</span><span class="sxs-lookup"><span data-stu-id="b9287-119">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
