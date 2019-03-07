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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 69914bce7ed322d90cfbd03dd611e2b745dfe066
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57470019"
---
# <a name="emitassemblycustomattribute-method"></a><span data-ttu-id="14fda-102">Método EmitAssemblyCustomAttribute</span><span class="sxs-lookup"><span data-stu-id="14fda-102">EmitAssemblyCustomAttribute Method</span></span>
<span data-ttu-id="14fda-103">Chamada para definir atributos de nível de assembly personalizados.</span><span class="sxs-lookup"><span data-stu-id="14fda-103">Call to set assembly-level custom attributes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="14fda-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="14fda-104">Syntax</span></span>  
  
```  
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
  
## <a name="parameters"></a><span data-ttu-id="14fda-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="14fda-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="14fda-106">ID do assembly.</span><span class="sxs-lookup"><span data-stu-id="14fda-106">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="14fda-107">Arquivo que descreve o atributo.</span><span class="sxs-lookup"><span data-stu-id="14fda-107">File that defiles the attribute.</span></span> <span data-ttu-id="14fda-108">Pode ser NULL se `AssemblyID` não indica um netmodule não associado.</span><span class="sxs-lookup"><span data-stu-id="14fda-108">Can be NULL if `AssemblyID` does not indicate an unbound netmodule.</span></span>  
  
 `tkType`  
 <span data-ttu-id="14fda-109">Tipo de atributo personalizado.</span><span class="sxs-lookup"><span data-stu-id="14fda-109">Type of the custom attribute.</span></span>  
  
 `pCustomValue`  
 <span data-ttu-id="14fda-110">Dados de valor personalizado.</span><span class="sxs-lookup"><span data-stu-id="14fda-110">Custom value data.</span></span>  
  
 `cbCustomValue`  
 <span data-ttu-id="14fda-111">Comprimento dos dados de valor personalizado.</span><span class="sxs-lookup"><span data-stu-id="14fda-111">Length of custom value data.</span></span>  
  
 `bSecurity`  
 <span data-ttu-id="14fda-112">TRUE se o atributo personalizado está relacionado à assinatura do assembly.</span><span class="sxs-lookup"><span data-stu-id="14fda-112">TRUE if the custom attribute is related to assembly signing.</span></span>  
  
 `bAllowMulti`  
 <span data-ttu-id="14fda-113">TRUE se vários atributos devem ser emitidos.</span><span class="sxs-lookup"><span data-stu-id="14fda-113">TRUE if multiple attributes are to be emitted.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="14fda-114">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="14fda-114">Return Value</span></span>  
 <span data-ttu-id="14fda-115">Se o método for bem-sucedido, retornará S_OK.</span><span class="sxs-lookup"><span data-stu-id="14fda-115">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="14fda-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="14fda-116">Requirements</span></span>  
 <span data-ttu-id="14fda-117">Requer alink.h</span><span class="sxs-lookup"><span data-stu-id="14fda-117">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14fda-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="14fda-118">See also</span></span>
- [<span data-ttu-id="14fda-119">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="14fda-119">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="14fda-120">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="14fda-120">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="14fda-121">API do ALink</span><span class="sxs-lookup"><span data-stu-id="14fda-121">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
