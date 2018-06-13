---
title: Método EndMerge
ms.date: 03/30/2017
api_name:
- IALink.EndMerge
- EndMerge
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- EndMerge
helpviewer_keywords:
- EndMerge method
ms.assetid: 1d03bb15-a2c8-4a04-8fc6-b126c89c3778
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e8f9eecd6d6d74717eb7c1e389bfa24e40afc950
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33402568"
---
# <a name="endmerge-method"></a><span data-ttu-id="22c54-102">Método EndMerge</span><span class="sxs-lookup"><span data-stu-id="22c54-102">EndMerge Method</span></span>
<span data-ttu-id="22c54-103">Indica que todos os atributos personalizados foram mesclados para o escopo de emitir.</span><span class="sxs-lookup"><span data-stu-id="22c54-103">Indicates that all custom attributes have been merged into the emit scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="22c54-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="22c54-104">Syntax</span></span>  
  
```  
HRESULT EndMerge(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="22c54-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="22c54-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="22c54-106">ID do assembly.</span><span class="sxs-lookup"><span data-stu-id="22c54-106">ID of the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="22c54-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="22c54-107">Return Value</span></span>  
 <span data-ttu-id="22c54-108">Retorna S_OK se o método for bem-sucedido.</span><span class="sxs-lookup"><span data-stu-id="22c54-108">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="22c54-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="22c54-109">Requirements</span></span>  
 <span data-ttu-id="22c54-110">Requer alink.h</span><span class="sxs-lookup"><span data-stu-id="22c54-110">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22c54-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="22c54-111">See Also</span></span>  
 [<span data-ttu-id="22c54-112">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="22c54-112">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="22c54-113">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="22c54-113">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="22c54-114">API do ALink</span><span class="sxs-lookup"><span data-stu-id="22c54-114">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
