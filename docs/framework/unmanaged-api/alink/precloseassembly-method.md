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
ms.openlocfilehash: fcfd3e79bbb52837a333b5ffacf5c13ae60f2490
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445619"
---
# <a name="precloseassembly-method"></a><span data-ttu-id="ccdf3-102">Método PreCloseAssembly</span><span class="sxs-lookup"><span data-stu-id="ccdf3-102">PreCloseAssembly Method</span></span>
<span data-ttu-id="ccdf3-103">Fecha o arquivo do assembly.</span><span class="sxs-lookup"><span data-stu-id="ccdf3-103">Closes the assembly file.</span></span> <span data-ttu-id="ccdf3-104">Chame esse método depois de fechar todos os outros arquivos, mas antes de fechar o arquivo do assembly.</span><span class="sxs-lookup"><span data-stu-id="ccdf3-104">Call this method after closing all other files, but before closing the assembly file.</span></span> <span data-ttu-id="ccdf3-105">Não chame esse método para módulos não associados.</span><span class="sxs-lookup"><span data-stu-id="ccdf3-105">Do not call this method for unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ccdf3-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ccdf3-106">Syntax</span></span>  
  
```cpp  
HRESULT PreCloseAssembly(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="ccdf3-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ccdf3-107">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="ccdf3-108">ID do assembly.</span><span class="sxs-lookup"><span data-stu-id="ccdf3-108">ID of the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ccdf3-109">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="ccdf3-109">Return Value</span></span>  
 <span data-ttu-id="ccdf3-110">Retorna S_OK se o método tiver sucesso.</span><span class="sxs-lookup"><span data-stu-id="ccdf3-110">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ccdf3-111">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="ccdf3-111">Requirements</span></span>  
 <span data-ttu-id="ccdf3-112">Requer ALink. h.</span><span class="sxs-lookup"><span data-stu-id="ccdf3-112">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ccdf3-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ccdf3-113">See also</span></span>

- [<span data-ttu-id="ccdf3-114">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="ccdf3-114">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="ccdf3-115">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="ccdf3-115">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="ccdf3-116">API do ALink</span><span class="sxs-lookup"><span data-stu-id="ccdf3-116">ALink API</span></span>](index.md)
