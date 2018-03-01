---
title: "Método EmitAssemblyCustomAttribute"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9cc7709ef060642f12a8bc7d048e520427a5c674
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="emitassemblycustomattribute-method"></a><span data-ttu-id="d2ef4-102">Método EmitAssemblyCustomAttribute</span><span class="sxs-lookup"><span data-stu-id="d2ef4-102">EmitAssemblyCustomAttribute Method</span></span>
<span data-ttu-id="d2ef4-103">Chamada para definir atributos de nível de assembly personalizados.</span><span class="sxs-lookup"><span data-stu-id="d2ef4-103">Call to set assembly-level custom attributes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d2ef4-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d2ef4-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="d2ef4-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d2ef4-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="d2ef4-106">ID do assembly.</span><span class="sxs-lookup"><span data-stu-id="d2ef4-106">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="d2ef4-107">Arquivo defiles o atributo.</span><span class="sxs-lookup"><span data-stu-id="d2ef4-107">File that defiles the attribute.</span></span> <span data-ttu-id="d2ef4-108">Pode ser NULL se `AssemblyID` não indica um netmodule não associado.</span><span class="sxs-lookup"><span data-stu-id="d2ef4-108">Can be NULL if `AssemblyID` does not indicate an unbound netmodule.</span></span>  
  
 `tkType`  
 <span data-ttu-id="d2ef4-109">Tipo de atributo personalizado.</span><span class="sxs-lookup"><span data-stu-id="d2ef4-109">Type of the custom attribute.</span></span>  
  
 `pCustomValue`  
 <span data-ttu-id="d2ef4-110">Dados de valor personalizado.</span><span class="sxs-lookup"><span data-stu-id="d2ef4-110">Custom value data.</span></span>  
  
 `cbCustomValue`  
 <span data-ttu-id="d2ef4-111">Comprimento dos dados de valor personalizado.</span><span class="sxs-lookup"><span data-stu-id="d2ef4-111">Length of custom value data.</span></span>  
  
 `bSecurity`  
 <span data-ttu-id="d2ef4-112">TRUE se o atributo personalizado está relacionado à assinatura do assembly.</span><span class="sxs-lookup"><span data-stu-id="d2ef4-112">TRUE if the custom attribute is related to assembly signing.</span></span>  
  
 `bAllowMulti`  
 <span data-ttu-id="d2ef4-113">TRUE se vários atributos devem ser emitidos.</span><span class="sxs-lookup"><span data-stu-id="d2ef4-113">TRUE if multiple attributes are to be emitted.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d2ef4-114">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="d2ef4-114">Return Value</span></span>  
 <span data-ttu-id="d2ef4-115">Retorna S_OK se o método for bem-sucedido.</span><span class="sxs-lookup"><span data-stu-id="d2ef4-115">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d2ef4-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d2ef4-116">Requirements</span></span>  
 <span data-ttu-id="d2ef4-117">Requer alink.h</span><span class="sxs-lookup"><span data-stu-id="d2ef4-117">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2ef4-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d2ef4-118">See Also</span></span>  
 [<span data-ttu-id="d2ef4-119">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="d2ef4-119">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="d2ef4-120">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="d2ef4-120">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="d2ef4-121">API do ALink</span><span class="sxs-lookup"><span data-stu-id="d2ef4-121">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
