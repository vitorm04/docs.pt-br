---
title: Método GetResolutionScope
ms.date: 03/30/2017
api_name:
- IALink.GetResolutionScope
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GetResolutionScope
helpviewer_keywords:
- GetResolutionScope method
ms.assetid: 5b48ca60-dacd-44b2-9979-4a5122f00812
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a2bfb43002b79fd3e499272b87756bdc3ab0b589
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70787330"
---
# <a name="getresolutionscope-method"></a><span data-ttu-id="b90b6-102">Método GetResolutionScope</span><span class="sxs-lookup"><span data-stu-id="b90b6-102">GetResolutionScope Method</span></span>
<span data-ttu-id="b90b6-103">Recupera o escopo de um determinado tipo.</span><span class="sxs-lookup"><span data-stu-id="b90b6-103">Retrieves the scope of a given type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b90b6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b90b6-104">Syntax</span></span>  
  
```cpp  
HRESULT GetResolutionScope(  
    mdAssembly  AssemblyID,  
    mdToken     FileToken,  
    mdToken     TargetFile,  
    mdToken*    pScope  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="b90b6-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b90b6-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="b90b6-106">ID do assembly.</span><span class="sxs-lookup"><span data-stu-id="b90b6-106">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="b90b6-107">Arquivo que é necessário de uma referência.</span><span class="sxs-lookup"><span data-stu-id="b90b6-107">File that is in need of a reference.</span></span>  
  
 `TargetFile`  
 <span data-ttu-id="b90b6-108">O token do arquivo no qual o tipo é definido, geralmente recuperado com o [Método ImportFile](importfile-method.md).</span><span class="sxs-lookup"><span data-stu-id="b90b6-108">Token of file that type is defined in, usually retrieved with [ImportFile Method](importfile-method.md).</span></span>  
  
 `pScope`  
 <span data-ttu-id="b90b6-109">Recebe a referência de módulo ou assembly.</span><span class="sxs-lookup"><span data-stu-id="b90b6-109">Receives the assembly or module reference.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b90b6-110">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="b90b6-110">Return Value</span></span>  
 <span data-ttu-id="b90b6-111">Retornará S_OK se o método tiver sucesso.</span><span class="sxs-lookup"><span data-stu-id="b90b6-111">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b90b6-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b90b6-112">Requirements</span></span>  
 <span data-ttu-id="b90b6-113">Requer ALink. h.</span><span class="sxs-lookup"><span data-stu-id="b90b6-113">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b90b6-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b90b6-114">See also</span></span>

- [<span data-ttu-id="b90b6-115">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="b90b6-115">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="b90b6-116">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="b90b6-116">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="b90b6-117">API do ALink</span><span class="sxs-lookup"><span data-stu-id="b90b6-117">ALink API</span></span>](index.md)
