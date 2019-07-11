---
title: Método ICorDebugILFrame::CanSetIP
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame.CanSetIP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame::CanSetIP
helpviewer_keywords:
- CanSetIP method, ICorDebugILFrame interface [.NET Framework debugging]
- ICorDebugILFrame::CanSetIP method [.NET Framework debugging]
ms.assetid: 16caf02f-c71e-486c-90b0-f0e54357d8f0
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 75b28dafae2861a2d33363f95a46bf1abf4cda35
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67756584"
---
# <a name="icordebugilframecansetip-method"></a>Método ICorDebugILFrame::CanSetIP
Obtém um HRESULT que indica se é seguro definir o ponteiro de instrução para o local de deslocamento especificado no código Microsoft Intermediate Language (MSIL).  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT CanSetIP (  
    [in] ULONG32   nOffset  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `nOffset`  
 [in] A configuração desejada para o ponteiro de instrução.  
  
## <a name="remarks"></a>Comentários  
 Use o `CanSetIP` método antes de chamar o [icordebugilframe:: SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md) método. Se `CanSetIP` retorna qualquer HRESULT que não seja S_OK, você ainda pode invocar `ICorDebugILFrame::SetIP`, mas não há nenhuma garantia de que o depurador continuará a execução de segura e correta do código que está sendo depurado.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug,h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
