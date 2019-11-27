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
ms.openlocfilehash: ec0a86e3396ad42152bc0a244f74ad13deba16e4
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446514"
---
# <a name="emitassemblycustomattribute-method"></a><span data-ttu-id="3c14b-102">Método EmitAssemblyCustomAttribute</span><span class="sxs-lookup"><span data-stu-id="3c14b-102">EmitAssemblyCustomAttribute Method</span></span>
<span data-ttu-id="3c14b-103">Chamada para definir atributos personalizados no nível do assembly.</span><span class="sxs-lookup"><span data-stu-id="3c14b-103">Call to set assembly-level custom attributes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3c14b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3c14b-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="3c14b-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="3c14b-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="3c14b-106">ID do assembly.</span><span class="sxs-lookup"><span data-stu-id="3c14b-106">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="3c14b-107">Arquivo que rearquivou o atributo.</span><span class="sxs-lookup"><span data-stu-id="3c14b-107">File that defiles the attribute.</span></span> <span data-ttu-id="3c14b-108">Pode ser NULL se `AssemblyID` não indicar um netmodule não associado.</span><span class="sxs-lookup"><span data-stu-id="3c14b-108">Can be NULL if `AssemblyID` does not indicate an unbound netmodule.</span></span>  
  
 `tkType`  
 <span data-ttu-id="3c14b-109">Tipo do atributo personalizado.</span><span class="sxs-lookup"><span data-stu-id="3c14b-109">Type of the custom attribute.</span></span>  
  
 `pCustomValue`  
 <span data-ttu-id="3c14b-110">Dados de valor personalizado.</span><span class="sxs-lookup"><span data-stu-id="3c14b-110">Custom value data.</span></span>  
  
 `cbCustomValue`  
 <span data-ttu-id="3c14b-111">Comprimento dos dados do valor personalizado.</span><span class="sxs-lookup"><span data-stu-id="3c14b-111">Length of custom value data.</span></span>  
  
 `bSecurity`  
 <span data-ttu-id="3c14b-112">TRUE se o atributo personalizado estiver relacionado à assinatura de assembly.</span><span class="sxs-lookup"><span data-stu-id="3c14b-112">TRUE if the custom attribute is related to assembly signing.</span></span>  
  
 `bAllowMulti`  
 <span data-ttu-id="3c14b-113">TRUE se vários atributos forem emitidos.</span><span class="sxs-lookup"><span data-stu-id="3c14b-113">TRUE if multiple attributes are to be emitted.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3c14b-114">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="3c14b-114">Return Value</span></span>  
 <span data-ttu-id="3c14b-115">Retorna S_OK se o método tiver sucesso.</span><span class="sxs-lookup"><span data-stu-id="3c14b-115">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3c14b-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3c14b-116">Requirements</span></span>  
 <span data-ttu-id="3c14b-117">Requer ALink. h</span><span class="sxs-lookup"><span data-stu-id="3c14b-117">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c14b-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3c14b-118">See also</span></span>

- [<span data-ttu-id="3c14b-119">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="3c14b-119">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="3c14b-120">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="3c14b-120">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="3c14b-121">API do ALink</span><span class="sxs-lookup"><span data-stu-id="3c14b-121">ALink API</span></span>](index.md)
