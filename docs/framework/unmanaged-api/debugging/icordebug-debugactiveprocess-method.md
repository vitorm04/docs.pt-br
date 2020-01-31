---
title: Método ICorDebug::DebugActiveProcess
ms.date: 03/30/2017
api_name:
- ICorDebug.DebugActiveProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug::DebugActiveProcess
helpviewer_keywords:
- DebugActiveProcess method [.NET Framework debugging]
- ICorDebug::DebugActiveProcess method [.NET Framework debugging]
ms.assetid: fdab0ade-7f56-4fa2-b3ef-f7a1d2852bba
topic_type:
- apiref
ms.openlocfilehash: 2d71cebb77ed3ca586e857710667c0077f4f76ed
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793580"
---
# <a name="icordebugdebugactiveprocess-method"></a>Método ICorDebug::DebugActiveProcess
Anexa o depurador a um processo existente.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT DebugActiveProcess (  
    [in]  DWORD               id,  
    [in]  BOOL                win32Attach,  
    [out] ICorDebugProcess    **ppProcess  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `id`  
 no A ID do processo ao qual o depurador deve ser anexado.  
  
 `win32Attach`  
 no Valor booliano definido como `true` se o depurador deve se comportar como o depurador Win32 para o processo e expedir os retornos de chamada não gerenciados; caso contrário, `false`.  
  
 `ppProcess`  
 fora Um ponteiro para o endereço de um objeto "ICorDebugProcess" que representa o processo ao qual o depurador foi anexado.  
  
## <a name="remarks"></a>Comentários  
 Não há suporte para depuração de interoperabilidade em plataformas Win9x e não x86, como plataformas baseadas em IA-64 e AMD64.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Interface ICorDebug](icordebug-interface.md)
