---
title: Método ICorDebugILFrame::CanSetIP
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame.CanSetIP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame::CanSetIP
helpviewer_keywords:
- CanSetIP method, ICorDebugILFrame interface [.NET Framework debugging]
- ICorDebugILFrame::CanSetIP method [.NET Framework debugging]
ms.assetid: 16caf02f-c71e-486c-90b0-f0e54357d8f0
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ad1ea4da252fe9fac89faa79195b6a6de245ad9c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33414694"
---
# <a name="icordebugilframecansetip-method"></a>Método ICorDebugILFrame::CanSetIP
Obtém o HRESULT que indica se é seguro definir o ponteiro de instrução para o local de deslocamento especificado no código do Microsoft Intermediate Language (MSIL).  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT CanSetIP (  
    [in] ULONG32   nOffset  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `nOffset`  
 [in] A configuração desejada para o ponteiro de instrução.  
  
## <a name="remarks"></a>Comentários  
 Use o `CanSetIP` método antes de chamar o [Icordebugilframe](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md) método. Se `CanSetIP` retorna qualquer HRESULT que não sejam S_OK, você ainda pode invocar `ICorDebugILFrame::SetIP`, mas não há nenhuma garantia de que o depurador continuará a execução correta e segura do código que está sendo depurado.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug, h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
