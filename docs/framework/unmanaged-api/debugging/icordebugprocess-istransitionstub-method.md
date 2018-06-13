---
title: Método ICorDebugProcess::IsTransitionStub
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.IsTransitionStub
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::IsTransitionStub
helpviewer_keywords:
- ICorDebugProcess::IsTransitionStub method [.NET Framework debugging]
- IsTransitionStub method [.NET Framework debugging]
ms.assetid: f7653317-7e48-4163-be03-f50f1a4b0f70
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e06dc35998a2874ed1d2f76725078874817e94d8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33420089"
---
# <a name="icordebugprocessistransitionstub-method"></a>Método ICorDebugProcess::IsTransitionStub
Obtém um valor que indica se um endereço está dentro de um stub que fará com que uma transição para código gerenciado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT IsTransitionStub(  
    [in]  CORDB_ADDRESS address,  
    [out] BOOL *pbTransitionStub);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `address`  
 [in] Um `CORDB_ADDRESS` valor que especifica o endereço em questão.  
  
 `pbTransitionStub`  
 [out] Um ponteiro para um valor booliano que é `true` se o endereço especificado está dentro de um stub que fará com que uma transição para código gerenciado; caso contrário *`pbTransitionStub` é `false`.  
  
## <a name="remarks"></a>Comentários  
 O `IsTransitionStub` método pode ser usado pelo revisão de código não gerenciado para decidir quando devolver o controle de revisão para o seletor gerenciado.  
  
 Você também pode stubs de transição de identidade examinando as informações do arquivo executável portátil (PE).  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
