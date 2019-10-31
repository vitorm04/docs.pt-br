---
title: 'Método ICorDebugVariableHome:: GetCode'
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHome.GetCode
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHome::GetCode
helpviewer_keywords:
- ICorDebugVariableHome::GetCode method [.NET Framework debugging]
- GetCode method, ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: ef002890-4a7b-4a5d-abbf-16c60083f794
topic_type:
- apiref
ms.openlocfilehash: 4770eb3e93104dd3862eb2163faf1dc7fe9008ba
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125131"
---
# <a name="icordebugvariablehomegetcode-method"></a><span data-ttu-id="de989-102">Método ICorDebugVariableHome:: GetCode</span><span class="sxs-lookup"><span data-stu-id="de989-102">ICorDebugVariableHome::GetCode Method</span></span>
<span data-ttu-id="de989-103">Obtém a instância "ICorDebugCode" que contém este objeto [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="de989-103">Gets the "ICorDebugCode" instance that contains this [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de989-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="de989-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCode(  
    [out] ICorDebugCode **ppCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="de989-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="de989-105">Parameters</span></span>  
 `ppCode`  
 <span data-ttu-id="de989-106">fora Um ponteiro para o endereço da instância "ICorDebugCode" que contém este objeto [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="de989-106">[out] A pointer to the address of the "ICorDebugCode" instance that contains this [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="de989-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="de989-107">Requirements</span></span>  
 <span data-ttu-id="de989-108">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="de989-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="de989-109">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="de989-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="de989-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="de989-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="de989-111">**Versões do .NET Framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="de989-111">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de989-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="de989-112">See also</span></span>

- [<span data-ttu-id="de989-113">Interface ICorDebugVariableHome</span><span class="sxs-lookup"><span data-stu-id="de989-113">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
