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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c9d851a31cbbf429f49b9f369ce9bc03fa110b5b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54731979"
---
# <a name="iclrdebugginglibraryprovider-interface"></a><span data-ttu-id="73642-102">Interface ICLRDebuggingLibraryProvider</span><span class="sxs-lookup"><span data-stu-id="73642-102">ICLRDebuggingLibraryProvider Interface</span></span>
<span data-ttu-id="73642-103">Inclui o [método ProvideLibrary](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-providelibrary-method.md) método, que obtém um provedor de biblioteca de interface de retorno de chamada que permite que o common language runtime específica da versão bibliotecas de depuração ser localizada e carregada sob demanda.</span><span class="sxs-lookup"><span data-stu-id="73642-103">Includes the [ProvideLibrary Method](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-providelibrary-method.md) method, which gets a library provider callback interface that allows common language runtime version-specific debugging libraries to be located and loaded on demand.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="73642-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="73642-104">Methods</span></span>  
  
|<span data-ttu-id="73642-105">Método</span><span class="sxs-lookup"><span data-stu-id="73642-105">Method</span></span>|<span data-ttu-id="73642-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="73642-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="73642-107">Método ProvideLibrary</span><span class="sxs-lookup"><span data-stu-id="73642-107">ProvideLibrary Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-providelibrary-method.md)|<span data-ttu-id="73642-108">Permite que o depurador fornecer um identificador para um módulo que pode ser usado para carregar uma biblioteca de depuração.</span><span class="sxs-lookup"><span data-stu-id="73642-108">Allows the debugger to provide a handle to a module which can be used to load a debug library.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="73642-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="73642-109">Requirements</span></span>  
 <span data-ttu-id="73642-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="73642-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="73642-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="73642-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="73642-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="73642-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="73642-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="73642-113">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73642-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="73642-114">See also</span></span>
- [<span data-ttu-id="73642-115">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="73642-115">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="73642-116">Depuração</span><span class="sxs-lookup"><span data-stu-id="73642-116">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
