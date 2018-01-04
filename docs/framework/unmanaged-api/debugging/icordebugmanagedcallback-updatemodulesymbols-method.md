---
title: "Método ICorDebugManagedCallback::UpdateModuleSymbols"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugManagedCallback.UpdateModuleSymbols
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugManagedCallback::UpdateModuleSymbols
helpviewer_keywords:
- UpdateModuleSymbols method [.NET Framework debugging]
- ICorDebugManagedCallback::UpdateModuleSymbols method [.NET Framework debugging]
ms.assetid: 0863f644-58e8-45a0-b0c3-a28e99b20938
topic_type: apiref
caps.latest.revision: "17"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ad5a84268f3810a1fb73a21a6bd8106e82ccbd78
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmanagedcallbackupdatemodulesymbols-method"></a><span data-ttu-id="df446-102">Método ICorDebugManagedCallback::UpdateModuleSymbols</span><span class="sxs-lookup"><span data-stu-id="df446-102">ICorDebugManagedCallback::UpdateModuleSymbols Method</span></span>
<span data-ttu-id="df446-103">Notifica o depurador que alterou os símbolos para um módulo de tempo de execução de linguagem comum.</span><span class="sxs-lookup"><span data-stu-id="df446-103">Notifies the debugger that the symbols for a common language runtime module have changed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="df446-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="df446-104">Syntax</span></span>  
  
```  
HRESULT UpdateModuleSymbols (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugModule    *pModule,  
    [in] IStream            *pSymbolStream  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="df446-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="df446-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="df446-106">[in] Um ponteiro para um objeto ICorDebugAppDomain que representa o domínio de aplicativo que contém o módulo no qual os símbolos foram alterados.</span><span class="sxs-lookup"><span data-stu-id="df446-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the module in which the symbols have changed.</span></span>  
  
 `pModule`  
 <span data-ttu-id="df446-107">[in] Um ponteiro para um objeto ICorDebugModule que representa o módulo no qual os símbolos foram alterados.</span><span class="sxs-lookup"><span data-stu-id="df446-107">[in] A pointer to an ICorDebugModule object that represents the module in which the symbols have changed.</span></span>  
  
 `pSymbolStream`  
 <span data-ttu-id="df446-108">[in] Um ponteiro para um COM Win32 `IStream` objeto que contém os símbolos modificados.</span><span class="sxs-lookup"><span data-stu-id="df446-108">[in] A pointer to a Win32 COM `IStream` object that contains the modified symbols.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="df446-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="df446-109">Remarks</span></span>  
 <span data-ttu-id="df446-110">Esse método fornece uma oportunidade para atualizar a exibição do depurador de símbolos do módulo chamando [Isymunmanagedreader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-updatesymbolstore-method.md) ou [: Replacesymbolstore](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-replacesymbolstore-method.md).</span><span class="sxs-lookup"><span data-stu-id="df446-110">This method provides an opportunity to update the debugger's view of a module's symbols by calling [ISymUnmanagedReader::UpdateSymbolStore](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-updatesymbolstore-method.md) or [ISymUnmanagedReader::ReplaceSymbolStore](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-replacesymbolstore-method.md).</span></span>  
  
 <span data-ttu-id="df446-111">Esse retorno de chamada pode ocorrer várias vezes para o mesmo módulo.</span><span class="sxs-lookup"><span data-stu-id="df446-111">This callback can occur multiple times for the same module.</span></span>  
  
 <span data-ttu-id="df446-112">Um depurador deve tentar associar os pontos de interrupção de nível de origem não associados.</span><span class="sxs-lookup"><span data-stu-id="df446-112">A debugger should try to bind unbound source-level breakpoints.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="df446-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="df446-113">Requirements</span></span>  
 <span data-ttu-id="df446-114">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="df446-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="df446-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="df446-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="df446-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="df446-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="df446-117">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="df446-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df446-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="df446-118">See Also</span></span>  
 [<span data-ttu-id="df446-119">Interface ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="df446-119">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
