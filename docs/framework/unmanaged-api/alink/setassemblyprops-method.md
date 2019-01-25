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
ms.openlocfilehash: 65d6e929a0a6fb5e1933a6c9216dfc5b56342113
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54560640"
---
# <a name="setassemblyprops-method"></a><span data-ttu-id="037bd-102">Método SetAssemblyProps</span><span class="sxs-lookup"><span data-stu-id="037bd-102">SetAssemblyProps Method</span></span>
<span data-ttu-id="037bd-103">Atribui a propriedades de nível de assembly.</span><span class="sxs-lookup"><span data-stu-id="037bd-103">Assigns assembly-level properties.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="037bd-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="037bd-104">Syntax</span></span>  
  
```  
HRESULT SetAssemblyProps(  
    mdAssembly      AssemblyID,  
    mdToken         FileToken,  
    AssemblyOptions Option,  
    VARIANT         Value  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="037bd-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="037bd-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="037bd-106">ID do assembly.</span><span class="sxs-lookup"><span data-stu-id="037bd-106">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="037bd-107">Arquivo que define a propriedade.</span><span class="sxs-lookup"><span data-stu-id="037bd-107">File that defines the property.</span></span> <span data-ttu-id="037bd-108">Pode ser NULL se `AssemblyID` não indica um netmodule não associado.</span><span class="sxs-lookup"><span data-stu-id="037bd-108">Can be NULL if `AssemblyID` does not indicate an unbound netmodule.</span></span>  
  
 `Option`  
 <span data-ttu-id="037bd-109">Indica a opção de modificar.</span><span class="sxs-lookup"><span data-stu-id="037bd-109">Indicates the option to modify.</span></span>  
  
 `Value`  
 <span data-ttu-id="037bd-110">Novo valor da opção.</span><span class="sxs-lookup"><span data-stu-id="037bd-110">New value of the option.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="037bd-111">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="037bd-111">Return Value</span></span>  
 <span data-ttu-id="037bd-112">Se o método for bem-sucedido, retornará S_OK.</span><span class="sxs-lookup"><span data-stu-id="037bd-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="037bd-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="037bd-113">Requirements</span></span>  
 <span data-ttu-id="037bd-114">Requer alink.h.</span><span class="sxs-lookup"><span data-stu-id="037bd-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="037bd-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="037bd-115">See also</span></span>
- [<span data-ttu-id="037bd-116">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="037bd-116">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="037bd-117">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="037bd-117">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="037bd-118">API do ALink</span><span class="sxs-lookup"><span data-stu-id="037bd-118">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
