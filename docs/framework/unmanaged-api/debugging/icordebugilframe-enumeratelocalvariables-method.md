---
title: Método ICorDebugILFrame::EnumerateLocalVariables
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame.EnumerateLocalVariables
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame::EnumerateLocalVariables
helpviewer_keywords:
- EnumerateLocalVariables method [.NET Framework debugging]
- ICorDebugILFrame::EnumerateLocalVariables method [.NET Framework debugging]
ms.assetid: 1a67fa1b-2419-4cd0-aad4-6f46a0719b4b
topic_type:
- apiref
ms.openlocfilehash: c071a7ddb7d8d3f0e6487ab85284c45f9a7f0372
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178840"
---
# <a name="icordebugilframeenumeratelocalvariables-method"></a>Método ICorDebugILFrame::EnumerateLocalVariables
Obtém um enumerador para as variáveis locais neste quadro.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT EnumerateLocalVariables(
    [out] ICorDebugValueEnum    **ppValueEnum  
);  
```  
  
## <a name="parameters"></a>parâmetros  
 `ppValueEnum`  
 [out] Um ponteiro para o endereço de um objeto ICorDebugValueEnum que é o enumerador das variáveis locais neste quadro.  
  
## <a name="remarks"></a>Comentários  
 `EnumerateLocalVariables`obtém um enumerador que pode listar as variáveis locais disponíveis no quadro de chamadas que é representado por este objeto ICorDebugILFrame. A lista pode não incluir todas as variáveis locais na função em execução, porque algumas delas podem não estar ativas.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
