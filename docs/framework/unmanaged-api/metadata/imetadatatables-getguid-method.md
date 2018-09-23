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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f589225dde1ba2aabc4ca32542339a771c3287d4
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2018
ms.locfileid: "46703233"
---
# <a name="imetadatatablesgetguid-method"></a><span data-ttu-id="03334-102">Método IMetaDataTables::GetGuid</span><span class="sxs-lookup"><span data-stu-id="03334-102">IMetaDataTables::GetGuid Method</span></span>
<span data-ttu-id="03334-103">Obtém um GUID da linha no índice especificado.</span><span class="sxs-lookup"><span data-stu-id="03334-103">Gets a GUID from the row at the specified index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="03334-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="03334-104">Syntax</span></span>  
  
```  
HRESULT GetGuid (   
    [in]  ULONG       ixGuid,  
    [out] const GUID  **ppGUID  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="03334-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="03334-105">Parameters</span></span>  
 `ixGuid`  
 <span data-ttu-id="03334-106">[in] O índice da linha da qual obter o GUID.</span><span class="sxs-lookup"><span data-stu-id="03334-106">[in] The index of the row from which to get the GUID.</span></span>  
  
 `ppGuid`  
 <span data-ttu-id="03334-107">[out] Um ponteiro para um ponteiro para o GUID.</span><span class="sxs-lookup"><span data-stu-id="03334-107">[out] A pointer to a pointer to the GUID.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="03334-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="03334-108">Remarks</span></span>  
 <span data-ttu-id="03334-109">Não recomendamos o uso desse método, porque ele não retorna resultados consistentes.</span><span class="sxs-lookup"><span data-stu-id="03334-109">We do not recommend the use of this method, because it does not return consistent results.</span></span> <span data-ttu-id="03334-110">Para obter informações sobre a tabela GUID, consulte a documentação do Common Language Infrastructure (CLI), especialmente "partição II: Metadata Definition and Semantics".</span><span class="sxs-lookup"><span data-stu-id="03334-110">For information about the GUID table, see the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics".</span></span> <span data-ttu-id="03334-111">A documentação está disponível online; confira [ECMA C# and Common Language Infrastructure Standards](https://go.microsoft.com/fwlink/?LinkID=99212), no MSDN, e [Standard ECMA-335 - Common Language Infrastructure (CLI)](https://go.microsoft.com/fwlink/?LinkID=65552), no site internacional da Ecma.</span><span class="sxs-lookup"><span data-stu-id="03334-111">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](https://go.microsoft.com/fwlink/?LinkID=99212) on MSDN and [Standard ECMA-335 - Common Language Infrastructure (CLI)](https://go.microsoft.com/fwlink/?LinkID=65552) on the Ecma International Web site.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="03334-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="03334-112">Requirements</span></span>  
 <span data-ttu-id="03334-113">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="03334-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="03334-114">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="03334-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="03334-115">**Biblioteca:** usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="03334-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="03334-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="03334-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03334-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="03334-117">See Also</span></span>  
 [<span data-ttu-id="03334-118">Interface IMetaDataTables</span><span class="sxs-lookup"><span data-stu-id="03334-118">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 [<span data-ttu-id="03334-119">Interface IMetaDataTables2</span><span class="sxs-lookup"><span data-stu-id="03334-119">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
