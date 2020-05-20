---
title: Método ISymUnmanagedVariable::GetAddressField3
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable.GetAddressField3
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable::GetAddressField3
helpviewer_keywords:
- ISymUnmanagedVariable::GetAddressField3 method [.NET Framework debugging]
- GetAddressField3 method [.NET Framework debugging]
ms.assetid: 4d834721-ad8d-439d-b356-c6b4aef022fc
topic_type:
- apiref
ms.openlocfilehash: ff888d3e2b86efeea3f4e3d33528f731d85886bf
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615261"
---
# <a name="isymunmanagedvariablegetaddressfield3-method"></a>Método ISymUnmanagedVariable::GetAddressField3
Obtém o terceiro campo de endereço para essa variável. Seu significado depende do tipo de endereço.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetAddressField3(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pRetVal`  
 fora Um ponteiro para um `ULONG32` que recebe o terceiro campo de endereço.  
  
## <a name="return-value"></a>Valor retornado  
 S_OK se o método tiver sucesso; caso contrário, E_FAIL ou algum outro código de erro.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Confira também

- [Interface ISymUnmanagedVariable](isymunmanagedvariable-interface.md)
- [Método GetAddressField1](isymunmanagedvariable-getaddressfield1-method.md)
- [Método GetAddressField2](isymunmanagedvariable-getaddressfield2-method.md)
- [Método GetAddressKind](isymunmanagedvariable-getaddresskind-method.md)
