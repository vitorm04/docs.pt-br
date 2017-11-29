---
title: "Método ISymUnmanagedVariable::GetAddressField3"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedVariable.GetAddressField3
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedVariable::GetAddressField3
helpviewer_keywords:
- ISymUnmanagedVariable::GetAddressField3 method [.NET Framework debugging]
- GetAddressField3 method [.NET Framework debugging]
ms.assetid: 4d834721-ad8d-439d-b356-c6b4aef022fc
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 1dfeb3f02b0c767dfc200a625fa4c617692dc11f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="isymunmanagedvariablegetaddressfield3-method"></a>Método ISymUnmanagedVariable::GetAddressField3
Obtém o terceiro campo de endereço para essa variável. Seu significado depende do tipo de endereço.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetAddressField3(  
    [out, retval] ULONG32* pRetVal);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pRetVal`  
 [out] Um ponteiro para um `ULONG32` que recebe o terceiro campo de endereço.  
  
## <a name="return-value"></a>Valor de retorno  
 S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Consulte também  
 [Interface ISymUnmanagedVariable](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)  
 [Método GetAddressField1](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield1-method.md)  
 [Método GetAddressField2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield2-method.md)  
 [Método GetAddressKind](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddresskind-method.md)
