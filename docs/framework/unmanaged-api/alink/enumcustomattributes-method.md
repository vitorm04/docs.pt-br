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
ms.openlocfilehash: 5a3d7d3bb05a878f4d9832cf39a8e8863929c4e5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33403208"
---
# <a name="enumcustomattributes-method"></a><span data-ttu-id="7e176-102">Método EnumCustomAttributes</span><span class="sxs-lookup"><span data-stu-id="7e176-102">EnumCustomAttributes Method</span></span>
<span data-ttu-id="7e176-103">Recupera atributos personalizados de nível de assembly.</span><span class="sxs-lookup"><span data-stu-id="7e176-103">Retrieves assembly-level custom attributes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7e176-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7e176-104">Syntax</span></span>  
  
```  
HRESULT EnumCustomAttributes(  
    HALINKENUM hEnum,  
    mdToken tkType,  
    mdCustomAttribute rCustomValues[],  
    ULONG cMax,  
    ULONG* pcCustomValues  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7e176-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7e176-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="7e176-106">Identificador do enumerador.</span><span class="sxs-lookup"><span data-stu-id="7e176-106">Handle of enumerator.</span></span>  
  
 `tkType`  
 <span data-ttu-id="7e176-107">Tipo de atributos a serem enumerados.</span><span class="sxs-lookup"><span data-stu-id="7e176-107">Type of attributes to be enumerated.</span></span> <span data-ttu-id="7e176-108">Use `mdTokenNill` para todos os atributos.</span><span class="sxs-lookup"><span data-stu-id="7e176-108">Use `mdTokenNill` for all attributes.</span></span>  
  
 `rCustomValues`  
 <span data-ttu-id="7e176-109">Recebe os tokens de atributos personalizados.</span><span class="sxs-lookup"><span data-stu-id="7e176-109">Receives custom attributes tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="7e176-110">Especifica o tamanho de `rCustomValues` matriz.</span><span class="sxs-lookup"><span data-stu-id="7e176-110">Specifies size of `rCustomValues` array.</span></span>  
  
 `pcCustomValues`  
 <span data-ttu-id="7e176-111">Opcionalmente, recebe a contagem de valores do token.</span><span class="sxs-lookup"><span data-stu-id="7e176-111">Optionally receives count of token values.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7e176-112">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="7e176-112">Return Value</span></span>  
 <span data-ttu-id="7e176-113">Retorna S_OK se o método for bem-sucedido.</span><span class="sxs-lookup"><span data-stu-id="7e176-113">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7e176-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7e176-114">Requirements</span></span>  
 <span data-ttu-id="7e176-115">Requer alink.h</span><span class="sxs-lookup"><span data-stu-id="7e176-115">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e176-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7e176-116">See Also</span></span>  
 [<span data-ttu-id="7e176-117">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="7e176-117">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="7e176-118">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="7e176-118">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="7e176-119">API do ALink</span><span class="sxs-lookup"><span data-stu-id="7e176-119">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
