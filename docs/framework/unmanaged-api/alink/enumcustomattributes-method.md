---
title: Método EnumCustomAttributes
ms.date: 03/30/2017
api_name:
- EnumCustomAttributes
- IALink.EnumCustomAttributes
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- EnumCustomAttributes
helpviewer_keywords:
- EnumCustomAttributes method
ms.assetid: 08dff60c-f01b-4050-8865-ea3f95361c9f
topic_type:
- apiref
ms.openlocfilehash: 6a5b3f1e9bf1444feb73949ef7133fbd9ae35134
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446479"
---
# <a name="enumcustomattributes-method"></a><span data-ttu-id="39b12-102">Método EnumCustomAttributes</span><span class="sxs-lookup"><span data-stu-id="39b12-102">EnumCustomAttributes Method</span></span>
<span data-ttu-id="39b12-103">Retrieves assembly-level custom attributes.</span><span class="sxs-lookup"><span data-stu-id="39b12-103">Retrieves assembly-level custom attributes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39b12-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="39b12-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumCustomAttributes(  
    HALINKENUM hEnum,  
    mdToken tkType,  
    mdCustomAttribute rCustomValues[],  
    ULONG cMax,  
    ULONG* pcCustomValues  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="39b12-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="39b12-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="39b12-106">Handle of enumerator.</span><span class="sxs-lookup"><span data-stu-id="39b12-106">Handle of enumerator.</span></span>  
  
 `tkType`  
 <span data-ttu-id="39b12-107">Type of attributes to be enumerated.</span><span class="sxs-lookup"><span data-stu-id="39b12-107">Type of attributes to be enumerated.</span></span> <span data-ttu-id="39b12-108">Use `mdTokenNill` for all attributes.</span><span class="sxs-lookup"><span data-stu-id="39b12-108">Use `mdTokenNill` for all attributes.</span></span>  
  
 `rCustomValues`  
 <span data-ttu-id="39b12-109">Receives custom attributes tokens.</span><span class="sxs-lookup"><span data-stu-id="39b12-109">Receives custom attributes tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="39b12-110">Specifies size of `rCustomValues` array.</span><span class="sxs-lookup"><span data-stu-id="39b12-110">Specifies size of `rCustomValues` array.</span></span>  
  
 `pcCustomValues`  
 <span data-ttu-id="39b12-111">Optionally receives count of token values.</span><span class="sxs-lookup"><span data-stu-id="39b12-111">Optionally receives count of token values.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="39b12-112">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="39b12-112">Return Value</span></span>  
 <span data-ttu-id="39b12-113">Returns S_OK if the method succeeds.</span><span class="sxs-lookup"><span data-stu-id="39b12-113">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="39b12-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="39b12-114">Requirements</span></span>  
 <span data-ttu-id="39b12-115">Requires alink.h</span><span class="sxs-lookup"><span data-stu-id="39b12-115">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39b12-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="39b12-116">See also</span></span>

- [<span data-ttu-id="39b12-117">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="39b12-117">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="39b12-118">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="39b12-118">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="39b12-119">API do ALink</span><span class="sxs-lookup"><span data-stu-id="39b12-119">ALink API</span></span>](index.md)
