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
ms.openlocfilehash: 020cc56126249b27a52387e6efa3aa10c83d9126
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59226840"
---
# <a name="endmerge-method"></a><span data-ttu-id="8f1a1-102">Método EndMerge</span><span class="sxs-lookup"><span data-stu-id="8f1a1-102">EndMerge Method</span></span>
<span data-ttu-id="8f1a1-103">Indica que todos os atributos personalizados foram mesclados para o escopo de emissão.</span><span class="sxs-lookup"><span data-stu-id="8f1a1-103">Indicates that all custom attributes have been merged into the emit scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8f1a1-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8f1a1-104">Syntax</span></span>  
  
```  
HRESULT EndMerge(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="8f1a1-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8f1a1-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="8f1a1-106">ID do assembly.</span><span class="sxs-lookup"><span data-stu-id="8f1a1-106">ID of the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8f1a1-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="8f1a1-107">Return Value</span></span>  
 <span data-ttu-id="8f1a1-108">Se o método for bem-sucedido, retornará S_OK.</span><span class="sxs-lookup"><span data-stu-id="8f1a1-108">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8f1a1-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8f1a1-109">Requirements</span></span>  
 <span data-ttu-id="8f1a1-110">Requer alink.h</span><span class="sxs-lookup"><span data-stu-id="8f1a1-110">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f1a1-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8f1a1-111">See also</span></span>

- [<span data-ttu-id="8f1a1-112">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="8f1a1-112">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="8f1a1-113">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="8f1a1-113">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="8f1a1-114">API do ALink</span><span class="sxs-lookup"><span data-stu-id="8f1a1-114">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
