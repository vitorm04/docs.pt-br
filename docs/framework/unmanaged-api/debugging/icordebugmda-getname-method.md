---
title: Método ICorDebugMDA::GetName
ms.date: 03/30/2017
api_name:
- ICorDebugMDA.GetName
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugMDA::GetName
helpviewer_keywords:
- ICorDebugMDA::GetName method [.NET Framework debugging]
- GetName method, ICorDebugMDA interface [.NET Framework debugging]
ms.assetid: 885bf5e8-00b7-4cd7-9d8d-e720d47918c4
topic_type:
- apiref
ms.openlocfilehash: 522ac2fd448abaaba48d4d5c20551e8029b35fd4
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793237"
---
# <a name="icordebugmdagetname-method"></a>Método ICorDebugMDA::GetName
Obtém uma cadeia de caracteres que contém o nome do MDA (Assistente de depuração gerenciada) representado por [ICorDebugMDA](icordebugmda-interface.md).  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetName (  
    [in] ULONG32   cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
        WCHAR      szName[]  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `cchName`  
 no O tamanho da matriz de `szName`.  
  
 `pcchName`  
 fora Um ponteiro para o comprimento do nome.  
  
 `szName`  
 fora Uma matriz na qual armazenar o nome.  
  
## <a name="remarks"></a>Comentários  
 Os nomes de MDA são valores exclusivos. O método `GetName` é uma alternativa de desempenho conveniente para obter o fluxo XML e extrair o nome do fluxo com base no esquema.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Interface ICorDebugMDA](icordebugmda-interface.md)
- [Diagnosticando erros com Assistentes de Depuração Gerenciados](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
