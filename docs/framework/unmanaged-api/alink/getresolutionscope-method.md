---
title: Método GetResolutionScope
ms.date: 03/30/2017
api_name:
- IALink.GetResolutionScope
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GetResolutionScope
helpviewer_keywords:
- GetResolutionScope method
ms.assetid: 5b48ca60-dacd-44b2-9979-4a5122f00812
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f8d230d5396c5a088fa76a7ca145b4a22d1e1d07
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54543351"
---
# <a name="getresolutionscope-method"></a><span data-ttu-id="e3082-102">Método GetResolutionScope</span><span class="sxs-lookup"><span data-stu-id="e3082-102">GetResolutionScope Method</span></span>
<span data-ttu-id="e3082-103">Recupera o escopo de um determinado tipo.</span><span class="sxs-lookup"><span data-stu-id="e3082-103">Retrieves the scope of a given type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3082-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e3082-104">Syntax</span></span>  
  
```  
HRESULT GetResolutionScope(  
    mdAssembly  AssemblyID,  
    mdToken     FileToken,  
    mdToken     TargetFile,  
    mdToken*    pScope  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e3082-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e3082-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="e3082-106">ID do assembly.</span><span class="sxs-lookup"><span data-stu-id="e3082-106">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="e3082-107">Arquivo que é a necessidade de uma referência.</span><span class="sxs-lookup"><span data-stu-id="e3082-107">File that is in need of a reference.</span></span>  
  
 `TargetFile`  
 <span data-ttu-id="e3082-108">Token de arquivo desse tipo é definido no, geralmente são recuperadas com [método ImportFile](../../../../docs/framework/unmanaged-api/alink/importfile-method.md).</span><span class="sxs-lookup"><span data-stu-id="e3082-108">Token of file that type is defined in, usually retrieved with [ImportFile Method](../../../../docs/framework/unmanaged-api/alink/importfile-method.md).</span></span>  
  
 `pScope`  
 <span data-ttu-id="e3082-109">Recebe o assembly ou uma referência de módulo.</span><span class="sxs-lookup"><span data-stu-id="e3082-109">Receives the assembly or module reference.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e3082-110">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="e3082-110">Return Value</span></span>  
 <span data-ttu-id="e3082-111">Se o método for bem-sucedido, retornará S_OK.</span><span class="sxs-lookup"><span data-stu-id="e3082-111">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e3082-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e3082-112">Requirements</span></span>  
 <span data-ttu-id="e3082-113">Requer alink.h.</span><span class="sxs-lookup"><span data-stu-id="e3082-113">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3082-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e3082-114">See also</span></span>
- [<span data-ttu-id="e3082-115">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="e3082-115">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="e3082-116">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="e3082-116">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="e3082-117">API do ALink</span><span class="sxs-lookup"><span data-stu-id="e3082-117">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
