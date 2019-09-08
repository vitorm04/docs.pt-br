---
title: Método FreeWin32ResBlob
ms.date: 03/30/2017
api_name:
- IALink.FreeWin32ResBlob
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- FreeWin32ResBlob
helpviewer_keywords:
- FreeWin32ResBlob method
ms.assetid: d941102b-2679-4c49-b15e-c0fc9c53e11f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ea0fbceb1e778a2f26e0625a337b803f417b59eb
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70777252"
---
# <a name="freewin32resblob-method"></a><span data-ttu-id="28188-102">Método FreeWin32ResBlob</span><span class="sxs-lookup"><span data-stu-id="28188-102">FreeWin32ResBlob Method</span></span>
<span data-ttu-id="28188-103">Libera o blob de recursos do Win32 e os recursos associados.</span><span class="sxs-lookup"><span data-stu-id="28188-103">Releases the Win32 resource blob and associated resources.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="28188-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="28188-104">Syntax</span></span>  
  
```cpp  
HRESULT FreeWin32ResBlob(  
    const void** ppResBlob  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="28188-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="28188-105">Parameters</span></span>  
 `ppResBlob`  
 <span data-ttu-id="28188-106">O blob de recursos a ser liberado.</span><span class="sxs-lookup"><span data-stu-id="28188-106">The resource blob to be released.</span></span> <span data-ttu-id="28188-107">Esse método atribui o ponteiro de blob a NULL.</span><span class="sxs-lookup"><span data-stu-id="28188-107">This method assigns the blob pointer to NULL.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="28188-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="28188-108">Return Value</span></span>  
 <span data-ttu-id="28188-109">Retornará S_OK se o método tiver sucesso.</span><span class="sxs-lookup"><span data-stu-id="28188-109">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="28188-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="28188-110">Requirements</span></span>  
 <span data-ttu-id="28188-111">Requer ALink. h</span><span class="sxs-lookup"><span data-stu-id="28188-111">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28188-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="28188-112">See also</span></span>

- [<span data-ttu-id="28188-113">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="28188-113">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="28188-114">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="28188-114">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="28188-115">API do ALink</span><span class="sxs-lookup"><span data-stu-id="28188-115">ALink API</span></span>](index.md)
