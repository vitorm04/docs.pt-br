---
title: "Método ICorDebugILFrame::SetIP"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugILFrame.SetIP
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugILFrame::SetIP
helpviewer_keywords:
- SetIP method, ICorDebugILFrame interface [.NET Framework debugging]
- ICorDebugILFrame::SetIP method [.NET Framework debugging]
ms.assetid: 23f38dc1-85e4-4263-9235-2d05bbb6a833
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b92dc50777d55ba6bfa1a0559ab198dd69114ade
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugilframesetip-method"></a>Método ICorDebugILFrame::SetIP
Define o ponteiro de instrução para o local de deslocamento especificado no código Microsoft intermediate language (MSIL).  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT SetIP (  
    [in] ULONG32 nOffset  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `nOffset`  
 O local de deslocamento no código MSIL.  
  
## <a name="remarks"></a>Comentários  
 Chamadas para `SetIP` imediatamente invalida todos os quadros e cadeias de para o thread atual. Se o depurador precisa de informações de quadro após uma chamada para `SetIP`, ele deve realizar um novo rastreamento de pilha.  
  
 [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) tentará manter o quadro de pilha em um estado válido. No entanto, mesmo se o quadro estiver em um estado válido, ainda pode haver problemas como variáveis locais não inicializadas. O chamador é responsável por garantir que a coerência do programa em execução.  
  
 Em plataformas de 64 bits, o ponteiro de instrução não pode ser movido de um `catch` ou `finally` bloco. Se `SetIP` é chamado para fazer isso em uma plataforma de 64 bits, será retornado um HRESULT indicando falha.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
