---
title: Interface ICLRDebugging
ms.date: 03/30/2017
api_name:
- ICLRDebugging
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDebugging
helpviewer_keywords:
- ICLRDebugging interface [.NET Framework debugging]
ms.assetid: 429d8fce-b1b1-49d7-895c-28c1c1aa2dbd
topic_type:
- apiref
ms.openlocfilehash: 9a768535c3bf69b5127777de4cee27054943091d
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793637"
---
# <a name="iclrdebugging-interface"></a>Interface ICLRDebugging
Fornece métodos que manipulam os módulos de carregamento e descarregamento para depuração.  
  
## <a name="methods"></a>{1&gt;Métodos&lt;1}  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método OpenVirtualProcess](iclrdebugging-openvirtualprocess-method.md)|Obtém a interface "ICorDebugProcess" que corresponde a um módulo Common Language Runtime (CLR) carregado no processo.|  
|[Método CanUnloadNow](iclrdebugging-canunloadnow-method.md)|Determina se uma biblioteca fornecida por uma interface [ICLRDebuggingLibraryProvider](iclrdebugginglibraryprovider-interface.md) ainda está em uso ou pode ser descarregada.|  
  
## <a name="remarks"></a>Comentários  
 Você pode obter uma instância da interface `ICLRDebugging` usando a função [CLRCreateInstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md) .  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Depurando interfaces](debugging-interfaces.md)
- [Depuração](index.md)
