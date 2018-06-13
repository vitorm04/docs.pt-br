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
ms.openlocfilehash: 6b3b77a0ffc7af3b3640d1b255bd3be522f45a7a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33413544"
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
  
#### <a name="parameters"></a>Parâmetros  
 `string`  
 [in] Um ponteiro para o valor de cadeia de caracteres.  
  
 `uiLength`  
 [in] Comprimento da cadeia de caracteres.  
  
## <a name="remarks"></a>Comentários  
 Se a cadeia de caracteres da direita caractere nulo deve estar na cadeia de caracteres gerenciada, o chamador de `NewStringWithLength` método deve garantir que o comprimento da cadeia de caracteres inclui o caractere nulo à direita.  
  
 A cadeia de caracteres sempre é criada no domínio do aplicativo no qual o thread está em execução no momento.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
