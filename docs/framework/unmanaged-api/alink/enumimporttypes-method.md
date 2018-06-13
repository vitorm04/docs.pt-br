---
title: Método EnumImportTypes
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 90319886dfe149a3d2d76451c1a8526299cf5b89
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33401642"
---
# <a name="enumimporttypes-method"></a><span data-ttu-id="ff642-102">Método EnumImportTypes</span><span class="sxs-lookup"><span data-stu-id="ff642-102">EnumImportTypes Method</span></span>
<span data-ttu-id="ff642-103">Enumera cada tipo em cada escopo.</span><span class="sxs-lookup"><span data-stu-id="ff642-103">Enumerates each type in each scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff642-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ff642-104">Syntax</span></span>  
  
```  
HRESULT EnumImportTypes(  
    HALINKENUM   hEnum,  
    DWORD        dwMax,  
    mdTypeDef    aTypeDefs[],  
    DWORD*       pdwCount  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ff642-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ff642-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="ff642-106">Identificador de enumerador.</span><span class="sxs-lookup"><span data-stu-id="ff642-106">Handle for enumerator.</span></span>  
  
 `dwMax`  
 <span data-ttu-id="ff642-107">Número máximo de tipos para recuperar.</span><span class="sxs-lookup"><span data-stu-id="ff642-107">Maximum number of types to retrieve.</span></span>  
  
 `aTypeDefs`  
 <span data-ttu-id="ff642-108">Recebe tipo tokens, não deve exceder `dwMax`.</span><span class="sxs-lookup"><span data-stu-id="ff642-108">Recieves type tokens, not to exceed `dwMax`.</span></span>  
  
 `pdwCount`  
 <span data-ttu-id="ff642-109">Recebe o número real de tipo em `aTypeDefs`.</span><span class="sxs-lookup"><span data-stu-id="ff642-109">Receives actual number of type in `aTypeDefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ff642-110">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="ff642-110">Return Value</span></span>  
 <span data-ttu-id="ff642-111">Retorna S_OK se o método for bem-sucedido.</span><span class="sxs-lookup"><span data-stu-id="ff642-111">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ff642-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ff642-112">Requirements</span></span>  
 <span data-ttu-id="ff642-113">Requer alink.h</span><span class="sxs-lookup"><span data-stu-id="ff642-113">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff642-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ff642-114">See Also</span></span>  
 [<span data-ttu-id="ff642-115">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="ff642-115">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="ff642-116">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="ff642-116">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="ff642-117">API do ALink</span><span class="sxs-lookup"><span data-stu-id="ff642-117">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
