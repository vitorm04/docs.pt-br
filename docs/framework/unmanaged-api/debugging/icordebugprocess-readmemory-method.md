---
title: Método ICorDebugProcess::ReadMemory
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.ReadMemory
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::ReadMemory
helpviewer_keywords:
- ReadMemory method [.NET Framework debugging]
- ICorDebugProcess::ReadMemory method [.NET Framework debugging]
ms.assetid: 28e4b2f6-9589-445c-be24-24a3306795e7
topic_type:
- apiref
ms.openlocfilehash: 383e3f8990a1f355c94ff5e9f9daa69bdbdd97bb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178659"
---
# <a name="icordebugprocessreadmemory-method"></a>Método ICorDebugProcess::ReadMemory
Lê uma área de memória especificada para este processo.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT ReadMemory(  
    [in]  CORDB_ADDRESS address,
    [in]  DWORD size,  
    [out, size_is(size), length_is(size)] BYTE buffer[],  
    [out] SIZE_T *read);  
```  
  
## <a name="parameters"></a>parâmetros  
 `address`  
 [em] Um `CORDB_ADDRESS` valor que especifica o endereço base da memória a ser lido.  
  
 `size`  
 [em] O número de bytes a serem lidos na memória.  
  
 `buffer`  
 [fora] Um buffer que recebe o conteúdo da memória.  
  
 `read`  
 [fora] Um ponteiro para o número de bytes transferidos para o buffer especificado.  
  
## <a name="remarks"></a>Comentários  
 O `ReadMemory` método destina-se principalmente a ser usado pela depuração de interop para inspecionar regiões de memória que estão sendo usadas pela porção não gerenciada da depuração. Este método também pode ser usado para ler o código de linguagem intermediária da Microsoft (MSIL) e o código nativo compilado pelo JIT.  
  
 Quaisquer pontos de interrupção gerenciados serão removidos dos `buffer` dados que são devolvidos no parâmetro. Não serão feitos ajustes para os breakpoints nativos definidos por [ICorDebugProcess2::SetUnmanagedBreakpoint](icordebugprocess2-setunmanagedbreakpoint-method.md).  
  
 Nenhum cache de memória do processo é realizado.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
