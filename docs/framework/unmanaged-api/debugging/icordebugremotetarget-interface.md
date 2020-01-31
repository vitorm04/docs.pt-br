---
title: Interface ICorDebugRemoteTarget
ms.date: 03/30/2017
api_name:
- ICorDebugRemoteTarget
api_location:
- CorDebug.dll
api_type:
- COM
f1_keywords:
- ICorDebugRemoteTarget
helpviewer_keywords:
- ICorDebugRemoteTarget interface [.NET Framework debugging]
ms.assetid: bd9936a6-cc24-4869-8761-0988664464e6
topic_type:
- apiref
ms.openlocfilehash: bab6b7f683b5563cf362366dfb007f83caeee12d
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791931"
---
# <a name="icordebugremotetarget-interface"></a>Interface ICorDebugRemoteTarget
Fornece métodos que permitem aos desenvolvedores depurar aplicativos baseados no Silverlight no ambiente Common Language Runtime (CLR).  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
interface ICorDebugRemoteTarget  : IUnknown  
{  
    HRESULT GetHostName (  
        [in]  ULONG32                    cchHostName,  
        [out] ULONG32*                   pcchHostName,  
        [out, size_is(cchHostName),  
              length_is(*pcchHostName)]  
                  WCHAR szHostName[]  
        );  
};  
```  
  
## <a name="methods"></a>{1&gt;Métodos&lt;1}  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método ICorDebugRemoteTarget::GetHostName](icordebugremotetarget-gethostname-method.md)|Retorna o nome do host ou o endereço IP de um computador remoto.|  
  
## <a name="remarks"></a>Comentários  
 A depuração de modo misto (ou seja, código gerenciado e nativo) não tem suporte no Windows 95, Windows 98 ou Windows ME, ou em plataformas não x86 (como IA-64 e AMD64).  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug. idl  
  
 **Biblioteca:** : CorGuids. lib  
  
 **Versões do .NET Framework:** 3,5 SP1  
  
## <a name="see-also"></a>Veja também

- [Interface ICorDebugRemote](icordebugremote-interface.md)
- [Interface ICorDebug](icordebug-interface.md)
- [Depurando interfaces](debugging-interfaces.md)
