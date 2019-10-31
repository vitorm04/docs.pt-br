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
ms.openlocfilehash: eaf5b9980d55b0efb473b4631a8c052b013d0796
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137250"
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
 no Um valor `CORDB_ADDRESS` que é o endereço base da área de memória na qual os dados são gravados. Antes que a transferência de dados ocorra, o sistema verifica se a área de memória do tamanho especificado, começando no endereço base, está acessível para gravação. Se não estiver acessível, o método falhará.  
  
 `size`  
 no O número de bytes a serem gravados na área de memória.  
  
 `buffer`  
 no Um buffer que contém dados a serem gravados.  
  
 `written`  
 fora Um ponteiro para uma variável que recebe o número de bytes gravados na área de memória nesse processo. Se `written` for NULL, esse parâmetro será ignorado.  
  
## <a name="remarks"></a>Comentários  
 Os dados são gravados automaticamente por trás de qualquer ponto de interrupção. No .NET Framework versão 2,0, os depuradores nativos não devem usar esse método para injetar pontos de interrupção no fluxo de instrução. Use [ICorDebugProcess2:: SetUnmanagedBreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md) em vez disso.  
  
 O método `WriteMemory` deve ser usado somente fora do código gerenciado. Esse método pode corromper o tempo de execução se for usado de forma inadequada.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
