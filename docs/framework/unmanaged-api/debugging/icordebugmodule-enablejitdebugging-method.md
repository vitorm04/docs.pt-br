---
title: Método ICorDebugModule::EnableJITDebugging
ms.date: 03/30/2017
api_name:
- ICorDebugModule.EnableJITDebugging
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::EnableJITDebugging
helpviewer_keywords:
- ICorDebugModule::EnableJITDebugging method [.NET Framework debugging]
- EnableJITDebugging method [.NET Framework debugging]
ms.assetid: 0a65e2a4-5bb6-496c-ae6f-40474426b5a6
topic_type:
- apiref
ms.openlocfilehash: da532ee1b5909a68bedbb9e6f6c96333e88002a8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73109720"
---
# <a name="icordebugmoduleenablejitdebugging-method"></a><span data-ttu-id="968ac-102">Método ICorDebugModule::EnableJITDebugging</span><span class="sxs-lookup"><span data-stu-id="968ac-102">ICorDebugModule::EnableJITDebugging Method</span></span>
<span data-ttu-id="968ac-103">Controla se o compilador JIT (just-in-time) preserva informações de depuração para métodos dentro deste módulo.</span><span class="sxs-lookup"><span data-stu-id="968ac-103">Controls whether the just-in-time (JIT) compiler preserves debugging information for methods within this module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="968ac-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="968ac-104">Syntax</span></span>  
  
```cpp  
HRESULT EnableJITDebugging(  
    [in] BOOL bTrackJITInfo,  
    [in] BOOL bAllowJitOpts  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="968ac-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="968ac-105">Parameters</span></span>  
 `bTrackJITInfo`  
 <span data-ttu-id="968ac-106">no Defina esse valor como `true` para permitir que o compilador JIT preserve informações de mapeamento entre a versão da Microsoft Intermediate Language (MSIL) e a versão compilada em JIT de cada método neste módulo.</span><span class="sxs-lookup"><span data-stu-id="968ac-106">[in] Set this value to `true` to enable the JIT compiler to preserve mapping information between the Microsoft intermediate language (MSIL) version and the JIT-compiled version of each method in this module.</span></span>  
  
 `bAllowJitOpts`  
 <span data-ttu-id="968ac-107">no Defina esse valor como `true` para permitir que o compilador JIT gere código com determinadas otimizações específicas de JIT para depuração.</span><span class="sxs-lookup"><span data-stu-id="968ac-107">[in] Set this value to `true` to enable the JIT compiler to generate code with certain JIT-specific optimizations for debugging.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="968ac-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="968ac-108">Remarks</span></span>  
 <span data-ttu-id="968ac-109">A depuração JIT é habilitada por padrão para todos os módulos que são carregados quando o depurador está ativo.</span><span class="sxs-lookup"><span data-stu-id="968ac-109">JIT debugging is enabled by default for all modules that are loaded when the debugger is active.</span></span> <span data-ttu-id="968ac-110">Habilitar ou desabilitar programaticamente as configurações substitui as configurações globais.</span><span class="sxs-lookup"><span data-stu-id="968ac-110">Programmatically enabling or disabling the settings overrides global settings.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="968ac-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="968ac-111">Requirements</span></span>  
 <span data-ttu-id="968ac-112">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="968ac-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="968ac-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="968ac-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="968ac-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="968ac-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="968ac-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="968ac-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
