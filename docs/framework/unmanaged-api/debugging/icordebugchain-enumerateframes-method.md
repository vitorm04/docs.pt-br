---
title: Método ICorDebugChain::EnumerateFrames
ms.date: 03/30/2017
api_name:
- ICorDebugChain.EnumerateFrames
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::EnumerateFrames method
helpviewer_keywords:
- EnumerateFrames method [.NET Framework debugging]
- ICorDebugChain::EnumerateFrames method [.NET Framework debugging]
ms.assetid: 9fcefa98-750d-4168-8915-8173a43accf2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7568f8ca3b92ef465ab595348f68895f389d61e4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61645302"
---
# <a name="icordebugchainenumerateframes-method"></a>Método ICorDebugChain::EnumerateFrames
Obtém um enumerador que contém todos os quadros de pilha gerenciada na cadeia, começando com o quadro mais recente.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT EnumerateFrames (  
    [out] ICorDebugFrameEnum **ppFrames  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `ppFrames`  
 [out] Um ponteiro para o endereço de um objeto ICorDebugFrameEnum que é o enumerador para os quadros de pilha.  
  
## <a name="remarks"></a>Comentários  
 A cadeia representa a pilha de chamadas física para o thread.  
  
 O `EnumerateFrames` método deve ser chamado apenas para cadeias de gerenciado. A API de depuração não fornece métodos para obter quadros contidos nas cadeias de não gerenciadas. O depurador deve usar outros meios para obter essas informações.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
