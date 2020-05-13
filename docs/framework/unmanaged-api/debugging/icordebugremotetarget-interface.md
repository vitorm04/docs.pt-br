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
ms.openlocfilehash: 4883c208468db0096bed3ff8cf4a8ed50a5d7cc6
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379225"
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
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método ICorDebugRemoteTarget::GetHostName](icordebugremotetarget-gethostname-method.md)|Retorna o nome do host ou o endereço IP de um computador remoto.|  
  
## <a name="remarks"></a>Comentários  
 A depuração de modo misto (ou seja, código gerenciado e nativo) não tem suporte no Windows 95, Windows 98 ou Windows ME, ou em plataformas não x86 (como IA-64 e AMD64).  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug. idl  
  
 **Biblioteca:** : CorGuids. lib  
  
 **Versões do .NET Framework:** 3,5 SP1  
  
## <a name="see-also"></a>Confira também

- [Interface ICorDebugRemote](icordebugremote-interface.md)
- [Interface ICorDebug](icordebug-interface.md)
- [Depurando interfaces](debugging-interfaces.md)
