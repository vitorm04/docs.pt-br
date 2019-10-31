---
title: Método ICorDebugProcess2::GetReferenceValueFromGCHandle
ms.date: 03/30/2017
api_name:
- ICorDebugProcess2.GetReferenceValueFromGCHandle
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess2::GetReferenceValueFromGCHandle
helpviewer_keywords:
- GetReferenceValueFromGCHandle method [.NET Framework debugging]
- ICorDebugProcess2::GetReferenceValueFromGCHandle method [.NET Framework debugging]
ms.assetid: 8bdd7f4c-19f2-4ede-875e-603773e8c128
topic_type:
- apiref
ms.openlocfilehash: 47647bf0460507b4c88b47bf87bfcc3bf620aecc
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137215"
---
# <a name="icordebugprocess2getreferencevaluefromgchandle-method"></a>Método ICorDebugProcess2::GetReferenceValueFromGCHandle
Obtém um ponteiro de referência para o objeto gerenciado especificado que tem um identificador de coleta de lixo.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetReferenceValueFromGCHandle (  
    [in]  UINT_PTR                 handle,  
    [out] ICorDebugReferenceValue  **pOutValue  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `handle`  
 no Um ponteiro para um objeto gerenciado que tem um identificador de coleta de lixo. Esse valor é um objeto <xref:System.IntPtr> e pode ser recuperado do <xref:System.Runtime.InteropServices.GCHandle> para o objeto gerenciado.  
  
 `pOutValue`  
 fora Um ponteiro para o endereço de um objeto ICorDebugReferenceValue que representa uma referência ao objeto gerenciado especificado.  
  
## <a name="remarks"></a>Comentários  
 Não confunda o valor de referência retornado com um valor de referência de coleta de lixo.  
  
 A referência retornada se comporta como uma referência normal. Ele é desabilitado quando a execução do código continua após um ponto de interrupção. O tempo de vida do objeto de destino não é afetado pelo tempo de vida do valor de referência.  
  
> [!NOTE]
> O método `GetReferenceValueFromGCHandle` não valida o identificador. Portanto, o método `GetReferenceValueFromGCHandle` pode potencialmente corromper o depurador e o código que está sendo depurado se um identificador inválido for passado.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
