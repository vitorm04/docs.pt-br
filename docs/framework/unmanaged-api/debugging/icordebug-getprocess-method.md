---
title: Método ICorDebug::GetProcess
ms.date: 03/30/2017
api_name:
- ICorDebug.GetProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug::GetProcess
helpviewer_keywords:
- GetProcess method, ICorDebug interface [.NET Framework debugging]
- ICorDebug::GetProcess method [.NET Framework debugging]
ms.assetid: 10a40ba0-1b65-4721-bd11-cf12d57b280d
topic_type:
- apiref
ms.openlocfilehash: 2762d0680c5299732196cafe09f6e346e873f19a
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76785138"
---
# <a name="icordebuggetprocess-method"></a><span data-ttu-id="4f734-102">Método ICorDebug::GetProcess</span><span class="sxs-lookup"><span data-stu-id="4f734-102">ICorDebug::GetProcess Method</span></span>
<span data-ttu-id="4f734-103">Obtém um ponteiro para a instância "ICorDebugProcess" para o processo especificado.</span><span class="sxs-lookup"><span data-stu-id="4f734-103">Gets a pointer to the "ICorDebugProcess" instance for the specified process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4f734-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4f734-104">Syntax</span></span>  
  
```cpp  
HRESULT GetProcess (  
    [in] DWORD               dwProcessId,  
    [out] ICorDebugProcess   **ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4f734-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="4f734-105">Parameters</span></span>  
 `dwProcessId`  
 <span data-ttu-id="4f734-106">no A ID do processo.</span><span class="sxs-lookup"><span data-stu-id="4f734-106">[in] The ID of the process.</span></span>  
  
 `ppProcess`  
 <span data-ttu-id="4f734-107">fora Um ponteiro para o endereço de uma instância de `ICorDebugProcess` para o processo especificado.</span><span class="sxs-lookup"><span data-stu-id="4f734-107">[out] A pointer to the address of a `ICorDebugProcess` instance for the specified process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4f734-108">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="4f734-108">Requirements</span></span>  
 <span data-ttu-id="4f734-109">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4f734-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4f734-110">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4f734-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4f734-111">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4f734-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4f734-112">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4f734-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f734-113">Veja também</span><span class="sxs-lookup"><span data-stu-id="4f734-113">See also</span></span>

- [<span data-ttu-id="4f734-114">Interface ICorDebug</span><span class="sxs-lookup"><span data-stu-id="4f734-114">ICorDebug Interface</span></span>](icordebug-interface.md)
