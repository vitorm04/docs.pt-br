---
title: "Método ICorDebugModule::EnableJITDebugging"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugModule.EnableJITDebugging
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugModule::EnableJITDebugging
helpviewer_keywords:
- ICorDebugModule::EnableJITDebugging method [.NET Framework debugging]
- EnableJITDebugging method [.NET Framework debugging]
ms.assetid: 0a65e2a4-5bb6-496c-ae6f-40474426b5a6
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 31fc3b7c2b977dbfd6f10cc767f81748243dfce4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugmoduleenablejitdebugging-method"></a><span data-ttu-id="99d19-102">Método ICorDebugModule::EnableJITDebugging</span><span class="sxs-lookup"><span data-stu-id="99d19-102">ICorDebugModule::EnableJITDebugging Method</span></span>
<span data-ttu-id="99d19-103">Controla se o compilador just-in-time (JIT) preserva as informações de depuração para métodos neste módulo.</span><span class="sxs-lookup"><span data-stu-id="99d19-103">Controls whether the just-in-time (JIT) compiler preserves debugging information for methods within this module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="99d19-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="99d19-104">Syntax</span></span>  
  
```  
HRESULT EnableJITDebugging(  
    [in] BOOL bTrackJITInfo,  
    [in] BOOL bAllowJitOpts  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="99d19-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="99d19-105">Parameters</span></span>  
 `bTrackJITInfo`  
 <span data-ttu-id="99d19-106">[in] Defina esse valor como `true` para habilitar o compilador JIT preservar as informações de mapeamento entre a versão do Microsoft intermediate language (MSIL) e a versão da compilação JIT de cada método neste módulo.</span><span class="sxs-lookup"><span data-stu-id="99d19-106">[in] Set this value to `true` to enable the JIT compiler to preserve mapping information between the Microsoft intermediate language (MSIL) version and the JIT-compiled version of each method in this module.</span></span>  
  
 `bAllowJitOpts`  
 <span data-ttu-id="99d19-107">[in] Defina esse valor como `true` para habilitar o compilador JIT gerar o código com certas otimizações JIT específicos para depuração.</span><span class="sxs-lookup"><span data-stu-id="99d19-107">[in] Set this value to `true` to enable the JIT compiler to generate code with certain JIT-specific optimizations for debugging.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="99d19-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="99d19-108">Remarks</span></span>  
 <span data-ttu-id="99d19-109">A depuração JIT está habilitada por padrão para todos os módulos que são carregados quando o depurador está ativo.</span><span class="sxs-lookup"><span data-stu-id="99d19-109">JIT debugging is enabled by default for all modules that are loaded when the debugger is active.</span></span> <span data-ttu-id="99d19-110">Habilitar ou desabilitar as configurações de programaticamente substitui configurações globais.</span><span class="sxs-lookup"><span data-stu-id="99d19-110">Programmatically enabling or disabling the settings overrides global settings.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="99d19-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="99d19-111">Requirements</span></span>  
 <span data-ttu-id="99d19-112">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="99d19-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="99d19-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="99d19-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="99d19-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="99d19-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="99d19-115">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="99d19-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
