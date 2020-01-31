---
title: Método ICorDebugMDA::GetDescription
ms.date: 03/30/2017
api_name:
- ICorDebugMDA.GetDescription
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugMDA::GetDescription
helpviewer_keywords:
- GetDescription method [.NET Framework debugging]
- ICorDebugMDA::GetDescription method [.NET Framework debugging]
ms.assetid: 01d1b481-ca67-4712-8744-d342ec0df639
topic_type:
- apiref
ms.openlocfilehash: e3744cbfa08de30c53f15c457034b50e2fc5d283
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793243"
---
# <a name="icordebugmdagetdescription-method"></a>Método ICorDebugMDA::GetDescription
Obtém uma cadeia de caracteres que contém a descrição do MDA (Assistente de depuração gerenciada) representado por [ICorDebugMDA](icordebugmda-interface.md).  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetDescription (  
    [in] ULONG32   cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
        WCHAR      szName[]  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `cchName`  
 no O tamanho do buffer de cadeia de caracteres que armazenará a descrição.  
  
 `pcchName`  
 fora Um ponteiro para o número de bytes retornados no buffer de cadeia de caracteres.  
  
 `szName`  
 fora Um buffer de cadeia de caracteres que contém a descrição do MDA.  
  
## <a name="remarks"></a>Comentários  
 A cadeia de caracteres pode ser de comprimento zero.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Interface ICorDebugMDA](icordebugmda-interface.md)
- [Diagnosticando erros com Assistentes de Depuração Gerenciados](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
