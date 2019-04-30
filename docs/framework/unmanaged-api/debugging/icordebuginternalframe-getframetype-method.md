---
title: Método ICorDebugInternalFrame::GetFrameType
ms.date: 03/30/2017
api_name:
- ICorDebugInternalFrame.GetFrameType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugInternalFrame::GetFrameType
helpviewer_keywords:
- GetFrameType method [.NET Framework debugging]
- ICorDebugInternalFrame::GetFrameType method [.NET Framework debugging]
ms.assetid: da278a29-dc2e-4bf7-96ce-801bdc4d7025
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a0b6f0550bad534379b562c3df9da9ab917f5270
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61946324"
---
# <a name="icordebuginternalframegetframetype-method"></a>Método ICorDebugInternalFrame::GetFrameType
Obtém o tipo deste quadro interno.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetFrameType (  
    [out] CorDebugInternalFrameType  *pType  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pType`  
 [out] Um ponteiro para um valor que indica o tipo de quadro interno representado por esta enumeração CorDebugInternalFrameType `ICorDebugInternalFrame` objeto.  
  
## <a name="remarks"></a>Comentários  
 O tipo de quadro interno nunca serão STUBFRAME_NONE. Depuradores normalmente devem ignorar os tipos de quadro interno não reconhecido.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
