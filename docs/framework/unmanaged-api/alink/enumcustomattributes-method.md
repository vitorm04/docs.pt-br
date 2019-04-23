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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b419962982fc80591ed565cceb28afb88a39495e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59199135"
---
# <a name="enumcustomattributes-method"></a><span data-ttu-id="0355f-102">Método EnumCustomAttributes</span><span class="sxs-lookup"><span data-stu-id="0355f-102">EnumCustomAttributes Method</span></span>
<span data-ttu-id="0355f-103">Recupera atributos personalizados de nível de assembly.</span><span class="sxs-lookup"><span data-stu-id="0355f-103">Retrieves assembly-level custom attributes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0355f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0355f-104">Syntax</span></span>  
  
```  
HRESULT EnumCustomAttributes(  
    HALINKENUM hEnum,  
    mdToken tkType,  
    mdCustomAttribute rCustomValues[],  
    ULONG cMax,  
    ULONG* pcCustomValues  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="0355f-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0355f-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="0355f-106">Identificador do enumerador.</span><span class="sxs-lookup"><span data-stu-id="0355f-106">Handle of enumerator.</span></span>  
  
 `tkType`  
 <span data-ttu-id="0355f-107">Tipo de atributos a serem enumerados.</span><span class="sxs-lookup"><span data-stu-id="0355f-107">Type of attributes to be enumerated.</span></span> <span data-ttu-id="0355f-108">Use `mdTokenNill` para todos os atributos.</span><span class="sxs-lookup"><span data-stu-id="0355f-108">Use `mdTokenNill` for all attributes.</span></span>  
  
 `rCustomValues`  
 <span data-ttu-id="0355f-109">Recebe os tokens de atributos personalizados.</span><span class="sxs-lookup"><span data-stu-id="0355f-109">Receives custom attributes tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="0355f-110">Especifica o tamanho de `rCustomValues` matriz.</span><span class="sxs-lookup"><span data-stu-id="0355f-110">Specifies size of `rCustomValues` array.</span></span>  
  
 `pcCustomValues`  
 <span data-ttu-id="0355f-111">Opcionalmente, recebe a contagem de valores do token.</span><span class="sxs-lookup"><span data-stu-id="0355f-111">Optionally receives count of token values.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0355f-112">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="0355f-112">Return Value</span></span>  
 <span data-ttu-id="0355f-113">Se o método for bem-sucedido, retornará S_OK.</span><span class="sxs-lookup"><span data-stu-id="0355f-113">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0355f-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0355f-114">Requirements</span></span>  
 <span data-ttu-id="0355f-115">Requer alink.h</span><span class="sxs-lookup"><span data-stu-id="0355f-115">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0355f-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0355f-116">See also</span></span>

- [<span data-ttu-id="0355f-117">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="0355f-117">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="0355f-118">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="0355f-118">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="0355f-119">API do ALink</span><span class="sxs-lookup"><span data-stu-id="0355f-119">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
