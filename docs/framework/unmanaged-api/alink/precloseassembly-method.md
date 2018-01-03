---
title: "Método PreCloseAssembly"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IALink.PreCloseAssembly
api_location: alink.dll
api_type: COM
f1_keywords: PreCloseAssembly
helpviewer_keywords: PreCloseAssembly method
ms.assetid: 6d23ac54-15ea-4027-a172-9ebef43e8f56
topic_type: apiref
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5a4d1f2eed036552ab17b6768b7b2d84f4a52c9c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="precloseassembly-method"></a><span data-ttu-id="d6698-102">Método PreCloseAssembly</span><span class="sxs-lookup"><span data-stu-id="d6698-102">PreCloseAssembly Method</span></span>
<span data-ttu-id="d6698-103">Fecha o arquivo de assembly.</span><span class="sxs-lookup"><span data-stu-id="d6698-103">Closes the assembly file.</span></span> <span data-ttu-id="d6698-104">Chame este método depois de fechar todos os outros arquivos, mas antes de fechar o arquivo de assembly.</span><span class="sxs-lookup"><span data-stu-id="d6698-104">Call this method after closing all other files, but before closing the assembly file.</span></span> <span data-ttu-id="d6698-105">Não chame este método para os módulos não associados.</span><span class="sxs-lookup"><span data-stu-id="d6698-105">Do not call this method for unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6698-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d6698-106">Syntax</span></span>  
  
```  
HRESULT PreCloseAssembly(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d6698-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d6698-107">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="d6698-108">ID do assembly.</span><span class="sxs-lookup"><span data-stu-id="d6698-108">ID of the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d6698-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="d6698-109">Return Value</span></span>  
 <span data-ttu-id="d6698-110">Retorna S_OK se o método for bem-sucedido.</span><span class="sxs-lookup"><span data-stu-id="d6698-110">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d6698-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d6698-111">Requirements</span></span>  
 <span data-ttu-id="d6698-112">Requer alink.h.</span><span class="sxs-lookup"><span data-stu-id="d6698-112">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6698-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d6698-113">See Also</span></span>  
 [<span data-ttu-id="d6698-114">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="d6698-114">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="d6698-115">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="d6698-115">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="d6698-116">API do ALink</span><span class="sxs-lookup"><span data-stu-id="d6698-116">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
