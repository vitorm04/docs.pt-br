---
title: Método ICorDebugManagedCallback::UpdateModuleSymbols
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.UpdateModuleSymbols
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::UpdateModuleSymbols
helpviewer_keywords:
- UpdateModuleSymbols method [.NET Framework debugging]
- ICorDebugManagedCallback::UpdateModuleSymbols method [.NET Framework debugging]
ms.assetid: 0863f644-58e8-45a0-b0c3-a28e99b20938
topic_type:
- apiref
ms.openlocfilehash: 2b64122489481c6b0fde605015720d0a56ba8fe2
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788318"
---
# <a name="icordebugmanagedcallbackupdatemodulesymbols-method"></a><span data-ttu-id="0d278-102">Método ICorDebugManagedCallback::UpdateModuleSymbols</span><span class="sxs-lookup"><span data-stu-id="0d278-102">ICorDebugManagedCallback::UpdateModuleSymbols Method</span></span>
<span data-ttu-id="0d278-103">Notifica o depurador de que os símbolos de um módulo Common Language Runtime foram alterados.</span><span class="sxs-lookup"><span data-stu-id="0d278-103">Notifies the debugger that the symbols for a common language runtime module have changed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d278-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0d278-104">Syntax</span></span>  
  
```cpp  
HRESULT UpdateModuleSymbols (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugModule    *pModule,  
    [in] IStream            *pSymbolStream  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0d278-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0d278-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="0d278-106">no Um ponteiro para um objeto ICorDebugAppDomain que representa o domínio do aplicativo que contém o módulo no qual os símbolos foram alterados.</span><span class="sxs-lookup"><span data-stu-id="0d278-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the module in which the symbols have changed.</span></span>  
  
 `pModule`  
 <span data-ttu-id="0d278-107">no Um ponteiro para um objeto ICorDebugModule que representa o módulo no qual os símbolos foram alterados.</span><span class="sxs-lookup"><span data-stu-id="0d278-107">[in] A pointer to an ICorDebugModule object that represents the module in which the symbols have changed.</span></span>  
  
 `pSymbolStream`  
 <span data-ttu-id="0d278-108">no Um ponteiro para um objeto de `IStream` COM do Win32 que contém os símbolos modificados.</span><span class="sxs-lookup"><span data-stu-id="0d278-108">[in] A pointer to a Win32 COM `IStream` object that contains the modified symbols.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0d278-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="0d278-109">Remarks</span></span>  
 <span data-ttu-id="0d278-110">Esse método fornece uma oportunidade de atualizar a exibição do depurador dos símbolos de um módulo chamando [ISymUnmanagedReader:: UpdateSymbolStore](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-updatesymbolstore-method.md) ou [ISymUnmanagedReader:: ReplaceSymbolStore](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-replacesymbolstore-method.md).</span><span class="sxs-lookup"><span data-stu-id="0d278-110">This method provides an opportunity to update the debugger's view of a module's symbols by calling [ISymUnmanagedReader::UpdateSymbolStore](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-updatesymbolstore-method.md) or [ISymUnmanagedReader::ReplaceSymbolStore](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-replacesymbolstore-method.md).</span></span>  
  
 <span data-ttu-id="0d278-111">Esse retorno de chamada pode ocorrer várias vezes para o mesmo módulo.</span><span class="sxs-lookup"><span data-stu-id="0d278-111">This callback can occur multiple times for the same module.</span></span>  
  
 <span data-ttu-id="0d278-112">Um depurador deve tentar associar pontos de interrupção de nível de origem não associados.</span><span class="sxs-lookup"><span data-stu-id="0d278-112">A debugger should try to bind unbound source-level breakpoints.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0d278-113">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="0d278-113">Requirements</span></span>  
 <span data-ttu-id="0d278-114">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0d278-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0d278-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0d278-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0d278-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0d278-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0d278-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0d278-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d278-118">Veja também</span><span class="sxs-lookup"><span data-stu-id="0d278-118">See also</span></span>

- [<span data-ttu-id="0d278-119">Interface ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="0d278-119">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
