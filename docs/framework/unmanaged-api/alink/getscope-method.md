---
title: GetScope Method1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IALink.GetScope
api_location: alink.dll
api_type: COM
f1_keywords: GetScope
helpviewer_keywords: GetScope method
ms.assetid: e1555328-2c71-4ece-b357-9eb6d3a8efc4
topic_type: apiref
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4cb51efc3f431dac4a10cc7582e2b43500ccba15
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="getscope-method1"></a><span data-ttu-id="9b205-102">GetScope Method1</span><span class="sxs-lookup"><span data-stu-id="9b205-102">GetScope Method1</span></span>
<span data-ttu-id="9b205-103">Obtém um escopo de importação.</span><span class="sxs-lookup"><span data-stu-id="9b205-103">Gets an import scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b205-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9b205-104">Syntax</span></span>  
  
```  
HRESULT GetScope(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwScope,  
    IMetaDataImport** ppImportScope  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9b205-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="9b205-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="9b205-106">ID exclusiva do assembly para importar.</span><span class="sxs-lookup"><span data-stu-id="9b205-106">Unique ID of assembly to import to.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="9b205-107">ID exclusiva do arquivo de origem.</span><span class="sxs-lookup"><span data-stu-id="9b205-107">Unique ID of the file to import from.</span></span>  
  
 `dwScope`  
 <span data-ttu-id="9b205-108">Escopo com base em zero para importar.</span><span class="sxs-lookup"><span data-stu-id="9b205-108">Zero-based scope to import.</span></span>  
  
 `ppImportScope`  
 <span data-ttu-id="9b205-109">Recebe [IMetaDataImport Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) interface para o escopo.</span><span class="sxs-lookup"><span data-stu-id="9b205-109">Receives [IMetaDataImport Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) interface for the scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9b205-110">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="9b205-110">Return Value</span></span>  
 <span data-ttu-id="9b205-111">Retorna S_OK se o método for bem-sucedido.</span><span class="sxs-lookup"><span data-stu-id="9b205-111">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9b205-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9b205-112">Requirements</span></span>  
 <span data-ttu-id="9b205-113">Requer alink.h</span><span class="sxs-lookup"><span data-stu-id="9b205-113">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b205-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9b205-114">See Also</span></span>  
 [<span data-ttu-id="9b205-115">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="9b205-115">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="9b205-116">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="9b205-116">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="9b205-117">API do ALink</span><span class="sxs-lookup"><span data-stu-id="9b205-117">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
