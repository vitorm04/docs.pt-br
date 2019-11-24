---
title: Método EmitAssemblyCustomAttribute
ms.date: 03/30/2017
api_name:
- IALink.EmitAssemblyCustomAttribute
- EmitAssemblyCustomAttribute
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- EmitAssemblyCustomAttribute
helpviewer_keywords:
- EmitAssemblyCustomAttribute method
ms.assetid: b72f5409-79af-4fa7-90a7-7630eec170f1
topic_type:
- apiref
ms.openlocfilehash: ec0a86e3396ad42152bc0a244f74ad13deba16e4
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446514"
---
# <a name="emitassemblycustomattribute-method"></a><span data-ttu-id="1c841-102">Método EmitAssemblyCustomAttribute</span><span class="sxs-lookup"><span data-stu-id="1c841-102">EmitAssemblyCustomAttribute Method</span></span>
<span data-ttu-id="1c841-103">Call to set assembly-level custom attributes.</span><span class="sxs-lookup"><span data-stu-id="1c841-103">Call to set assembly-level custom attributes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1c841-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1c841-104">Syntax</span></span>  
  
```cpp  
HRESULT EmitAssemblyCustomAttribute(  
    mdAssembly   AssemblyID,  
    mdToken      FileToken,  
    mdToken      tkType,  
    void const*  pCustomValue,  
    DWORD        cbCustomValue,  
    BOOL         bSecurity,  
    BOOL         bAllowMulti  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="1c841-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="1c841-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="1c841-106">ID of the assembly.</span><span class="sxs-lookup"><span data-stu-id="1c841-106">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="1c841-107">File that defiles the attribute.</span><span class="sxs-lookup"><span data-stu-id="1c841-107">File that defiles the attribute.</span></span> <span data-ttu-id="1c841-108">Can be NULL if `AssemblyID` does not indicate an unbound netmodule.</span><span class="sxs-lookup"><span data-stu-id="1c841-108">Can be NULL if `AssemblyID` does not indicate an unbound netmodule.</span></span>  
  
 `tkType`  
 <span data-ttu-id="1c841-109">Type of the custom attribute.</span><span class="sxs-lookup"><span data-stu-id="1c841-109">Type of the custom attribute.</span></span>  
  
 `pCustomValue`  
 <span data-ttu-id="1c841-110">Custom value data.</span><span class="sxs-lookup"><span data-stu-id="1c841-110">Custom value data.</span></span>  
  
 `cbCustomValue`  
 <span data-ttu-id="1c841-111">Length of custom value data.</span><span class="sxs-lookup"><span data-stu-id="1c841-111">Length of custom value data.</span></span>  
  
 `bSecurity`  
 <span data-ttu-id="1c841-112">TRUE if the custom attribute is related to assembly signing.</span><span class="sxs-lookup"><span data-stu-id="1c841-112">TRUE if the custom attribute is related to assembly signing.</span></span>  
  
 `bAllowMulti`  
 <span data-ttu-id="1c841-113">TRUE if multiple attributes are to be emitted.</span><span class="sxs-lookup"><span data-stu-id="1c841-113">TRUE if multiple attributes are to be emitted.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1c841-114">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="1c841-114">Return Value</span></span>  
 <span data-ttu-id="1c841-115">Returns S_OK if the method succeeds.</span><span class="sxs-lookup"><span data-stu-id="1c841-115">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1c841-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1c841-116">Requirements</span></span>  
 <span data-ttu-id="1c841-117">Requires alink.h</span><span class="sxs-lookup"><span data-stu-id="1c841-117">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c841-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1c841-118">See also</span></span>

- [<span data-ttu-id="1c841-119">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="1c841-119">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="1c841-120">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="1c841-120">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="1c841-121">API do ALink</span><span class="sxs-lookup"><span data-stu-id="1c841-121">ALink API</span></span>](index.md)
