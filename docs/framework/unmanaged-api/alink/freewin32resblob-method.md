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
ms.openlocfilehash: 75aec187452e2f9f442a5d4856fe6777c03f34c1
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67741984"
---
# <a name="freewin32resblob-method"></a><span data-ttu-id="e71b6-102">Método FreeWin32ResBlob</span><span class="sxs-lookup"><span data-stu-id="e71b6-102">FreeWin32ResBlob Method</span></span>
<span data-ttu-id="e71b6-103">Libera o blob de recurso do Win32 e recursos associados.</span><span class="sxs-lookup"><span data-stu-id="e71b6-103">Releases the Win32 resource blob and associated resources.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e71b6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e71b6-104">Syntax</span></span>  
  
```cpp  
HRESULT FreeWin32ResBlob(  
    const void** ppResBlob  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="e71b6-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e71b6-105">Parameters</span></span>  
 `ppResBlob`  
 <span data-ttu-id="e71b6-106">O blob de recursos sejam liberados.</span><span class="sxs-lookup"><span data-stu-id="e71b6-106">The resource blob to be released.</span></span> <span data-ttu-id="e71b6-107">Esse método atribui o ponteiro de blob para NULL.</span><span class="sxs-lookup"><span data-stu-id="e71b6-107">This method assigns the blob pointer to NULL.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e71b6-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="e71b6-108">Return Value</span></span>  
 <span data-ttu-id="e71b6-109">Se o método for bem-sucedido, retornará S_OK.</span><span class="sxs-lookup"><span data-stu-id="e71b6-109">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e71b6-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e71b6-110">Requirements</span></span>  
 <span data-ttu-id="e71b6-111">Requer alink.h</span><span class="sxs-lookup"><span data-stu-id="e71b6-111">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e71b6-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e71b6-112">See also</span></span>

- [<span data-ttu-id="e71b6-113">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="e71b6-113">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="e71b6-114">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="e71b6-114">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="e71b6-115">API do ALink</span><span class="sxs-lookup"><span data-stu-id="e71b6-115">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
