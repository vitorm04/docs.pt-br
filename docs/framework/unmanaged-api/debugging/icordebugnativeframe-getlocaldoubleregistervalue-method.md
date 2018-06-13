---
title: Método ICorDebugNativeFrame::GetLocalDoubleRegisterValue
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame.GetLocalDoubleRegisterValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame::GetLocalDoubleRegisterValue
helpviewer_keywords:
- ICorDebugNativeFrame::GetLocalDoubleRegisterValue method [.NET Framework debugging]
- GetLocalDoubleRegisterValue method [.NET Framework debugging]
ms.assetid: 1f838215-ac8a-434f-8ce6-03021d3098d9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9de77f942a1b89b0ab11ef71229e491a5305cafc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33420746"
---
# <a name="icordebugnativeframegetlocaldoubleregistervalue-method"></a>Método ICorDebugNativeFrame::GetLocalDoubleRegisterValue
Obtém o valor de um argumento ou uma variável local que é armazenado em dois registros especificados para este quadro nativo.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetLocalDoubleRegisterValue (  
    [in] CorDebugRegister   highWordReg,  
    [in] CorDebugRegister   lowWordReg,  
    [in] ULONG              cbSigBlob,  
    [in] PCCOR_SIGNATURE    pvSigBlob,  
    [out] ICorDebugValue    **ppValue  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `highWordReg`  
 [in] Um valor da enumeração "CorDebugRegister" que especifica o registro que contém a palavra alta do valor.  
  
 `lowWordReg`  
 [in] Um valor de `CorDebugRegister` enumeração que especifica o registro que contém a palavra baixa do valor.  
  
 `cbSigBlob`  
 [in] Um inteiro que especifica o tamanho da assinatura de metadados binária que é referenciado pelo `pvSigBlob` parâmetro.  
  
 `pvSigBlob`  
 [in] Um `PCCOR_SIGNATURE` valor que aponta para a assinatura de metadados binário do tipo de valor.  
  
 `ppValue`  
 [out] Um ponteiro para o endereço de um objeto de "ICorDebugValue" que representa o valor recuperado é armazenado nos registradores especificados.  
  
## <a name="remarks"></a>Comentários  
 O `GetLocalDoubleRegisterValue` método pode ser usado em um quadro nativo ou um just-in-time (JIT)-compilado quadro.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 
