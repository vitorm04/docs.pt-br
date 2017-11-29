---
title: "Método ICorDebugILFrame::GetIP"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugILFrame.GetIP
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugILFrame::GetIP
helpviewer_keywords:
- GetIP method, ICorDebugILFrame interface [.NET Framework debugging]
- ICorDebugILFrame::GetIP method [.NET Framework debugging]
ms.assetid: 18217ba1-1776-4297-a3b9-f77e64b0fead
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 6f1ea9ad653deeaaa22944517ba5cbdb2f39c6d4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
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
  
#### <a name="parameters"></a>Parâmetros  
 `pnOffset`  
 [out] O valor do ponteiro de instrução.  
  
 `pMappingResult`  
 [out] Um ponteiro para uma combinação bit a bit dos valores de enumeração CorDebugMappingResult que descrevem como o valor do ponteiro de instrução foi obtido.  
  
## <a name="remarks"></a>Comentários  
 O valor do ponteiro de instrução é o deslocamento do quadro de pilha em código da função Microsoft intermediate language (MSIL). Se o quadro de pilhas estiver ativo, esse endereço é a próxima instrução a executar. Se o quadro de pilha não estiver ativo, esse endereço é a próxima instrução a ser executada quando o quadro de pilhas é reativado.  
  
 Se este quadro é um quadro compilado do just-in-time (JIT), o valor do ponteiro de instrução será determinado pelo mapeamento com versões anteriores de ponteiro de instrução nativos real, portanto, o valor pode ser apenas aproximado.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
