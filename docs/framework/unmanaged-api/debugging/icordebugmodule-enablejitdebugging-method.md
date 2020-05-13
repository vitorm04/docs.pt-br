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
ms.openlocfilehash: bdf027f94c8416d052cb807d04be76a39868ccf7
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212926"
---
# <a name="icordebugmoduleenablejitdebugging-method"></a><span data-ttu-id="cccbc-102">Método ICorDebugModule::EnableJITDebugging</span><span class="sxs-lookup"><span data-stu-id="cccbc-102">ICorDebugModule::EnableJITDebugging Method</span></span>
<span data-ttu-id="cccbc-103">Controla se o compilador JIT (just-in-time) preserva informações de depuração para métodos dentro deste módulo.</span><span class="sxs-lookup"><span data-stu-id="cccbc-103">Controls whether the just-in-time (JIT) compiler preserves debugging information for methods within this module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cccbc-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cccbc-104">Syntax</span></span>  
  
```cpp  
HRESULT EnableJITDebugging(  
    [in] BOOL bTrackJITInfo,  
    [in] BOOL bAllowJitOpts  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cccbc-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="cccbc-105">Parameters</span></span>  
 `bTrackJITInfo`  
 <span data-ttu-id="cccbc-106">no Defina esse valor como `true` para habilitar o compilador JIT para preservar informações de mapeamento entre a versão do Microsoft Intermediate Language (MSIL) e a versão compilada em JIT de cada método neste módulo.</span><span class="sxs-lookup"><span data-stu-id="cccbc-106">[in] Set this value to `true` to enable the JIT compiler to preserve mapping information between the Microsoft intermediate language (MSIL) version and the JIT-compiled version of each method in this module.</span></span>  
  
 `bAllowJitOpts`  
 <span data-ttu-id="cccbc-107">no Defina esse valor como `true` para habilitar o compilador JIT para gerar código com determinadas otimizações específicas de JIT para depuração.</span><span class="sxs-lookup"><span data-stu-id="cccbc-107">[in] Set this value to `true` to enable the JIT compiler to generate code with certain JIT-specific optimizations for debugging.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cccbc-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="cccbc-108">Remarks</span></span>  
 <span data-ttu-id="cccbc-109">A depuração JIT é habilitada por padrão para todos os módulos que são carregados quando o depurador está ativo.</span><span class="sxs-lookup"><span data-stu-id="cccbc-109">JIT debugging is enabled by default for all modules that are loaded when the debugger is active.</span></span> <span data-ttu-id="cccbc-110">Habilitar ou desabilitar programaticamente as configurações substitui as configurações globais.</span><span class="sxs-lookup"><span data-stu-id="cccbc-110">Programmatically enabling or disabling the settings overrides global settings.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cccbc-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="cccbc-111">Requirements</span></span>  
 <span data-ttu-id="cccbc-112">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cccbc-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cccbc-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cccbc-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cccbc-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cccbc-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cccbc-115">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cccbc-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
