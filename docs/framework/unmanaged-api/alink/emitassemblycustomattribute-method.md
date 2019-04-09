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
ms.openlocfilehash: 67073f04cfe981dd383369029d9a4b436929a0a6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59117839"
---
# <a name="emitassemblycustomattribute-method"></a><span data-ttu-id="d78c4-102">Método EmitAssemblyCustomAttribute</span><span class="sxs-lookup"><span data-stu-id="d78c4-102">EmitAssemblyCustomAttribute Method</span></span>
<span data-ttu-id="d78c4-103">Chamada para definir atributos de nível de assembly personalizados.</span><span class="sxs-lookup"><span data-stu-id="d78c4-103">Call to set assembly-level custom attributes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d78c4-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d78c4-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="d78c4-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d78c4-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="d78c4-106">ID do assembly.</span><span class="sxs-lookup"><span data-stu-id="d78c4-106">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="d78c4-107">Arquivo que descreve o atributo.</span><span class="sxs-lookup"><span data-stu-id="d78c4-107">File that defiles the attribute.</span></span> <span data-ttu-id="d78c4-108">Pode ser NULL se `AssemblyID` não indica um netmodule não associado.</span><span class="sxs-lookup"><span data-stu-id="d78c4-108">Can be NULL if `AssemblyID` does not indicate an unbound netmodule.</span></span>  
  
 `tkType`  
 <span data-ttu-id="d78c4-109">Tipo de atributo personalizado.</span><span class="sxs-lookup"><span data-stu-id="d78c4-109">Type of the custom attribute.</span></span>  
  
 `pCustomValue`  
 <span data-ttu-id="d78c4-110">Dados de valor personalizado.</span><span class="sxs-lookup"><span data-stu-id="d78c4-110">Custom value data.</span></span>  
  
 `cbCustomValue`  
 <span data-ttu-id="d78c4-111">Comprimento dos dados de valor personalizado.</span><span class="sxs-lookup"><span data-stu-id="d78c4-111">Length of custom value data.</span></span>  
  
 `bSecurity`  
 <span data-ttu-id="d78c4-112">TRUE se o atributo personalizado está relacionado à assinatura do assembly.</span><span class="sxs-lookup"><span data-stu-id="d78c4-112">TRUE if the custom attribute is related to assembly signing.</span></span>  
  
 `bAllowMulti`  
 <span data-ttu-id="d78c4-113">TRUE se vários atributos devem ser emitidos.</span><span class="sxs-lookup"><span data-stu-id="d78c4-113">TRUE if multiple attributes are to be emitted.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d78c4-114">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="d78c4-114">Return Value</span></span>  
 <span data-ttu-id="d78c4-115">Se o método for bem-sucedido, retornará S_OK.</span><span class="sxs-lookup"><span data-stu-id="d78c4-115">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d78c4-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d78c4-116">Requirements</span></span>  
 <span data-ttu-id="d78c4-117">Requer alink.h</span><span class="sxs-lookup"><span data-stu-id="d78c4-117">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d78c4-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d78c4-118">See also</span></span>

- [<span data-ttu-id="d78c4-119">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="d78c4-119">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="d78c4-120">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="d78c4-120">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="d78c4-121">API do ALink</span><span class="sxs-lookup"><span data-stu-id="d78c4-121">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
