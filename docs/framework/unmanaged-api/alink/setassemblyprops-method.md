---
title: Método SetAssemblyProps
ms.date: 03/30/2017
api_name:
- IALink.SetAssemblyProps
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- SetAssemblyProps
helpviewer_keywords:
- SetAssemblyProps method
ms.assetid: a3d7cf29-1414-49e6-8aae-9b3283c4f5f0
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 180eb1a3129cfcd96668ecfee11947c15c5e0915
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70776906"
---
# <a name="setassemblyprops-method"></a><span data-ttu-id="ec089-102">Método SetAssemblyProps</span><span class="sxs-lookup"><span data-stu-id="ec089-102">SetAssemblyProps Method</span></span>
<span data-ttu-id="ec089-103">Atribui propriedades no nível do assembly.</span><span class="sxs-lookup"><span data-stu-id="ec089-103">Assigns assembly-level properties.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ec089-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ec089-104">Syntax</span></span>  
  
```cpp  
HRESULT SetAssemblyProps(  
    mdAssembly      AssemblyID,  
    mdToken         FileToken,  
    AssemblyOptions Option,  
    VARIANT         Value  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="ec089-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ec089-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="ec089-106">ID do assembly.</span><span class="sxs-lookup"><span data-stu-id="ec089-106">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="ec089-107">Arquivo que define a propriedade.</span><span class="sxs-lookup"><span data-stu-id="ec089-107">File that defines the property.</span></span> <span data-ttu-id="ec089-108">Pode ser NULL se `AssemblyID` não indicar um netmodule não associado.</span><span class="sxs-lookup"><span data-stu-id="ec089-108">Can be NULL if `AssemblyID` does not indicate an unbound netmodule.</span></span>  
  
 `Option`  
 <span data-ttu-id="ec089-109">Indica a opção a ser modificada.</span><span class="sxs-lookup"><span data-stu-id="ec089-109">Indicates the option to modify.</span></span>  
  
 `Value`  
 <span data-ttu-id="ec089-110">Novo valor da opção.</span><span class="sxs-lookup"><span data-stu-id="ec089-110">New value of the option.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ec089-111">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="ec089-111">Return Value</span></span>  
 <span data-ttu-id="ec089-112">Retornará S_OK se o método tiver sucesso.</span><span class="sxs-lookup"><span data-stu-id="ec089-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ec089-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ec089-113">Requirements</span></span>  
 <span data-ttu-id="ec089-114">Requer ALink. h.</span><span class="sxs-lookup"><span data-stu-id="ec089-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec089-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ec089-115">See also</span></span>

- [<span data-ttu-id="ec089-116">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="ec089-116">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="ec089-117">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="ec089-117">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="ec089-118">API do ALink</span><span class="sxs-lookup"><span data-stu-id="ec089-118">ALink API</span></span>](index.md)
