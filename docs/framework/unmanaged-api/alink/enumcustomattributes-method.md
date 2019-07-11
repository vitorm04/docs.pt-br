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
ms.openlocfilehash: 09ccf731f0494b6eda49f6a15d04970a723c473b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67742064"
---
# <a name="enumcustomattributes-method"></a><span data-ttu-id="53b47-102">Método EnumCustomAttributes</span><span class="sxs-lookup"><span data-stu-id="53b47-102">EnumCustomAttributes Method</span></span>
<span data-ttu-id="53b47-103">Recupera atributos personalizados de nível de assembly.</span><span class="sxs-lookup"><span data-stu-id="53b47-103">Retrieves assembly-level custom attributes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="53b47-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="53b47-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumCustomAttributes(  
    HALINKENUM hEnum,  
    mdToken tkType,  
    mdCustomAttribute rCustomValues[],  
    ULONG cMax,  
    ULONG* pcCustomValues  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="53b47-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="53b47-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="53b47-106">Identificador do enumerador.</span><span class="sxs-lookup"><span data-stu-id="53b47-106">Handle of enumerator.</span></span>  
  
 `tkType`  
 <span data-ttu-id="53b47-107">Tipo de atributos a serem enumerados.</span><span class="sxs-lookup"><span data-stu-id="53b47-107">Type of attributes to be enumerated.</span></span> <span data-ttu-id="53b47-108">Use `mdTokenNill` para todos os atributos.</span><span class="sxs-lookup"><span data-stu-id="53b47-108">Use `mdTokenNill` for all attributes.</span></span>  
  
 `rCustomValues`  
 <span data-ttu-id="53b47-109">Recebe os tokens de atributos personalizados.</span><span class="sxs-lookup"><span data-stu-id="53b47-109">Receives custom attributes tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="53b47-110">Especifica o tamanho de `rCustomValues` matriz.</span><span class="sxs-lookup"><span data-stu-id="53b47-110">Specifies size of `rCustomValues` array.</span></span>  
  
 `pcCustomValues`  
 <span data-ttu-id="53b47-111">Opcionalmente, recebe a contagem de valores do token.</span><span class="sxs-lookup"><span data-stu-id="53b47-111">Optionally receives count of token values.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="53b47-112">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="53b47-112">Return Value</span></span>  
 <span data-ttu-id="53b47-113">Se o método for bem-sucedido, retornará S_OK.</span><span class="sxs-lookup"><span data-stu-id="53b47-113">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="53b47-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="53b47-114">Requirements</span></span>  
 <span data-ttu-id="53b47-115">Requer alink.h</span><span class="sxs-lookup"><span data-stu-id="53b47-115">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53b47-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="53b47-116">See also</span></span>

- [<span data-ttu-id="53b47-117">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="53b47-117">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="53b47-118">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="53b47-118">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="53b47-119">API do ALink</span><span class="sxs-lookup"><span data-stu-id="53b47-119">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
