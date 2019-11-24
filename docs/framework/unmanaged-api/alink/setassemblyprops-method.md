---
title: Método SetAssemblyProps
ms.date: 03/30/2017
api_name:
- IALink.SetAssemblyProps
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- SetAssemblyProps
helpviewer_keywords:
- SetAssemblyProps method
ms.assetid: a3d7cf29-1414-49e6-8aae-9b3283c4f5f0
topic_type:
- apiref
ms.openlocfilehash: 4bfad8b985a8ef059031464e99a8004842b276c0
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445578"
---
# <a name="setassemblyprops-method"></a><span data-ttu-id="96ac0-102">Método SetAssemblyProps</span><span class="sxs-lookup"><span data-stu-id="96ac0-102">SetAssemblyProps Method</span></span>
<span data-ttu-id="96ac0-103">Assigns assembly-level properties.</span><span class="sxs-lookup"><span data-stu-id="96ac0-103">Assigns assembly-level properties.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96ac0-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="96ac0-104">Syntax</span></span>  
  
```cpp  
HRESULT SetAssemblyProps(  
    mdAssembly      AssemblyID,  
    mdToken         FileToken,  
    AssemblyOptions Option,  
    VARIANT         Value  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="96ac0-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="96ac0-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="96ac0-106">ID of the assembly.</span><span class="sxs-lookup"><span data-stu-id="96ac0-106">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="96ac0-107">File that defines the property.</span><span class="sxs-lookup"><span data-stu-id="96ac0-107">File that defines the property.</span></span> <span data-ttu-id="96ac0-108">Can be NULL if `AssemblyID` does not indicate an unbound netmodule.</span><span class="sxs-lookup"><span data-stu-id="96ac0-108">Can be NULL if `AssemblyID` does not indicate an unbound netmodule.</span></span>  
  
 `Option`  
 <span data-ttu-id="96ac0-109">Indicates the option to modify.</span><span class="sxs-lookup"><span data-stu-id="96ac0-109">Indicates the option to modify.</span></span>  
  
 `Value`  
 <span data-ttu-id="96ac0-110">New value of the option.</span><span class="sxs-lookup"><span data-stu-id="96ac0-110">New value of the option.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="96ac0-111">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="96ac0-111">Return Value</span></span>  
 <span data-ttu-id="96ac0-112">Returns S_OK if the method succeeds.</span><span class="sxs-lookup"><span data-stu-id="96ac0-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="96ac0-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="96ac0-113">Requirements</span></span>  
 <span data-ttu-id="96ac0-114">Requires alink.h.</span><span class="sxs-lookup"><span data-stu-id="96ac0-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96ac0-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="96ac0-115">See also</span></span>

- [<span data-ttu-id="96ac0-116">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="96ac0-116">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="96ac0-117">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="96ac0-117">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="96ac0-118">API do ALink</span><span class="sxs-lookup"><span data-stu-id="96ac0-118">ALink API</span></span>](index.md)
