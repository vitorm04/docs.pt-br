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
ms.openlocfilehash: 8daf76e50b4c584115a55936aa9336c95a3669ec
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67742072"
---
# <a name="endmerge-method"></a><span data-ttu-id="912e7-102">Método EndMerge</span><span class="sxs-lookup"><span data-stu-id="912e7-102">EndMerge Method</span></span>
<span data-ttu-id="912e7-103">Indica que todos os atributos personalizados foram mesclados para o escopo de emissão.</span><span class="sxs-lookup"><span data-stu-id="912e7-103">Indicates that all custom attributes have been merged into the emit scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="912e7-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="912e7-104">Syntax</span></span>  
  
```cpp  
HRESULT EndMerge(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="912e7-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="912e7-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="912e7-106">ID do assembly.</span><span class="sxs-lookup"><span data-stu-id="912e7-106">ID of the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="912e7-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="912e7-107">Return Value</span></span>  
 <span data-ttu-id="912e7-108">Se o método for bem-sucedido, retornará S_OK.</span><span class="sxs-lookup"><span data-stu-id="912e7-108">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="912e7-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="912e7-109">Requirements</span></span>  
 <span data-ttu-id="912e7-110">Requer alink.h</span><span class="sxs-lookup"><span data-stu-id="912e7-110">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="912e7-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="912e7-111">See also</span></span>

- [<span data-ttu-id="912e7-112">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="912e7-112">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="912e7-113">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="912e7-113">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="912e7-114">API do ALink</span><span class="sxs-lookup"><span data-stu-id="912e7-114">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
