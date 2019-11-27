---
title: Método EmitInternalExportedTypes
ms.date: 03/30/2017
api_name:
- EmitInternalExportedTypes
- IALink2.EmitInternalExportedTypes
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- EmitInternalExportedTypes
helpviewer_keywords:
- EmitInternalExportedTypes method
ms.assetid: 28c8b00d-2c14-40b4-aed5-a1db0e2428eb
topic_type:
- apiref
ms.openlocfilehash: d4b7064b0339825c29e4001bc35c4a604098468a
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446503"
---
# <a name="emitinternalexportedtypes-method"></a><span data-ttu-id="d2d7e-102">Método EmitInternalExportedTypes</span><span class="sxs-lookup"><span data-stu-id="d2d7e-102">EmitInternalExportedTypes Method</span></span>
<span data-ttu-id="d2d7e-103">Emite tipos adicionados ao assembly.</span><span class="sxs-lookup"><span data-stu-id="d2d7e-103">Emits types added to the assembly.</span></span> <span data-ttu-id="d2d7e-104">Chame esse método após a adição de tipos internos conhecidos.</span><span class="sxs-lookup"><span data-stu-id="d2d7e-104">Call this method after known internal types have been added.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d2d7e-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d2d7e-105">Syntax</span></span>  
  
```cpp  
HRESULT EmitInternalExportedTypes(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="d2d7e-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d2d7e-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="d2d7e-107">ID do assembly.</span><span class="sxs-lookup"><span data-stu-id="d2d7e-107">ID of assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d2d7e-108">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="d2d7e-108">Return Value</span></span>  
 <span data-ttu-id="d2d7e-109">Retorna S_OK se o método tiver sucesso.</span><span class="sxs-lookup"><span data-stu-id="d2d7e-109">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d2d7e-110">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d2d7e-110">Requirements</span></span>  
 <span data-ttu-id="d2d7e-111">Requer ALink. h</span><span class="sxs-lookup"><span data-stu-id="d2d7e-111">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2d7e-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d2d7e-112">See also</span></span>

- [<span data-ttu-id="d2d7e-113">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="d2d7e-113">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="d2d7e-114">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="d2d7e-114">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="d2d7e-115">API do ALink</span><span class="sxs-lookup"><span data-stu-id="d2d7e-115">ALink API</span></span>](index.md)
