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
ms.openlocfilehash: d124ce5dd38bed7eb439a055ff9e30a75efe5891
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33400738"
---
# <a name="freewin32resblob-method"></a><span data-ttu-id="0f7d0-102">Método FreeWin32ResBlob</span><span class="sxs-lookup"><span data-stu-id="0f7d0-102">FreeWin32ResBlob Method</span></span>
<span data-ttu-id="0f7d0-103">Libera o blob de recursos do Win32 e os recursos associados.</span><span class="sxs-lookup"><span data-stu-id="0f7d0-103">Releases the Win32 resource blob and associated resources.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0f7d0-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0f7d0-104">Syntax</span></span>  
  
```  
HRESULT FreeWin32ResBlob(  
    const void** ppResBlob  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0f7d0-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0f7d0-105">Parameters</span></span>  
 `ppResBlob`  
 <span data-ttu-id="0f7d0-106">O blob de recursos sejam liberados.</span><span class="sxs-lookup"><span data-stu-id="0f7d0-106">The resource blob to be released.</span></span> <span data-ttu-id="0f7d0-107">Esse método atribui o ponteiro de blob para NULL.</span><span class="sxs-lookup"><span data-stu-id="0f7d0-107">This method assigns the blob pointer to NULL.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0f7d0-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="0f7d0-108">Return Value</span></span>  
 <span data-ttu-id="0f7d0-109">Retorna S_OK se o método for bem-sucedido.</span><span class="sxs-lookup"><span data-stu-id="0f7d0-109">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0f7d0-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0f7d0-110">Requirements</span></span>  
 <span data-ttu-id="0f7d0-111">Requer alink.h</span><span class="sxs-lookup"><span data-stu-id="0f7d0-111">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f7d0-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0f7d0-112">See Also</span></span>  
 [<span data-ttu-id="0f7d0-113">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="0f7d0-113">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="0f7d0-114">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="0f7d0-114">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="0f7d0-115">API do ALink</span><span class="sxs-lookup"><span data-stu-id="0f7d0-115">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
