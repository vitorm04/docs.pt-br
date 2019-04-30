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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 08bf4022f7cd7f85ffe7939c16fd47950e131a77
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61948883"
---
# <a name="icordebugprocess2getreferencevaluefromgchandle-method"></a>Método ICorDebugProcess2::GetReferenceValueFromGCHandle
Obtém um ponteiro de referência para o objeto especificado gerenciado que possua uma coleta de lixo a alça.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetReferenceValueFromGCHandle (  
    [in]  UINT_PTR                 handle,  
    [out] ICorDebugReferenceValue  **pOutValue  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `handle`  
 [in] Um ponteiro para um objeto gerenciado que tem um identificador de coleta de lixo. Esse valor é uma <xref:System.IntPtr> do objeto e pode ser recuperada do <xref:System.Runtime.InteropServices.GCHandle> do objeto gerenciado.  
  
 `pOutValue`  
 [out] Um ponteiro para o endereço de um objeto ICorDebugReferenceValue que representa uma referência ao objeto especificado gerenciado.  
  
## <a name="remarks"></a>Comentários  
 Não confunda o valor retornado de referência com um valor de referência de coleta de lixo.  
  
 A referência retornada se comporta como uma referência normal. Ela é desabilitada quando a execução de código continua depois de um ponto de interrupção. O tempo de vida do objeto de destino não é afetado pelo tempo de vida do valor de referência.  
  
> [!NOTE]
>  O `GetReferenceValueFromGCHandle` método não valida o identificador. Portanto, o `GetReferenceValueFromGCHandle` método pode corromper o depurador e o código que está sendo depurado, se um identificador inválido for passado.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
