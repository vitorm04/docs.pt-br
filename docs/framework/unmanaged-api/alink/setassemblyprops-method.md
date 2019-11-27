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
ms.openlocfilehash: 4bfad8b985a8ef059031464e99a8004842b276c0
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445578"
---
# <a name="setassemblyprops-method"></a><span data-ttu-id="3b4eb-102">Método SetAssemblyProps</span><span class="sxs-lookup"><span data-stu-id="3b4eb-102">SetAssemblyProps Method</span></span>
<span data-ttu-id="3b4eb-103">Atribui propriedades no nível do assembly.</span><span class="sxs-lookup"><span data-stu-id="3b4eb-103">Assigns assembly-level properties.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3b4eb-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3b4eb-104">Syntax</span></span>  
  
```cpp  
HRESULT SetAssemblyProps(  
    mdAssembly      AssemblyID,  
    mdToken         FileToken,  
    AssemblyOptions Option,  
    VARIANT         Value  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="3b4eb-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="3b4eb-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="3b4eb-106">ID do assembly.</span><span class="sxs-lookup"><span data-stu-id="3b4eb-106">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="3b4eb-107">Arquivo que define a propriedade.</span><span class="sxs-lookup"><span data-stu-id="3b4eb-107">File that defines the property.</span></span> <span data-ttu-id="3b4eb-108">Pode ser NULL se `AssemblyID` não indicar um netmodule não associado.</span><span class="sxs-lookup"><span data-stu-id="3b4eb-108">Can be NULL if `AssemblyID` does not indicate an unbound netmodule.</span></span>  
  
 `Option`  
 <span data-ttu-id="3b4eb-109">Indica a opção a ser modificada.</span><span class="sxs-lookup"><span data-stu-id="3b4eb-109">Indicates the option to modify.</span></span>  
  
 `Value`  
 <span data-ttu-id="3b4eb-110">Novo valor da opção.</span><span class="sxs-lookup"><span data-stu-id="3b4eb-110">New value of the option.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3b4eb-111">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="3b4eb-111">Return Value</span></span>  
 <span data-ttu-id="3b4eb-112">Retorna S_OK se o método tiver sucesso.</span><span class="sxs-lookup"><span data-stu-id="3b4eb-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3b4eb-113">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="3b4eb-113">Requirements</span></span>  
 <span data-ttu-id="3b4eb-114">Requer ALink. h.</span><span class="sxs-lookup"><span data-stu-id="3b4eb-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b4eb-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3b4eb-115">See also</span></span>

- [<span data-ttu-id="3b4eb-116">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="3b4eb-116">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="3b4eb-117">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="3b4eb-117">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="3b4eb-118">API do ALink</span><span class="sxs-lookup"><span data-stu-id="3b4eb-118">ALink API</span></span>](index.md)
