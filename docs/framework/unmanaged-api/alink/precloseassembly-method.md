---
title: Método PreCloseAssembly
ms.date: 03/30/2017
api_name:
- IALink.PreCloseAssembly
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- PreCloseAssembly
helpviewer_keywords:
- PreCloseAssembly method
ms.assetid: 6d23ac54-15ea-4027-a172-9ebef43e8f56
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 82421fa83a6f0d24492d70f961e731b679c25728
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33400712"
---
# <a name="precloseassembly-method"></a><span data-ttu-id="b3125-102">Método PreCloseAssembly</span><span class="sxs-lookup"><span data-stu-id="b3125-102">PreCloseAssembly Method</span></span>
<span data-ttu-id="b3125-103">Fecha o arquivo de assembly.</span><span class="sxs-lookup"><span data-stu-id="b3125-103">Closes the assembly file.</span></span> <span data-ttu-id="b3125-104">Chame este método depois de fechar todos os outros arquivos, mas antes de fechar o arquivo de assembly.</span><span class="sxs-lookup"><span data-stu-id="b3125-104">Call this method after closing all other files, but before closing the assembly file.</span></span> <span data-ttu-id="b3125-105">Não chame este método para os módulos não associados.</span><span class="sxs-lookup"><span data-stu-id="b3125-105">Do not call this method for unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b3125-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b3125-106">Syntax</span></span>  
  
```  
HRESULT PreCloseAssembly(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b3125-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b3125-107">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="b3125-108">ID do assembly.</span><span class="sxs-lookup"><span data-stu-id="b3125-108">ID of the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b3125-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="b3125-109">Return Value</span></span>  
 <span data-ttu-id="b3125-110">Retorna S_OK se o método for bem-sucedido.</span><span class="sxs-lookup"><span data-stu-id="b3125-110">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b3125-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b3125-111">Requirements</span></span>  
 <span data-ttu-id="b3125-112">Requer alink.h.</span><span class="sxs-lookup"><span data-stu-id="b3125-112">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3125-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b3125-113">See Also</span></span>  
 [<span data-ttu-id="b3125-114">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="b3125-114">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="b3125-115">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="b3125-115">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="b3125-116">API do ALink</span><span class="sxs-lookup"><span data-stu-id="b3125-116">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
