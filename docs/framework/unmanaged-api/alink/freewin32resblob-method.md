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
ms.openlocfilehash: e52984e12f22486212f0a2ec02d452a77242400e
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57491822"
---
# <a name="freewin32resblob-method"></a><span data-ttu-id="13083-102">Método FreeWin32ResBlob</span><span class="sxs-lookup"><span data-stu-id="13083-102">FreeWin32ResBlob Method</span></span>
<span data-ttu-id="13083-103">Libera o blob de recurso do Win32 e recursos associados.</span><span class="sxs-lookup"><span data-stu-id="13083-103">Releases the Win32 resource blob and associated resources.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13083-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="13083-104">Syntax</span></span>  
  
```  
HRESULT FreeWin32ResBlob(  
    const void** ppResBlob  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="13083-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="13083-105">Parameters</span></span>  
 `ppResBlob`  
 <span data-ttu-id="13083-106">O blob de recursos sejam liberados.</span><span class="sxs-lookup"><span data-stu-id="13083-106">The resource blob to be released.</span></span> <span data-ttu-id="13083-107">Esse método atribui o ponteiro de blob para NULL.</span><span class="sxs-lookup"><span data-stu-id="13083-107">This method assigns the blob pointer to NULL.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="13083-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="13083-108">Return Value</span></span>  
 <span data-ttu-id="13083-109">Se o método for bem-sucedido, retornará S_OK.</span><span class="sxs-lookup"><span data-stu-id="13083-109">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="13083-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="13083-110">Requirements</span></span>  
 <span data-ttu-id="13083-111">Requer alink.h</span><span class="sxs-lookup"><span data-stu-id="13083-111">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13083-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="13083-112">See also</span></span>
- [<span data-ttu-id="13083-113">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="13083-113">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="13083-114">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="13083-114">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="13083-115">API do ALink</span><span class="sxs-lookup"><span data-stu-id="13083-115">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
