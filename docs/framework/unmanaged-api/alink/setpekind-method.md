---
title: Método SetPEKind
ms.date: 03/30/2017
api_name:
- IALink2.SetPEKind
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- SetPEKind
helpviewer_keywords:
- SetPEKind method
ms.assetid: 050e77ee-3014-45c0-9e29-2ebe29347b0d
topic_type:
- apiref
ms.openlocfilehash: dfbc10bdbe633450dee2e27524c29ead21fb739e
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445541"
---
# <a name="setpekind-method"></a><span data-ttu-id="462ff-102">Método SetPEKind</span><span class="sxs-lookup"><span data-stu-id="462ff-102">SetPEKind Method</span></span>
<span data-ttu-id="462ff-103">Determines the portable executable type, either machine-specific or machine-agnostic.</span><span class="sxs-lookup"><span data-stu-id="462ff-103">Determines the portable executable type, either machine-specific or machine-agnostic.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="462ff-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="462ff-104">Syntax</span></span>  
  
```cpp  
HRESULT SetPEKind(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwPEKind,  
    DWORD dwMachine  
) PURE;   
```  
  
## <a name="parameters"></a><span data-ttu-id="462ff-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="462ff-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="462ff-106">ID of the assembly.</span><span class="sxs-lookup"><span data-stu-id="462ff-106">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="462ff-107">Token of file for which the PE type is to be set.</span><span class="sxs-lookup"><span data-stu-id="462ff-107">Token of file for which the PE type is to be set.</span></span> <span data-ttu-id="462ff-108">Can be NULL if `AssemblyID` does not indicate an unbound netmodule.</span><span class="sxs-lookup"><span data-stu-id="462ff-108">Can be NULL if `AssemblyID` does not indicate an unbound netmodule.</span></span>  
  
 `dwPEKind`  
 <span data-ttu-id="462ff-109">The type of PE, as indicated by the [CorPEKind Enumeration](../metadata/corpekind-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="462ff-109">The type of PE, as indicated by the [CorPEKind Enumeration](../metadata/corpekind-enumeration.md).</span></span>  
  
 `dwMachine`  
 <span data-ttu-id="462ff-110">The target machine architecture, as indicated in the NT header.</span><span class="sxs-lookup"><span data-stu-id="462ff-110">The target machine architecture, as indicated in the NT header.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="462ff-111">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="462ff-111">Return Value</span></span>  
 <span data-ttu-id="462ff-112">Returns S_OK if the method succeeds.</span><span class="sxs-lookup"><span data-stu-id="462ff-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="462ff-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="462ff-113">Requirements</span></span>  
 <span data-ttu-id="462ff-114">Requires alink.h.</span><span class="sxs-lookup"><span data-stu-id="462ff-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="462ff-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="462ff-115">See also</span></span>

- [<span data-ttu-id="462ff-116">Método GetPEKind</span><span class="sxs-lookup"><span data-stu-id="462ff-116">GetPEKind Method</span></span>](../metadata/imetadataimport2-getpekind-method.md)
- [<span data-ttu-id="462ff-117">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="462ff-117">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="462ff-118">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="462ff-118">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="462ff-119">API do ALink</span><span class="sxs-lookup"><span data-stu-id="462ff-119">ALink API</span></span>](index.md)
