---
title: "Método ICorDebugILFrame::EnumerateArguments"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugILFrame.EnumerateArguments
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugILFrame::EnumerateArguments
helpviewer_keywords:
- ICorDebugILFrame::EnumerateArguments method [.NET Framework debugging]
- EnumerateArguments method [.NET Framework debugging]
ms.assetid: 00ac81e2-a774-422a-bd88-54a4b3c99f73
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 474118abc505928d16737d792a619e75f1209344
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugilframeenumeratearguments-method"></a>Método ICorDebugILFrame::EnumerateArguments
Obtém um enumerador para os argumentos nesse quadro.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT EnumerateArguments (  
    [out] ICorDebugValueEnum    **ppValueEnum  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ppValueEnum`  
 [out] Um ponteiro para o endereço de um objeto de ICorDebugValueEnum que é o enumerador para os argumentos nesse quadro.  
  
## <a name="remarks"></a>Comentários  
 `EnumerateArguments`Obtém um enumerador que pode listar os argumentos disponíveis no quadro de chamada que é representado pelo objeto ICorDebugILFrame. A lista incluirá os argumentos que são [vararg](/cpp/windows/vararg) (ou seja, um número variável de argumentos), bem como argumentos que não são `vararg`.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
