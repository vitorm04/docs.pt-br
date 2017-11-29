---
title: "Método GetScope2"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IALink2.GetScope2
api_location: alink.dll
api_type: COM
f1_keywords: GetScope2
helpviewer_keywords: GetScope2 method
ms.assetid: 49435665-6f5a-4acd-9034-8c9244a04a63
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 143d1d7cfd6f99a662fd7a79e2e2fa629f74967a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="getscope2-method"></a><span data-ttu-id="f93fa-102">Método GetScope2</span><span class="sxs-lookup"><span data-stu-id="f93fa-102">GetScope2 Method</span></span>
<span data-ttu-id="f93fa-103">Obtém um escopo de importação.</span><span class="sxs-lookup"><span data-stu-id="f93fa-103">Gets an import scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f93fa-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f93fa-104">Syntax</span></span>  
  
```  
HRESULT GetScope2(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwScope,  
    IMetaDataImport2** ppImportScope  
) PURE;   
```  
  
#### <a name="parameters"></a><span data-ttu-id="f93fa-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f93fa-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="f93fa-106">ID do assembly de destino.</span><span class="sxs-lookup"><span data-stu-id="f93fa-106">ID of target assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="f93fa-107">ID do arquivo do qual importar.</span><span class="sxs-lookup"><span data-stu-id="f93fa-107">ID of file from which to import.</span></span>  
  
 `dwScope`  
 <span data-ttu-id="f93fa-108">Escopo com base em zero para importar.</span><span class="sxs-lookup"><span data-stu-id="f93fa-108">Zero-based scope to import.</span></span>  
  
 `ppImportScope`  
 <span data-ttu-id="f93fa-109">Recebe o ponteiro para [Interface IMetaDataImport2](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md) interface para escopo indicado.</span><span class="sxs-lookup"><span data-stu-id="f93fa-109">Receives pointer to [IMetaDataImport2 Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md) interface for indicated scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f93fa-110">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="f93fa-110">Return Value</span></span>  
 <span data-ttu-id="f93fa-111">Retorna S_OK se o método for bem-sucedido.</span><span class="sxs-lookup"><span data-stu-id="f93fa-111">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f93fa-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f93fa-112">Requirements</span></span>  
 <span data-ttu-id="f93fa-113">Requer alink.h.</span><span class="sxs-lookup"><span data-stu-id="f93fa-113">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f93fa-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f93fa-114">See Also</span></span>  
 [<span data-ttu-id="f93fa-115">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="f93fa-115">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="f93fa-116">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="f93fa-116">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="f93fa-117">API do ALink</span><span class="sxs-lookup"><span data-stu-id="f93fa-117">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
