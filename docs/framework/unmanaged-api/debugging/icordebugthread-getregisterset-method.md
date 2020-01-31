---
title: Método ICorDebugThread::GetRegisterSet
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetRegisterSet
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetRegisterSet
helpviewer_keywords:
- ICorDebugThread::GetRegisterSet method [.NET Framework debugging]
- GetRegisterSet method, ICorDebugThread interface [.NET Framework debugging]
ms.assetid: 3b9b6260-98ac-4cfd-88e5-5d7614f94a0c
topic_type:
- apiref
ms.openlocfilehash: 9793424e79ed878b04a5c51daad08b5d12d439e1
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791463"
---
# <a name="icordebugthreadgetregisterset-method"></a><span data-ttu-id="72676-102">Método ICorDebugThread::GetRegisterSet</span><span class="sxs-lookup"><span data-stu-id="72676-102">ICorDebugThread::GetRegisterSet Method</span></span>
<span data-ttu-id="72676-103">Obtém um ponteiro de interface para o conjunto de registros que está associado à parte ativa deste objeto ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="72676-103">Gets an interface pointer to the register set that is associated with the active part of this ICorDebugThread object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72676-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="72676-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRegisterSet (  
    [out] ICorDebugRegisterSet **ppRegisters  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="72676-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="72676-105">Parameters</span></span>  
 `ppRegisters`  
 <span data-ttu-id="72676-106">fora Um ponteiro para o endereço de um objeto de interface [ICorDebugRegisterSet](icordebugregisterset-interface.md) que representa o conjunto de registros para a parte ativa desse thread.</span><span class="sxs-lookup"><span data-stu-id="72676-106">[out] A pointer to the address of an [ICorDebugRegisterSet](icordebugregisterset-interface.md) interface object that represents the register set for the active part of this thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="72676-107">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="72676-107">Requirements</span></span>  
 <span data-ttu-id="72676-108">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="72676-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="72676-109">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="72676-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="72676-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="72676-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="72676-111">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="72676-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
