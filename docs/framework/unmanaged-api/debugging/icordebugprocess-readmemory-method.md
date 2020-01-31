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
ms.openlocfilehash: dca2a4e5ee869346108137a8ba01ab8855756725
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792551"
---
# <a name="icordebugprocessreadmemory-method"></a>Método ICorDebugProcess::ReadMemory
Lê uma área especificada de memória para esse processo.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT ReadMemory(  
    [in]  CORDB_ADDRESS address,   
    [in]  DWORD size,  
    [out, size_is(size), length_is(size)] BYTE buffer[],  
    [out] SIZE_T *read);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `address`  
 no Um valor `CORDB_ADDRESS` que especifica o endereço base da memória a ser lida.  
  
 `size`  
 no O número de bytes a serem lidos da memória.  
  
 `buffer`  
 fora Um buffer que recebe o conteúdo da memória.  
  
 `read`  
 fora Um ponteiro para o número de bytes transferidos para o buffer especificado.  
  
## <a name="remarks"></a>Comentários  
 O método `ReadMemory` destina-se principalmente a ser usado pela depuração de interoperabilidade para inspecionar regiões de memória que estão sendo usadas pela parte não gerenciada do depurador. Esse método também pode ser usado para ler o código MSIL (Microsoft Intermediate Language) e o código compilado por JIT nativo.  
  
 Todos os pontos de interrupção gerenciados serão removidos dos dados retornados no parâmetro `buffer`. Nenhum ajuste será feito para pontos de interrupção nativos definidos por [ICorDebugProcess2:: SetUnmanagedBreakpoint](icordebugprocess2-setunmanagedbreakpoint-method.md).  
  
 Nenhum cache de memória de processo é executado.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
