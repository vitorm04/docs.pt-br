---
title: Método ICorDebugFrame::GetFunction
ms.date: 03/30/2017
api_name:
- ICorDebugFrame.GetFunction
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrame::GetFunction
helpviewer_keywords:
- GetFunction method, ICorDebugFrame interface [.NET Framework debugging]
- ICorDebugFrame::GetFunction method [.NET Framework debugging]
ms.assetid: 879d2311-0ff1-4616-a8b3-959ea5868b2e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a48396f8ef668cfe7755b2718180317b465793b6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61995833"
---
# <a name="icordebugframegetfunction-method"></a>Método ICorDebugFrame::GetFunction
Obtém a função que contém o código associado a esse registro de ativação.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetFunction (  
    [out] ICorDebugFunction  **ppFunction  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `ppFunction`  
 [out] Um ponteiro para o endereço de um objeto ICorDebugFunction que representa a função que contém o código associado a esse registro de ativação.  
  
## <a name="remarks"></a>Comentários  
 O `GetFunction` método poderá falhar se o quadro não está associado a qualquer função específica.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
