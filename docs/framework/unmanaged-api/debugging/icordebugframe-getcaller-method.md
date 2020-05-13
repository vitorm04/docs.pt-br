---
title: Método ICorDebugFrame::GetCaller
ms.date: 03/30/2017
api_name:
- ICorDebugFrame.GetCaller
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrame::GetCaller
helpviewer_keywords:
- GetCaller method, ICorDebugFrame interface [.NET Framework debugging]
- ICorDebugFrame::GetCaller method [.NET Framework debugging]
ms.assetid: bfdc946b-8238-4eb9-8a85-884049fb0fd4
topic_type:
- apiref
ms.openlocfilehash: b29de0b70daa783197e78fe985d379d4124bc140
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83205141"
---
# <a name="icordebugframegetcaller-method"></a><span data-ttu-id="a969e-102">Método ICorDebugFrame::GetCaller</span><span class="sxs-lookup"><span data-stu-id="a969e-102">ICorDebugFrame::GetCaller Method</span></span>
<span data-ttu-id="a969e-103">Obtém um ponteiro para o objeto ICorDebugFrame na cadeia atual que chamou esse quadro.</span><span class="sxs-lookup"><span data-stu-id="a969e-103">Gets a pointer to the ICorDebugFrame object in the current chain that called this frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a969e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a969e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCaller (  
    [out] ICorDebugFrame     **ppFrame  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a969e-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a969e-105">Parameters</span></span>  
 `ppFrame`  
 <span data-ttu-id="a969e-106">fora Um ponteiro para o endereço de um `ICorDebugFrame` objeto que representa o quadro de chamada.</span><span class="sxs-lookup"><span data-stu-id="a969e-106">[out] A pointer to the address of an `ICorDebugFrame` object that represents the calling frame.</span></span> <span data-ttu-id="a969e-107">Esse valor será nulo se o quadro chamado for o quadro mais externo na cadeia atual.</span><span class="sxs-lookup"><span data-stu-id="a969e-107">This value is null if the called frame is the outermost frame in the current chain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a969e-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a969e-108">Requirements</span></span>  
 <span data-ttu-id="a969e-109">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a969e-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a969e-110">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a969e-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a969e-111">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a969e-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a969e-112">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a969e-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
