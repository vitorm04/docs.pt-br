---
title: "Método ImportTypes"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IALink.ImportTypes
api_location: alink.dll
api_type: COM
f1_keywords: ImportTypes
helpviewer_keywords: ImportTypes method
ms.assetid: 351d4b4c-c939-486d-9471-51914a55f471
topic_type: apiref
caps.latest.revision: "5"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 39e7cfb3c811a89ae88d6984946f72a9b1f469db
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="importtypes-method"></a><span data-ttu-id="d0167-102">Método ImportTypes</span><span class="sxs-lookup"><span data-stu-id="d0167-102">ImportTypes Method</span></span>
<span data-ttu-id="d0167-103">Inicia a importação de tipos de cada escopo importados por meio de [método ImportFile](../../../../docs/framework/unmanaged-api/alink/importfile-method.md).</span><span class="sxs-lookup"><span data-stu-id="d0167-103">Initiates the importing of types from each scope imported via [ImportFile Method](../../../../docs/framework/unmanaged-api/alink/importfile-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0167-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d0167-104">Syntax</span></span>  
  
```  
HRESULT ImportTypes(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwScope,  
    HALINKENUM* phEnum,  
    IMetaDataImport** ppImportScope,  
    DWORD* pdwCountOfTypes  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d0167-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d0167-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="d0167-106">ID do assembly para importar.</span><span class="sxs-lookup"><span data-stu-id="d0167-106">ID of the assembly to import to.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="d0167-107">ID do arquivo de origem.</span><span class="sxs-lookup"><span data-stu-id="d0167-107">ID of the file to import from.</span></span>  
  
 `dwScope`  
 <span data-ttu-id="d0167-108">Escopo com base em zero para importar.</span><span class="sxs-lookup"><span data-stu-id="d0167-108">Zero-based scope to import.</span></span>  
  
 `phEnum`  
 <span data-ttu-id="d0167-109">Recebe o identificador de enumerador para os tipos neste escopo.</span><span class="sxs-lookup"><span data-stu-id="d0167-109">Receives enumerator handle for the types in this scope.</span></span>  
  
 `ppImportScope`  
 <span data-ttu-id="d0167-110">Opcionalmente, recebe [IMetaDataImport Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="d0167-110">Optionally receives [IMetaDataImport Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) interface.</span></span>  
  
 `pdwCountOfTypes`  
 <span data-ttu-id="d0167-111">Opcionalmente, recebe contagem dos tipos no escopo indicado.</span><span class="sxs-lookup"><span data-stu-id="d0167-111">Optionally receives count of types in the indicated scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d0167-112">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="d0167-112">Return Value</span></span>  
 <span data-ttu-id="d0167-113">Retorna S_OK se o método for bem-sucedido.</span><span class="sxs-lookup"><span data-stu-id="d0167-113">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d0167-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d0167-114">Requirements</span></span>  
 <span data-ttu-id="d0167-115">Requer alink.h</span><span class="sxs-lookup"><span data-stu-id="d0167-115">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0167-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d0167-116">See Also</span></span>  
 [<span data-ttu-id="d0167-117">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="d0167-117">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="d0167-118">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="d0167-118">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="d0167-119">API do ALink</span><span class="sxs-lookup"><span data-stu-id="d0167-119">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
