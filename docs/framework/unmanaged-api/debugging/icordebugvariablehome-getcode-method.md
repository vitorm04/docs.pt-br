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
ms.openlocfilehash: 87d611a7b6e12a9238b00131326e8205778769e6
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396600"
---
# <a name="icordebugvariablehomegetcode-method"></a><span data-ttu-id="d47b9-102">Método ICorDebugVariableHome:: GetCode</span><span class="sxs-lookup"><span data-stu-id="d47b9-102">ICorDebugVariableHome::GetCode Method</span></span>
<span data-ttu-id="d47b9-103">Obtém a instância "ICorDebugCode" que contém este objeto [ICorDebugVariableHome](icordebugvariablehome-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="d47b9-103">Gets the "ICorDebugCode" instance that contains this [ICorDebugVariableHome](icordebugvariablehome-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d47b9-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d47b9-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCode(  
    [out] ICorDebugCode **ppCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d47b9-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d47b9-105">Parameters</span></span>  
 `ppCode`  
 <span data-ttu-id="d47b9-106">fora Um ponteiro para o endereço da instância "ICorDebugCode" que contém este objeto [ICorDebugVariableHome](icordebugvariablehome-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="d47b9-106">[out] A pointer to the address of the "ICorDebugCode" instance that contains this [ICorDebugVariableHome](icordebugvariablehome-interface.md) object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d47b9-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d47b9-107">Requirements</span></span>  
 <span data-ttu-id="d47b9-108">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d47b9-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d47b9-109">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d47b9-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d47b9-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d47b9-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d47b9-111">**.NET Framework versões:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d47b9-111">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d47b9-112">Veja também</span><span class="sxs-lookup"><span data-stu-id="d47b9-112">See also</span></span>

- [<span data-ttu-id="d47b9-113">Interface ICorDebugVariableHome</span><span class="sxs-lookup"><span data-stu-id="d47b9-113">ICorDebugVariableHome Interface</span></span>](icordebugvariablehome-interface.md)
