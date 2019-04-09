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
ms.openlocfilehash: 196a57b3e919ea4ccbc0b91e5b6f281ad3c30b62
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59118151"
---
# <a name="freewin32resblob-method"></a><span data-ttu-id="364b7-102">Método FreeWin32ResBlob</span><span class="sxs-lookup"><span data-stu-id="364b7-102">FreeWin32ResBlob Method</span></span>
<span data-ttu-id="364b7-103">Libera o blob de recurso do Win32 e recursos associados.</span><span class="sxs-lookup"><span data-stu-id="364b7-103">Releases the Win32 resource blob and associated resources.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="364b7-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="364b7-104">Syntax</span></span>  
  
```  
HRESULT FreeWin32ResBlob(  
    const void** ppResBlob  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="364b7-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="364b7-105">Parameters</span></span>  
 `ppResBlob`  
 <span data-ttu-id="364b7-106">O blob de recursos sejam liberados.</span><span class="sxs-lookup"><span data-stu-id="364b7-106">The resource blob to be released.</span></span> <span data-ttu-id="364b7-107">Esse método atribui o ponteiro de blob para NULL.</span><span class="sxs-lookup"><span data-stu-id="364b7-107">This method assigns the blob pointer to NULL.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="364b7-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="364b7-108">Return Value</span></span>  
 <span data-ttu-id="364b7-109">Se o método for bem-sucedido, retornará S_OK.</span><span class="sxs-lookup"><span data-stu-id="364b7-109">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="364b7-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="364b7-110">Requirements</span></span>  
 <span data-ttu-id="364b7-111">Requer alink.h</span><span class="sxs-lookup"><span data-stu-id="364b7-111">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="364b7-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="364b7-112">See also</span></span>

- [<span data-ttu-id="364b7-113">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="364b7-113">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="364b7-114">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="364b7-114">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="364b7-115">API do ALink</span><span class="sxs-lookup"><span data-stu-id="364b7-115">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
