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
ms.openlocfilehash: 3836b6c08098d38516c8a25260fb28998a2317fe
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73084776"
---
# <a name="icordebugeval2newstringwithlength-method"></a>Método ICorDebugEval2::NewStringWithLength
Cria uma cadeia de caracteres do comprimento especificado, com o conteúdo especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT NewStringWithLength (  
    [in] LPCWSTR               string,  
    [in] UINT                  uiLength  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `string`  
 no Um ponteiro para o valor da cadeia de caracteres.  
  
 `uiLength`  
 no Comprimento da cadeia de caracteres.  
  
## <a name="remarks"></a>Comentários  
 Se espera-se que o caractere nulo à direita da cadeia de caracteres esteja na cadeia de caracteres gerenciada, o chamador do método `NewStringWithLength` deve garantir que o comprimento da cadeia de caracteres inclua o caractere nulo à direita.  
  
 A cadeia de caracteres é sempre criada no domínio do aplicativo no qual o thread está sendo executado no momento.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
