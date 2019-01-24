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
ms.openlocfilehash: 4e437868138d7ae31d233853ecc0f709de3ee39d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54512713"
---
# <a name="enumimporttypes-method"></a><span data-ttu-id="c17b1-102">Método EnumImportTypes</span><span class="sxs-lookup"><span data-stu-id="c17b1-102">EnumImportTypes Method</span></span>
<span data-ttu-id="c17b1-103">Enumera cada tipo em cada escopo.</span><span class="sxs-lookup"><span data-stu-id="c17b1-103">Enumerates each type in each scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c17b1-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c17b1-104">Syntax</span></span>  
  
```  
HRESULT EnumImportTypes(  
    HALINKENUM   hEnum,  
    DWORD        dwMax,  
    mdTypeDef    aTypeDefs[],  
    DWORD*       pdwCount  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c17b1-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c17b1-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="c17b1-106">Identificador para o enumerador.</span><span class="sxs-lookup"><span data-stu-id="c17b1-106">Handle for enumerator.</span></span>  
  
 `dwMax`  
 <span data-ttu-id="c17b1-107">Número máximo de tipos para recuperar.</span><span class="sxs-lookup"><span data-stu-id="c17b1-107">Maximum number of types to retrieve.</span></span>  
  
 `aTypeDefs`  
 <span data-ttu-id="c17b1-108">Recebe digite tokens, não deve exceder `dwMax`.</span><span class="sxs-lookup"><span data-stu-id="c17b1-108">Recieves type tokens, not to exceed `dwMax`.</span></span>  
  
 `pdwCount`  
 <span data-ttu-id="c17b1-109">Recebe o número real de tipo no `aTypeDefs`.</span><span class="sxs-lookup"><span data-stu-id="c17b1-109">Receives actual number of type in `aTypeDefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c17b1-110">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="c17b1-110">Return Value</span></span>  
 <span data-ttu-id="c17b1-111">Se o método for bem-sucedido, retornará S_OK.</span><span class="sxs-lookup"><span data-stu-id="c17b1-111">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c17b1-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c17b1-112">Requirements</span></span>  
 <span data-ttu-id="c17b1-113">Requer alink.h</span><span class="sxs-lookup"><span data-stu-id="c17b1-113">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c17b1-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c17b1-114">See also</span></span>
- [<span data-ttu-id="c17b1-115">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="c17b1-115">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="c17b1-116">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="c17b1-116">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="c17b1-117">API do ALink</span><span class="sxs-lookup"><span data-stu-id="c17b1-117">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
