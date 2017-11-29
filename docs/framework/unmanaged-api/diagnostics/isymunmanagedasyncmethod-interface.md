---
title: Interface ISymUnmanagedAsyncMethod
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: f2de5224-fd91-45de-9e58-bc600c6d22f1
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 3ee944940cef0d3162a020c81353fd6b8cfb82f8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedasyncmethod-interface"></a><span data-ttu-id="51719-102">Interface ISymUnmanagedAsyncMethod</span><span class="sxs-lookup"><span data-stu-id="51719-102">ISymUnmanagedAsyncMethod Interface</span></span>
<span data-ttu-id="51719-103">Essa interface é o complemento de leitura para [ISymUnmanagedAsyncMethodPropertiesWriter Interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md).</span><span class="sxs-lookup"><span data-stu-id="51719-103">This interface is the reading complement to [ISymUnmanagedAsyncMethodPropertiesWriter Interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="51719-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="51719-104">Syntax</span></span>  
  
```idl  
[object,uuid(B20D55B3-532E-4906-87E7-25BD5734ABD2),pointer_default(unique)]interface ISymUnmanagedAsyncMethod : IUnknown  
```  
  
## <a name="methods"></a><span data-ttu-id="51719-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="51719-105">Methods</span></span>  
 <span data-ttu-id="51719-106">Essa interface contém os seguintes métodos:</span><span class="sxs-lookup"><span data-stu-id="51719-106">This interface contains the following methods:</span></span>  
  
|<span data-ttu-id="51719-107">Método</span><span class="sxs-lookup"><span data-stu-id="51719-107">Method</span></span>|<span data-ttu-id="51719-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="51719-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="51719-109">Método GetAsyncStepInfo</span><span class="sxs-lookup"><span data-stu-id="51719-109">GetAsyncStepInfo Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-getasyncstepinfo-method.md)|<span data-ttu-id="51719-110">Consulte [método DefineAsyncStepInfo](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span><span class="sxs-lookup"><span data-stu-id="51719-110">See [DefineAsyncStepInfo Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span></span>|  
|[<span data-ttu-id="51719-111">Método GetAsyncStepInfoCount</span><span class="sxs-lookup"><span data-stu-id="51719-111">GetAsyncStepInfoCount Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-getasyncstepinfocount-method.md)|<span data-ttu-id="51719-112">Consulte [método DefineAsyncStepInfo](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span><span class="sxs-lookup"><span data-stu-id="51719-112">See [DefineAsyncStepInfo Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span></span>|  
|[<span data-ttu-id="51719-113">Método GetCatchHandlerILOffset</span><span class="sxs-lookup"><span data-stu-id="51719-113">GetCatchHandlerILOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-getcatchhandleriloffset-method.md)|<span data-ttu-id="51719-114">Consulte [método DefineCatchHandlerILOffset](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md).</span><span class="sxs-lookup"><span data-stu-id="51719-114">See [DefineCatchHandlerILOffset Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md).</span></span>|  
|[<span data-ttu-id="51719-115">Método GetKickoffMethod</span><span class="sxs-lookup"><span data-stu-id="51719-115">GetKickoffMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-getkickoffmethod-method.md)|<span data-ttu-id="51719-116">Consulte [método DefineKickoffMethod](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md).</span><span class="sxs-lookup"><span data-stu-id="51719-116">See [DefineKickoffMethod Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md).</span></span>|  
|[<span data-ttu-id="51719-117">Método HasCatchHandlerILOffset</span><span class="sxs-lookup"><span data-stu-id="51719-117">HasCatchHandlerILOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-hascatchhandleriloffset-method.md)|<span data-ttu-id="51719-118">Consulte [método DefineCatchHandlerILOffset](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md).</span><span class="sxs-lookup"><span data-stu-id="51719-118">See [DefineCatchHandlerILOffset Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md).</span></span>|  
|[<span data-ttu-id="51719-119">Método IsAsyncMethod</span><span class="sxs-lookup"><span data-stu-id="51719-119">IsAsyncMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-isasyncmethod-method.md)|<span data-ttu-id="51719-120">Verifica se o método tem informações assíncrono ou não.</span><span class="sxs-lookup"><span data-stu-id="51719-120">Checks if the method has async information or not.</span></span><br /><br /> <span data-ttu-id="51719-121">Se esse método retornar `FALSE` é inválido chamar outros métodos nessa interface.</span><span class="sxs-lookup"><span data-stu-id="51719-121">If this method returns `FALSE` then it is invalid to call any other methods in this interface.</span></span> <span data-ttu-id="51719-122">Eles serão retornar todos os `E_UNEXPECTED` nesse caso.</span><span class="sxs-lookup"><span data-stu-id="51719-122">They will all return `E_UNEXPECTED` in this case.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="51719-123">Requisitos</span><span class="sxs-lookup"><span data-stu-id="51719-123">Requirements</span></span>  
 <span data-ttu-id="51719-124">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="51719-124">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51719-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="51719-125">See Also</span></span>  
 [<span data-ttu-id="51719-126">Interfaces de armazenamento de símbolo de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="51719-126">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
