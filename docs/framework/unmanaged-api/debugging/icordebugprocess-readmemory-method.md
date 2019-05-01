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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 218279684304b766a9bf009f5891ac4910254a3c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61994377"
---
# <a name="icordebugprocessreadmemory-method"></a>Método ICorDebugProcess::ReadMemory
Lê uma área especificada de memória para esse processo.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT ReadMemory(  
    [in]  CORDB_ADDRESS address,   
    [in]  DWORD size,  
    [out, size_is(size), length_is(size)] BYTE buffer[],  
    [out] SIZE_T *read);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `address`  
 [in] Um `CORDB_ADDRESS` valor que especifica o endereço básico da memória a ser lido.  
  
 `size`  
 [in] O número de bytes a serem lidos da memória.  
  
 `buffer`  
 [out] Um buffer que recebe o conteúdo da memória.  
  
 `read`  
 [out] Um ponteiro para o número de bytes transferidos para o buffer especificado.  
  
## <a name="remarks"></a>Comentários  
 O `ReadMemory` método destina-se principalmente a ser usado pela depuração interop para inspecionar as regiões de memória que estão sendo usadas pela parte não gerenciada o ser depurado. Esse método também pode ser usado para ler o código Microsoft intermediate language (MSIL) e o código nativo compilado por JIT.  
  
 Nenhum ponto de interrupção gerenciados serão removidos dos dados que são retornados no `buffer` parâmetro. Nenhum ajuste será feita para pontos de interrupção nativos definido [ICorDebugProcess2::SetUnmanagedBreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md).  
  
 Sem cache de memória de processo é executada.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
