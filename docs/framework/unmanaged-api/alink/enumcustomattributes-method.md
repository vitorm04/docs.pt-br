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
ms.openlocfilehash: 5d8827f46a12bd090fa27e71072d833607d34677
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70777354"
---
# <a name="enumcustomattributes-method"></a><span data-ttu-id="76d43-102">Método EnumCustomAttributes</span><span class="sxs-lookup"><span data-stu-id="76d43-102">EnumCustomAttributes Method</span></span>
<span data-ttu-id="76d43-103">Recupera atributos personalizados no nível do assembly.</span><span class="sxs-lookup"><span data-stu-id="76d43-103">Retrieves assembly-level custom attributes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="76d43-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="76d43-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumCustomAttributes(  
    HALINKENUM hEnum,  
    mdToken tkType,  
    mdCustomAttribute rCustomValues[],  
    ULONG cMax,  
    ULONG* pcCustomValues  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="76d43-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="76d43-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="76d43-106">Identificador do enumerador.</span><span class="sxs-lookup"><span data-stu-id="76d43-106">Handle of enumerator.</span></span>  
  
 `tkType`  
 <span data-ttu-id="76d43-107">Tipo de atributos a serem enumerados.</span><span class="sxs-lookup"><span data-stu-id="76d43-107">Type of attributes to be enumerated.</span></span> <span data-ttu-id="76d43-108">Use `mdTokenNill` para todos os atributos.</span><span class="sxs-lookup"><span data-stu-id="76d43-108">Use `mdTokenNill` for all attributes.</span></span>  
  
 `rCustomValues`  
 <span data-ttu-id="76d43-109">Recebe tokens de atributos personalizados.</span><span class="sxs-lookup"><span data-stu-id="76d43-109">Receives custom attributes tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="76d43-110">Especifica o tamanho `rCustomValues` da matriz.</span><span class="sxs-lookup"><span data-stu-id="76d43-110">Specifies size of `rCustomValues` array.</span></span>  
  
 `pcCustomValues`  
 <span data-ttu-id="76d43-111">Opcionalmente, recebe a contagem de valores de token.</span><span class="sxs-lookup"><span data-stu-id="76d43-111">Optionally receives count of token values.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="76d43-112">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="76d43-112">Return Value</span></span>  
 <span data-ttu-id="76d43-113">Retornará S_OK se o método tiver sucesso.</span><span class="sxs-lookup"><span data-stu-id="76d43-113">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="76d43-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="76d43-114">Requirements</span></span>  
 <span data-ttu-id="76d43-115">Requer ALink. h</span><span class="sxs-lookup"><span data-stu-id="76d43-115">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76d43-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="76d43-116">See also</span></span>

- [<span data-ttu-id="76d43-117">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="76d43-117">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="76d43-118">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="76d43-118">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="76d43-119">API do ALink</span><span class="sxs-lookup"><span data-stu-id="76d43-119">ALink API</span></span>](index.md)
