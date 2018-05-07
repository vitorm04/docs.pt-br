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
ms.openlocfilehash: d408f317b546fb7e8314e904e6f5ad9e6296ae6d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugchainenumerateframes-method"></a>Método ICorDebugChain::EnumerateFrames
Obtém um enumerador que contém todos os quadros de pilha gerenciada na cadeia, começando com o quadro mais recente.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT EnumerateFrames (  
    [out] ICorDebugFrameEnum **ppFrames  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ppFrames`  
 [out] Um ponteiro para o endereço de um objeto de ICorDebugFrameEnum que é o enumerador para os quadros de pilha.  
  
## <a name="remarks"></a>Comentários  
 A cadeia representa a pilha de chamadas físico para o thread.  
  
 O `EnumerateFrames` método deve ser chamado somente para gerenciado cadeias. A API de depuração não fornece métodos para a obtenção de quadros contidos nas cadeias de não gerenciadas. O depurador deve usar outro meio para obter essas informações.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
