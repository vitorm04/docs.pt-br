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
ms.openlocfilehash: 18084cb69d2c620fc892cc05e5a561e8fda3bc1c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61775512"
---
# <a name="icordebugprocessistransitionstub-method"></a>Método ICorDebugProcess::IsTransitionStub
Obtém um valor que indica se um endereço está dentro de um stub que fará com que uma transição para código gerenciado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT IsTransitionStub(  
    [in]  CORDB_ADDRESS address,  
    [out] BOOL *pbTransitionStub);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `address`  
 [in] Um `CORDB_ADDRESS` valor que especifica o endereço em questão.  
  
 `pbTransitionStub`  
 [out] Um ponteiro para um valor booliano que será `true` se o endereço especificado está dentro de um stub que fará com que uma transição para código gerenciado; caso contrário, *`pbTransitionStub` é `false`.  
  
## <a name="remarks"></a>Comentários  
 O `IsTransitionStub` método pode ser usado pelo código não gerenciado de passo a passo para decidir quando retornar o controle de revisão para o escalonador gerenciado.  
  
 Você também pode stubs de transição de identidade examinando informações no arquivo executável portátil (PE).  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
