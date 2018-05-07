---
title: Método ICorDebugILFrame::EnumerateLocalVariables
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame.EnumerateLocalVariables
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame::EnumerateLocalVariables
helpviewer_keywords:
- EnumerateLocalVariables method [.NET Framework debugging]
- ICorDebugILFrame::EnumerateLocalVariables method [.NET Framework debugging]
ms.assetid: 1a67fa1b-2419-4cd0-aad4-6f46a0719b4b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6fd7694901534ad6897bbf78239081af6314e4bd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugilframeenumeratelocalvariables-method"></a>Método ICorDebugILFrame::EnumerateLocalVariables
Obtém um enumerador para as variáveis locais nesse quadro.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT EnumerateLocalVariables(   
    [out] ICorDebugValueEnum    **ppValueEnum  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ppValueEnum`  
 [out] Um ponteiro para o endereço de um objeto de ICorDebugValueEnum que é o enumerador para as variáveis locais nesse quadro.  
  
## <a name="remarks"></a>Comentários  
 `EnumerateLocalVariables` Obtém um enumerador que pode listar as variáveis locais disponíveis no quadro de chamada que é representado pelo objeto ICorDebugILFrame. A lista pode não incluir todas as variáveis locais na função em execução, porque alguns deles não podem estar ativa.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
