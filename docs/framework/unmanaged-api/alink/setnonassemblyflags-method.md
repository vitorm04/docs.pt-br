---
title: Método SetNonAssemblyFlags
ms.date: 03/30/2017
api_name:
- IALink.SetNonAssemblyFlags
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- SetNonAssemblyFlags
helpviewer_keywords:
- SetNonAssemblyFlags method
ms.assetid: f8ba6fc8-f5aa-4066-ac96-56332758f5ec
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 27ad89f1910bc7bb08a23c9fdb0d50828fb8b5e6
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67741443"
---
# <a name="setnonassemblyflags-method"></a><span data-ttu-id="bc35a-102">Método SetNonAssemblyFlags</span><span class="sxs-lookup"><span data-stu-id="bc35a-102">SetNonAssemblyFlags Method</span></span>
<span data-ttu-id="bc35a-103">Define os sinalizadores que não são específicas do assembly.</span><span class="sxs-lookup"><span data-stu-id="bc35a-103">Sets flags that are not assembly-specific.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc35a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bc35a-104">Syntax</span></span>  
  
```cpp  
HRESULT SetNonAssemblyFlags(  
    AssemblyFlags afFlags  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="bc35a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="bc35a-105">Parameters</span></span>  
 `afFlags`  
 <span data-ttu-id="bc35a-106">Sinalizadores de ALink.</span><span class="sxs-lookup"><span data-stu-id="bc35a-106">ALink flags.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bc35a-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="bc35a-107">Return Value</span></span>  
 <span data-ttu-id="bc35a-108">Se o método for bem-sucedido, retornará S_OK.</span><span class="sxs-lookup"><span data-stu-id="bc35a-108">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bc35a-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="bc35a-109">Requirements</span></span>  
 <span data-ttu-id="bc35a-110">Requer alink.h</span><span class="sxs-lookup"><span data-stu-id="bc35a-110">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc35a-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bc35a-111">See also</span></span>

- [<span data-ttu-id="bc35a-112">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="bc35a-112">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="bc35a-113">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="bc35a-113">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="bc35a-114">API do ALink</span><span class="sxs-lookup"><span data-stu-id="bc35a-114">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
