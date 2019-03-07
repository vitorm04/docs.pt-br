---
title: Método ICorDebugEval2::NewStringWithLength
ms.date: 03/30/2017
api_name:
- ICorDebugEval2.NewStringWithLength
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval2::NewStringWithLength
helpviewer_keywords:
- NewStringWithLength method [.NET Framework debugging]
- ICorDebugEval2::NewStringWithLength method [.NET Framework debugging]
ms.assetid: d5f54a34-6335-4708-b407-a756ec70fab4
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b84a2fad53feda2996515781035c0eaad5828d54
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57473429"
---
# <a name="icordebugeval2newstringwithlength-method"></a>Método ICorDebugEval2::NewStringWithLength
Cria uma cadeia de caracteres de comprimento especificado, com o conteúdo especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT NewStringWithLength (  
    [in] LPCWSTR               string,  
    [in] UINT                  uiLength  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `string`  
 [in] Um ponteiro para o valor de cadeia de caracteres.  
  
 `uiLength`  
 [in] Comprimento da cadeia de caracteres.  
  
## <a name="remarks"></a>Comentários  
 Se a cadeia de caracteres da direita caractere nulo deve estar em uma cadeia de caracteres gerenciada, o chamador do `NewStringWithLength` método deve garantir que o comprimento da cadeia de caracteres inclui o caractere nulo à direita.  
  
 A cadeia de caracteres sempre é criada no domínio do aplicativo no qual o thread está em execução no momento.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
