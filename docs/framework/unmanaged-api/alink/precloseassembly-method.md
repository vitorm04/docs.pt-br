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
ms.openlocfilehash: a820d5d742c722b495a5a4b3952450a0434110fd
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67741556"
---
# <a name="precloseassembly-method"></a><span data-ttu-id="db327-102">Método PreCloseAssembly</span><span class="sxs-lookup"><span data-stu-id="db327-102">PreCloseAssembly Method</span></span>
<span data-ttu-id="db327-103">Fecha o arquivo do assembly.</span><span class="sxs-lookup"><span data-stu-id="db327-103">Closes the assembly file.</span></span> <span data-ttu-id="db327-104">Chame esse método depois de fechar todos os outros arquivos, mas antes de fechar o arquivo do assembly.</span><span class="sxs-lookup"><span data-stu-id="db327-104">Call this method after closing all other files, but before closing the assembly file.</span></span> <span data-ttu-id="db327-105">Não chame este método para módulos não associados.</span><span class="sxs-lookup"><span data-stu-id="db327-105">Do not call this method for unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db327-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="db327-106">Syntax</span></span>  
  
```cpp  
HRESULT PreCloseAssembly(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="db327-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="db327-107">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="db327-108">ID do assembly.</span><span class="sxs-lookup"><span data-stu-id="db327-108">ID of the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="db327-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="db327-109">Return Value</span></span>  
 <span data-ttu-id="db327-110">Se o método for bem-sucedido, retornará S_OK.</span><span class="sxs-lookup"><span data-stu-id="db327-110">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="db327-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="db327-111">Requirements</span></span>  
 <span data-ttu-id="db327-112">Requer alink.h.</span><span class="sxs-lookup"><span data-stu-id="db327-112">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db327-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="db327-113">See also</span></span>

- [<span data-ttu-id="db327-114">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="db327-114">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="db327-115">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="db327-115">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="db327-116">API do ALink</span><span class="sxs-lookup"><span data-stu-id="db327-116">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
