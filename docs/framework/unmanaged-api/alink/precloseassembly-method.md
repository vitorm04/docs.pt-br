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
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59184503"
---
# <a name="precloseassembly-method"></a><span data-ttu-id="666ca-102">Método PreCloseAssembly</span><span class="sxs-lookup"><span data-stu-id="666ca-102">PreCloseAssembly Method</span></span>
<span data-ttu-id="666ca-103">Fecha o arquivo do assembly.</span><span class="sxs-lookup"><span data-stu-id="666ca-103">Closes the assembly file.</span></span> <span data-ttu-id="666ca-104">Chame esse método depois de fechar todos os outros arquivos, mas antes de fechar o arquivo do assembly.</span><span class="sxs-lookup"><span data-stu-id="666ca-104">Call this method after closing all other files, but before closing the assembly file.</span></span> <span data-ttu-id="666ca-105">Não chame este método para módulos não associados.</span><span class="sxs-lookup"><span data-stu-id="666ca-105">Do not call this method for unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="666ca-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="666ca-106">Syntax</span></span>  
  
```  
HRESULT PreCloseAssembly(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="666ca-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="666ca-107">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="666ca-108">ID do assembly.</span><span class="sxs-lookup"><span data-stu-id="666ca-108">ID of the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="666ca-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="666ca-109">Return Value</span></span>  
 <span data-ttu-id="666ca-110">Se o método for bem-sucedido, retornará S_OK.</span><span class="sxs-lookup"><span data-stu-id="666ca-110">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="666ca-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="666ca-111">Requirements</span></span>  
 <span data-ttu-id="666ca-112">Requer alink.h.</span><span class="sxs-lookup"><span data-stu-id="666ca-112">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="666ca-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="666ca-113">See also</span></span>

- [<span data-ttu-id="666ca-114">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="666ca-114">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="666ca-115">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="666ca-115">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="666ca-116">API do ALink</span><span class="sxs-lookup"><span data-stu-id="666ca-116">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
