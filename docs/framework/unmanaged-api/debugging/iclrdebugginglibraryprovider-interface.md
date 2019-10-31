---
title: Interface ICLRDebuggingLibraryProvider
ms.date: 03/30/2017
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
ms.openlocfilehash: 81b9ffe5979ad553a5bdfbc27111469b2ff4db6f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73111370"
---
# <a name="iclrdebugginglibraryprovider-interface"></a><span data-ttu-id="e46c9-102">Interface ICLRDebuggingLibraryProvider</span><span class="sxs-lookup"><span data-stu-id="e46c9-102">ICLRDebuggingLibraryProvider Interface</span></span>
<span data-ttu-id="e46c9-103">Inclui o método de [método ProvideLibrary](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-providelibrary-method.md) , que obtém uma interface de retorno de chamada do provedor de biblioteca que permite que Common Language Runtime bibliotecas de depuração específicas à versão sejam localizadas e carregadas sob demanda.</span><span class="sxs-lookup"><span data-stu-id="e46c9-103">Includes the [ProvideLibrary Method](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-providelibrary-method.md) method, which gets a library provider callback interface that allows common language runtime version-specific debugging libraries to be located and loaded on demand.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e46c9-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="e46c9-104">Methods</span></span>  
  
|<span data-ttu-id="e46c9-105">Método</span><span class="sxs-lookup"><span data-stu-id="e46c9-105">Method</span></span>|<span data-ttu-id="e46c9-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="e46c9-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e46c9-107">Método ProvideLibrary</span><span class="sxs-lookup"><span data-stu-id="e46c9-107">ProvideLibrary Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-providelibrary-method.md)|<span data-ttu-id="e46c9-108">Permite que o depurador forneça um identificador para um módulo que pode ser usado para carregar uma biblioteca de depuração.</span><span class="sxs-lookup"><span data-stu-id="e46c9-108">Allows the debugger to provide a handle to a module which can be used to load a debug library.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e46c9-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e46c9-109">Requirements</span></span>  
 <span data-ttu-id="e46c9-110">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e46c9-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e46c9-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e46c9-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e46c9-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e46c9-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e46c9-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e46c9-113">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e46c9-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e46c9-114">See also</span></span>

- [<span data-ttu-id="e46c9-115">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="e46c9-115">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="e46c9-116">Depuração</span><span class="sxs-lookup"><span data-stu-id="e46c9-116">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
