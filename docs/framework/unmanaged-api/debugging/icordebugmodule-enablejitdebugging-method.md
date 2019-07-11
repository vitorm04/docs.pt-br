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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8aeb6ed448539db2720fee0d42cfcc344fd3bbf7
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67762767"
---
# <a name="icordebugmoduleenablejitdebugging-method"></a><span data-ttu-id="c21a2-102">Método ICorDebugModule::EnableJITDebugging</span><span class="sxs-lookup"><span data-stu-id="c21a2-102">ICorDebugModule::EnableJITDebugging Method</span></span>
<span data-ttu-id="c21a2-103">Controla se o compilador just-in-time (JIT) preserva informações de depuração para métodos neste módulo.</span><span class="sxs-lookup"><span data-stu-id="c21a2-103">Controls whether the just-in-time (JIT) compiler preserves debugging information for methods within this module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c21a2-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c21a2-104">Syntax</span></span>  
  
```cpp  
HRESULT EnableJITDebugging(  
    [in] BOOL bTrackJITInfo,  
    [in] BOOL bAllowJitOpts  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c21a2-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c21a2-105">Parameters</span></span>  
 `bTrackJITInfo`  
 <span data-ttu-id="c21a2-106">[in] Defina esse valor como `true` para habilitar o compilador JIT preservar as informações de mapeamento entre a versão do Microsoft intermediate language (MSIL) e a versão de cada método neste módulo compilado por JIT.</span><span class="sxs-lookup"><span data-stu-id="c21a2-106">[in] Set this value to `true` to enable the JIT compiler to preserve mapping information between the Microsoft intermediate language (MSIL) version and the JIT-compiled version of each method in this module.</span></span>  
  
 `bAllowJitOpts`  
 <span data-ttu-id="c21a2-107">[in] Defina esse valor como `true` para habilitar o compilador JIT gerar código com determinadas otimizações JIT específicas para a depuração.</span><span class="sxs-lookup"><span data-stu-id="c21a2-107">[in] Set this value to `true` to enable the JIT compiler to generate code with certain JIT-specific optimizations for debugging.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c21a2-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="c21a2-108">Remarks</span></span>  
 <span data-ttu-id="c21a2-109">Depuração JIT é habilitada por padrão para todos os módulos que são carregados quando o depurador está ativo.</span><span class="sxs-lookup"><span data-stu-id="c21a2-109">JIT debugging is enabled by default for all modules that are loaded when the debugger is active.</span></span> <span data-ttu-id="c21a2-110">Programaticamente habilitando ou desabilitando as configurações de substituições de configurações globais.</span><span class="sxs-lookup"><span data-stu-id="c21a2-110">Programmatically enabling or disabling the settings overrides global settings.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c21a2-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c21a2-111">Requirements</span></span>  
 <span data-ttu-id="c21a2-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c21a2-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c21a2-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c21a2-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c21a2-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c21a2-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c21a2-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c21a2-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
