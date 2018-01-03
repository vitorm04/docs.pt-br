---
title: "Método ImportTypes2"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IALink2.ImportTypes2
api_location: alink.dll
api_type: COM
f1_keywords: ImportTypes2
helpviewer_keywords: ImportTypes2 method
ms.assetid: 32f3ba58-9695-41e9-ba58-fd19e45ed396
topic_type: apiref
caps.latest.revision: "5"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 47c49253a1e2839939ef4e671f155e4a44d07529
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="importtypes2-method"></a><span data-ttu-id="f7491-102">Método ImportTypes2</span><span class="sxs-lookup"><span data-stu-id="f7491-102">ImportTypes2 Method</span></span>
<span data-ttu-id="f7491-103">Inicia a importação de tipos.</span><span class="sxs-lookup"><span data-stu-id="f7491-103">Initiates the import of types.</span></span> <span data-ttu-id="f7491-104">Chame este método para iniciar a importação de tipos de cada escopo importado por meio de [método ImportFile](../../../../docs/framework/unmanaged-api/alink/importfile-method.md).</span><span class="sxs-lookup"><span data-stu-id="f7491-104">Call this method to begin importing types from each scope imported via [ImportFile Method](../../../../docs/framework/unmanaged-api/alink/importfile-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7491-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f7491-105">Syntax</span></span>  
  
```  
HRESULT ImportTypes2(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwScope,  
    HALINKENUM* phEnum,  
    IMetaDataImport2** ppImportScope,  
    DWORD* pdwCountOfTypes  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f7491-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f7491-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="f7491-107">ID do assembly no qual deseja importar.</span><span class="sxs-lookup"><span data-stu-id="f7491-107">ID of assembly into which to import.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="f7491-108">ID do arquivo do qual importar.</span><span class="sxs-lookup"><span data-stu-id="f7491-108">ID of file to from which to import.</span></span>  
  
 `dwScope`  
 <span data-ttu-id="f7491-109">Escopo com base em zero do qual importar.</span><span class="sxs-lookup"><span data-stu-id="f7491-109">Zero-based scope from which to import.</span></span>  
  
 `phEnum`  
 <span data-ttu-id="f7491-110">Recebe o identificador de enumerador para os tipos no escopo fornecido.</span><span class="sxs-lookup"><span data-stu-id="f7491-110">Receives enumerator handle for the types in the given scope.</span></span>  
  
 `ppImportScope`  
 <span data-ttu-id="f7491-111">Opcionalmente, recebe [Interface IMetaDataImport2](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="f7491-111">Optionally receives [IMetaDataImport2 Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md) interface.</span></span>  
  
 `pdwCountOfTypes`  
 <span data-ttu-id="f7491-112">Opcionalmente, recebe a contagem de tipos no escopo especificado.</span><span class="sxs-lookup"><span data-stu-id="f7491-112">Optionally receives count of types in the specified scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f7491-113">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="f7491-113">Return Value</span></span>  
 <span data-ttu-id="f7491-114">Retorna S_OK se o método for bem-sucedido.</span><span class="sxs-lookup"><span data-stu-id="f7491-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f7491-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f7491-115">Requirements</span></span>  
 <span data-ttu-id="f7491-116">Requer alink.h</span><span class="sxs-lookup"><span data-stu-id="f7491-116">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7491-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f7491-117">See Also</span></span>  
 [<span data-ttu-id="f7491-118">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="f7491-118">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="f7491-119">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="f7491-119">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="f7491-120">API do ALink</span><span class="sxs-lookup"><span data-stu-id="f7491-120">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
