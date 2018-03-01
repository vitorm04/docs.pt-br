---
title: "Método EnumImportTypes"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- EnumImportTypes
- IALink.EnumImportTypes
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- EnumImportTypes
helpviewer_keywords:
- EnumImportTypes method
ms.assetid: 83a0e4e7-ec06-40cb-9b63-700b9695bb04
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 08644816d3fa11ade5a8ebee1573e8f66d526101
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="enumimporttypes-method"></a><span data-ttu-id="32cf3-102">Método EnumImportTypes</span><span class="sxs-lookup"><span data-stu-id="32cf3-102">EnumImportTypes Method</span></span>
<span data-ttu-id="32cf3-103">Enumera cada tipo em cada escopo.</span><span class="sxs-lookup"><span data-stu-id="32cf3-103">Enumerates each type in each scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32cf3-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="32cf3-104">Syntax</span></span>  
  
```  
HRESULT EnumImportTypes(  
    HALINKENUM   hEnum,  
    DWORD        dwMax,  
    mdTypeDef    aTypeDefs[],  
    DWORD*       pdwCount  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="32cf3-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="32cf3-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="32cf3-106">Identificador de enumerador.</span><span class="sxs-lookup"><span data-stu-id="32cf3-106">Handle for enumerator.</span></span>  
  
 `dwMax`  
 <span data-ttu-id="32cf3-107">Número máximo de tipos para recuperar.</span><span class="sxs-lookup"><span data-stu-id="32cf3-107">Maximum number of types to retrieve.</span></span>  
  
 `aTypeDefs`  
 <span data-ttu-id="32cf3-108">Recebe tipo tokens, não deve exceder `dwMax`.</span><span class="sxs-lookup"><span data-stu-id="32cf3-108">Recieves type tokens, not to exceed `dwMax`.</span></span>  
  
 `pdwCount`  
 <span data-ttu-id="32cf3-109">Recebe o número real de tipo em `aTypeDefs`.</span><span class="sxs-lookup"><span data-stu-id="32cf3-109">Receives actual number of type in `aTypeDefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="32cf3-110">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="32cf3-110">Return Value</span></span>  
 <span data-ttu-id="32cf3-111">Retorna S_OK se o método for bem-sucedido.</span><span class="sxs-lookup"><span data-stu-id="32cf3-111">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="32cf3-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="32cf3-112">Requirements</span></span>  
 <span data-ttu-id="32cf3-113">Requer alink.h</span><span class="sxs-lookup"><span data-stu-id="32cf3-113">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32cf3-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="32cf3-114">See Also</span></span>  
 [<span data-ttu-id="32cf3-115">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="32cf3-115">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="32cf3-116">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="32cf3-116">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="32cf3-117">API do ALink</span><span class="sxs-lookup"><span data-stu-id="32cf3-117">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
