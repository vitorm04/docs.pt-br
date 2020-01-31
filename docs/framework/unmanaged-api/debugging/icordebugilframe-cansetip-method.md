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
ms.openlocfilehash: c6a02b080739d00667893008be4a19b4fa9a6ef2
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788588"
---
# <a name="icordebugilframecansetip-method"></a>Método ICorDebugILFrame::CanSetIP
Obtém um HRESULT que indica se é seguro definir o ponteiro de instrução para o local de deslocamento especificado no código MSIL (Microsoft Intermediate Language).  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT CanSetIP (  
    [in] ULONG32   nOffset  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `nOffset`  
 no A configuração desejada para o ponteiro de instrução.  
  
## <a name="remarks"></a>Comentários  
 Use o método `CanSetIP` antes de chamar o método [ICorDebugILFrame:: SetIP](icordebugilframe-setip-method.md) . Se `CanSetIP` retornar qualquer HRESULT diferente de S_OK, você ainda poderá invocar `ICorDebugILFrame::SetIP`, mas não haverá nenhuma garantia de que o depurador continuará a execução segura e correta do código que está sendo depurado.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug. idl, CorDebug, h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
