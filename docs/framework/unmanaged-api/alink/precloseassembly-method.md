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
ms.openlocfilehash: aab42e939651d75b1933962d72ba8bec1090f52d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59184503"
---
# <a name="precloseassembly-method"></a><span data-ttu-id="414bf-102">Método PreCloseAssembly</span><span class="sxs-lookup"><span data-stu-id="414bf-102">PreCloseAssembly Method</span></span>
<span data-ttu-id="414bf-103">Fecha o arquivo do assembly.</span><span class="sxs-lookup"><span data-stu-id="414bf-103">Closes the assembly file.</span></span> <span data-ttu-id="414bf-104">Chame esse método depois de fechar todos os outros arquivos, mas antes de fechar o arquivo do assembly.</span><span class="sxs-lookup"><span data-stu-id="414bf-104">Call this method after closing all other files, but before closing the assembly file.</span></span> <span data-ttu-id="414bf-105">Não chame este método para módulos não associados.</span><span class="sxs-lookup"><span data-stu-id="414bf-105">Do not call this method for unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="414bf-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="414bf-106">Syntax</span></span>  
  
```  
HRESULT PreCloseAssembly(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="414bf-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="414bf-107">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="414bf-108">ID do assembly.</span><span class="sxs-lookup"><span data-stu-id="414bf-108">ID of the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="414bf-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="414bf-109">Return Value</span></span>  
 <span data-ttu-id="414bf-110">Se o método for bem-sucedido, retornará S_OK.</span><span class="sxs-lookup"><span data-stu-id="414bf-110">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="414bf-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="414bf-111">Requirements</span></span>  
 <span data-ttu-id="414bf-112">Requer alink.h.</span><span class="sxs-lookup"><span data-stu-id="414bf-112">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="414bf-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="414bf-113">See also</span></span>

- [<span data-ttu-id="414bf-114">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="414bf-114">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="414bf-115">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="414bf-115">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="414bf-116">API do ALink</span><span class="sxs-lookup"><span data-stu-id="414bf-116">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
