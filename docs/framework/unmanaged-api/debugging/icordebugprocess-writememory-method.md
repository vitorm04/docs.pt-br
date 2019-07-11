---
title: Método ICorDebugProcess::WriteMemory
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.WriteMemory
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::WriteMemory
helpviewer_keywords:
- ICorDebugProcess::WriteMemory method [.NET Framework debugging]
- WriteMemory method [.NET Framework debugging]
ms.assetid: d5c07d86-045d-4391-893b-0bcd2959f90e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4599bf310a0b819bc662b90a5a86e87ac27c37b1
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67737010"
---
# <a name="icordebugprocesswritememory-method"></a>Método ICorDebugProcess::WriteMemory
Grava dados em uma área de memória nesse processo.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT WriteMemory(  
    [in]  CORDB_ADDRESS address,  
    [in]  DWORD size,  
    [in, size_is(size)] BYTE buffer[],  
    [out] SIZE_T *written);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `address`  
 [in] Um `CORDB_ADDRESS` valor que é o endereço básico da área de memória no qual os dados é gravado. Antes que ocorra a transferência de dados, o sistema verifica que a área de memória do tamanho especificado, começando no endereço base, é acessível para gravação. Se não estiver acessível, o método falhará.  
  
 `size`  
 [in] O número de bytes a serem gravados para a área de memória.  
  
 `buffer`  
 [in] Um buffer que contém dados a serem gravados.  
  
 `written`  
 [out] Um ponteiro para uma variável que recebe o número de bytes gravados para a área de memória nesse processo. Se `written` for NULL, esse parâmetro será ignorado.  
  
## <a name="remarks"></a>Comentários  
 Automaticamente, os dados são gravados por trás de qualquer ponto de interrupção. No .NET Framework versão 2.0, depuradores nativos não devem usar esse método para inserir pontos de interrupção no fluxo de instruções. Use [ICorDebugProcess2::SetUnmanagedBreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md) em vez disso.  
  
 O `WriteMemory` método deve ser usado apenas para código gerenciado. Esse método pode corromper o tempo de execução se usado incorretamente.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
