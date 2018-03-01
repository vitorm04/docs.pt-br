---
title: Interface ICLRDebuggingLibraryProvider
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
- ICLRDebuggingLibraryProvider
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDebuggingLibraryProvider
helpviewer_keywords:
- ICLRDebuggingLibraryProvider interface [.NET Framework debugging]
ms.assetid: 67739617-6add-41a9-9de5-a3200c3109ce
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a7320bf261f28fed85c44f2550df5ecd06421290
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrdebugginglibraryprovider-interface"></a><span data-ttu-id="99524-102">Interface ICLRDebuggingLibraryProvider</span><span class="sxs-lookup"><span data-stu-id="99524-102">ICLRDebuggingLibraryProvider Interface</span></span>
<span data-ttu-id="99524-103">Inclui o [método ProvideLibrary](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-providelibrary-method.md) método, que obtém um provedor de biblioteca de interface de retorno de chamada que permite que o CLR bibliotecas de depuração específicos da versão em tempo de execução a ser localizada e carregada na demanda.</span><span class="sxs-lookup"><span data-stu-id="99524-103">Includes the [ProvideLibrary Method](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-providelibrary-method.md) method, which gets a library provider callback interface that allows common language runtime version-specific debugging libraries to be located and loaded on demand.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="99524-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="99524-104">Methods</span></span>  
  
|<span data-ttu-id="99524-105">Método</span><span class="sxs-lookup"><span data-stu-id="99524-105">Method</span></span>|<span data-ttu-id="99524-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="99524-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="99524-107">Método ProvideLibrary</span><span class="sxs-lookup"><span data-stu-id="99524-107">ProvideLibrary Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-providelibrary-method.md)|<span data-ttu-id="99524-108">Permite que o depurador fornecer um identificador para um módulo que pode ser usado para carregar uma biblioteca de depuração.</span><span class="sxs-lookup"><span data-stu-id="99524-108">Allows the debugger to provide a handle to a module which can be used to load a debug library.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="99524-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="99524-109">Requirements</span></span>  
 <span data-ttu-id="99524-110">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="99524-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="99524-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="99524-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="99524-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="99524-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="99524-113">**Versões do .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="99524-113">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99524-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="99524-114">See Also</span></span>  
 [<span data-ttu-id="99524-115">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="99524-115">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="99524-116">Depuração</span><span class="sxs-lookup"><span data-stu-id="99524-116">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
