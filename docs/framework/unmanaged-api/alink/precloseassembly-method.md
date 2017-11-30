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
ms.openlocfilehash: 8d940cbdeddc7030c679fae8c8694bb3542123b4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="precloseassembly-method"></a><span data-ttu-id="f8306-102">Método PreCloseAssembly</span><span class="sxs-lookup"><span data-stu-id="f8306-102">PreCloseAssembly Method</span></span>
<span data-ttu-id="f8306-103">Fecha o arquivo de assembly.</span><span class="sxs-lookup"><span data-stu-id="f8306-103">Closes the assembly file.</span></span> <span data-ttu-id="f8306-104">Chame este método depois de fechar todos os outros arquivos, mas antes de fechar o arquivo de assembly.</span><span class="sxs-lookup"><span data-stu-id="f8306-104">Call this method after closing all other files, but before closing the assembly file.</span></span> <span data-ttu-id="f8306-105">Não chame este método para os módulos não associados.</span><span class="sxs-lookup"><span data-stu-id="f8306-105">Do not call this method for unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f8306-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f8306-106">Syntax</span></span>  
  
```  
HRESULT PreCloseAssembly(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f8306-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f8306-107">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="f8306-108">ID do assembly.</span><span class="sxs-lookup"><span data-stu-id="f8306-108">ID of the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f8306-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="f8306-109">Return Value</span></span>  
 <span data-ttu-id="f8306-110">Retorna S_OK se o método for bem-sucedido.</span><span class="sxs-lookup"><span data-stu-id="f8306-110">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f8306-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f8306-111">Requirements</span></span>  
 <span data-ttu-id="f8306-112">Requer alink.h.</span><span class="sxs-lookup"><span data-stu-id="f8306-112">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8306-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f8306-113">See Also</span></span>  
 [<span data-ttu-id="f8306-114">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="f8306-114">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="f8306-115">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="f8306-115">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="f8306-116">API do ALink</span><span class="sxs-lookup"><span data-stu-id="f8306-116">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
