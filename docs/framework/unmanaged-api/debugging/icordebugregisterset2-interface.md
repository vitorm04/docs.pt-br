---
title: Interface ICorDebugRegisterSet2
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet2
helpviewer_keywords:
- ICorDebugRegisterSet2 interface [.NET Framework debugging]
ms.assetid: d7fbccbf-3b6b-4db8-a96d-768e1cb6b1a6
topic_type:
- apiref
ms.openlocfilehash: f989f1c1f29c63af54ff125f4ad1aaa2bcee6757
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378208"
---
# <a name="icordebugregisterset2-interface"></a>Interface ICorDebugRegisterSet2
Estende os recursos da interface [ICorDebugRegisterSet](icordebugregisterset-interface.md) para plataformas de hardware que têm mais de 64 registros.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método GetRegisters](icordebugregisterset2-getregisters-method.md)|Obtém o valor de cada registro (no computador que está executando o código) que é especificado pela máscara de bits.|  
|[Método GetRegistersAvailable](icordebugregisterset2-getregistersavailable-method.md)|Obtém uma matriz de bytes que fornece um bitmap dos registros disponíveis.|  
|[Método SetRegisters](icordebugregisterset2-setregisters-method.md)|Não implementado na versão .NET Framework 2,0.|  
  
## <a name="remarks"></a>Comentários  
  
> [!NOTE]
> Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Depurando interfaces](debugging-interfaces.md)
- [Interface ICorDebugRegisterSet](icordebugregisterset-interface.md)
