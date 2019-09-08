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
ms.openlocfilehash: 88f594117fffedb6acafef26a9e834dd951ea5bb
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70787531"
---
# <a name="endmerge-method"></a><span data-ttu-id="9eaa0-102">Método EndMerge</span><span class="sxs-lookup"><span data-stu-id="9eaa0-102">EndMerge Method</span></span>
<span data-ttu-id="9eaa0-103">Indica que todos os atributos personalizados foram mesclados no escopo de emissão.</span><span class="sxs-lookup"><span data-stu-id="9eaa0-103">Indicates that all custom attributes have been merged into the emit scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9eaa0-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9eaa0-104">Syntax</span></span>  
  
```cpp  
HRESULT EndMerge(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="9eaa0-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="9eaa0-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="9eaa0-106">ID do assembly.</span><span class="sxs-lookup"><span data-stu-id="9eaa0-106">ID of the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9eaa0-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="9eaa0-107">Return Value</span></span>  
 <span data-ttu-id="9eaa0-108">Retornará S_OK se o método tiver sucesso.</span><span class="sxs-lookup"><span data-stu-id="9eaa0-108">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9eaa0-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9eaa0-109">Requirements</span></span>  
 <span data-ttu-id="9eaa0-110">Requer ALink. h</span><span class="sxs-lookup"><span data-stu-id="9eaa0-110">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9eaa0-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9eaa0-111">See also</span></span>

- [<span data-ttu-id="9eaa0-112">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="9eaa0-112">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="9eaa0-113">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="9eaa0-113">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="9eaa0-114">API do ALink</span><span class="sxs-lookup"><span data-stu-id="9eaa0-114">ALink API</span></span>](index.md)
