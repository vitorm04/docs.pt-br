---
title: Método ICorDebugILFrame::GetIP
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame.GetIP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame::GetIP
helpviewer_keywords:
- GetIP method, ICorDebugILFrame interface [.NET Framework debugging]
- ICorDebugILFrame::GetIP method [.NET Framework debugging]
ms.assetid: 18217ba1-1776-4297-a3b9-f77e64b0fead
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7a7b8985e7580282d0e38205f9b1d6078f86cee6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61988605"
---
# <a name="icordebugilframegetip-method"></a>Método ICorDebugILFrame::GetIP
Obtém o valor do ponteiro de instrução e um valor de combinação bit a bit que descreve como o valor do ponteiro de instrução foi obtido.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetIP (  
    [out] ULONG32               *pnOffset,   
    [out] CorDebugMappingResult *pMappingResult  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pnOffset`  
 [out] O valor do ponteiro de instrução.  
  
 `pMappingResult`  
 [out] Um ponteiro para uma combinação bit a bit dos valores de enumeração CorDebugMappingResult que descrevem como o valor do ponteiro de instrução foi obtido.  
  
## <a name="remarks"></a>Comentários  
 O valor do ponteiro de instrução é o deslocamento do quadro de pilha no código da função Microsoft intermediate language (MSIL). Se o quadro de pilhas estiver ativo, esse endereço é a próxima instrução a executar. Se o quadro de pilha não estiver ativo, esse endereço é a próxima instrução a ser executado quando o quadro de pilha for reativado.  
  
 Se este quadro é um quadro compilado do just-in-time (JIT), o valor do ponteiro de instrução será determinado pelo mapeamento com versões anteriores do ponteiro de instrução de nativa real, portanto, o valor pode ser apenas aproximado.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
