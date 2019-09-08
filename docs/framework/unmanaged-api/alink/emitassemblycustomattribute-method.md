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
ms.openlocfilehash: 77d54f6c8f67dda5132518d1fbd579a91ce82071
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70777445"
---
# <a name="emitassemblycustomattribute-method"></a><span data-ttu-id="8264a-102">Método EmitAssemblyCustomAttribute</span><span class="sxs-lookup"><span data-stu-id="8264a-102">EmitAssemblyCustomAttribute Method</span></span>
<span data-ttu-id="8264a-103">Chamada para definir atributos personalizados no nível do assembly.</span><span class="sxs-lookup"><span data-stu-id="8264a-103">Call to set assembly-level custom attributes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8264a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8264a-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="8264a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8264a-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="8264a-106">ID do assembly.</span><span class="sxs-lookup"><span data-stu-id="8264a-106">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="8264a-107">Arquivo que rearquivou o atributo.</span><span class="sxs-lookup"><span data-stu-id="8264a-107">File that defiles the attribute.</span></span> <span data-ttu-id="8264a-108">Pode ser NULL se `AssemblyID` não indicar um netmodule não associado.</span><span class="sxs-lookup"><span data-stu-id="8264a-108">Can be NULL if `AssemblyID` does not indicate an unbound netmodule.</span></span>  
  
 `tkType`  
 <span data-ttu-id="8264a-109">Tipo do atributo personalizado.</span><span class="sxs-lookup"><span data-stu-id="8264a-109">Type of the custom attribute.</span></span>  
  
 `pCustomValue`  
 <span data-ttu-id="8264a-110">Dados de valor personalizado.</span><span class="sxs-lookup"><span data-stu-id="8264a-110">Custom value data.</span></span>  
  
 `cbCustomValue`  
 <span data-ttu-id="8264a-111">Comprimento dos dados do valor personalizado.</span><span class="sxs-lookup"><span data-stu-id="8264a-111">Length of custom value data.</span></span>  
  
 `bSecurity`  
 <span data-ttu-id="8264a-112">TRUE se o atributo personalizado estiver relacionado à assinatura de assembly.</span><span class="sxs-lookup"><span data-stu-id="8264a-112">TRUE if the custom attribute is related to assembly signing.</span></span>  
  
 `bAllowMulti`  
 <span data-ttu-id="8264a-113">TRUE se vários atributos forem emitidos.</span><span class="sxs-lookup"><span data-stu-id="8264a-113">TRUE if multiple attributes are to be emitted.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8264a-114">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="8264a-114">Return Value</span></span>  
 <span data-ttu-id="8264a-115">Retornará S_OK se o método tiver sucesso.</span><span class="sxs-lookup"><span data-stu-id="8264a-115">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8264a-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8264a-116">Requirements</span></span>  
 <span data-ttu-id="8264a-117">Requer ALink. h</span><span class="sxs-lookup"><span data-stu-id="8264a-117">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8264a-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8264a-118">See also</span></span>

- [<span data-ttu-id="8264a-119">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="8264a-119">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="8264a-120">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="8264a-120">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="8264a-121">API do ALink</span><span class="sxs-lookup"><span data-stu-id="8264a-121">ALink API</span></span>](index.md)
