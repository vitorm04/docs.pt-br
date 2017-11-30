---
title: Interface ICLRDebuggingLibraryProvider
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDebuggingLibraryProvider
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICLRDebuggingLibraryProvider
helpviewer_keywords: ICLRDebuggingLibraryProvider interface [.NET Framework debugging]
ms.assetid: 67739617-6add-41a9-9de5-a3200c3109ce
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 82ed352e3f5fb83a2f464f2d82ff9a9885227fe7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrdebugginglibraryprovider-interface"></a><span data-ttu-id="45270-102">Interface ICLRDebuggingLibraryProvider</span><span class="sxs-lookup"><span data-stu-id="45270-102">ICLRDebuggingLibraryProvider Interface</span></span>
<span data-ttu-id="45270-103">Inclui o [método ProvideLibrary](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-providelibrary-method.md) método, que obtém um provedor de biblioteca de interface de retorno de chamada que permite que o CLR bibliotecas de depuração específicos da versão em tempo de execução a ser localizada e carregada na demanda.</span><span class="sxs-lookup"><span data-stu-id="45270-103">Includes the [ProvideLibrary Method](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-providelibrary-method.md) method, which gets a library provider callback interface that allows common language runtime version-specific debugging libraries to be located and loaded on demand.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="45270-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="45270-104">Methods</span></span>  
  
|<span data-ttu-id="45270-105">Método</span><span class="sxs-lookup"><span data-stu-id="45270-105">Method</span></span>|<span data-ttu-id="45270-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="45270-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="45270-107">Método ProvideLibrary</span><span class="sxs-lookup"><span data-stu-id="45270-107">ProvideLibrary Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-providelibrary-method.md)|<span data-ttu-id="45270-108">Permite que o depurador fornecer um identificador para um módulo que pode ser usado para carregar uma biblioteca de depuração.</span><span class="sxs-lookup"><span data-stu-id="45270-108">Allows the debugger to provide a handle to a module which can be used to load a debug library.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="45270-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="45270-109">Requirements</span></span>  
 <span data-ttu-id="45270-110">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="45270-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="45270-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="45270-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="45270-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="45270-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="45270-113">**Versões do .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="45270-113">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45270-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="45270-114">See Also</span></span>  
 [<span data-ttu-id="45270-115">Interfaces de depuração</span><span class="sxs-lookup"><span data-stu-id="45270-115">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="45270-116">Depuração</span><span class="sxs-lookup"><span data-stu-id="45270-116">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
