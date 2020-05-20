---
title: Método ISymUnmanagedVariable::GetAddressKind
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable.GetAddressKind
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable::GetAddressKind
helpviewer_keywords:
- GetAddressKind method [.NET Framework debugging]
- ISymUnmanagedVariable::GetAddressKind method [.NET Framework debugging]
ms.assetid: a71563c0-62f2-4eb4-970c-825d61827613
topic_type:
- apiref
ms.openlocfilehash: 093c5e3e64395c8946acd9201990d132e8111fc7
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83610581"
---
# <a name="isymunmanagedvariablegetaddresskind-method"></a>Método ISymUnmanagedVariable::GetAddressKind
Obtém o tipo de endereço dessa variável.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetAddressKind(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pRetVal`  
 fora Um ponteiro para um `ULONG32` que recebe o valor. Os valores possíveis são definidos na enumeração [CorSymAddrKind](corsymaddrkind-enumeration.md) .  
  
## <a name="return-value"></a>Valor retornado  
 S_OK se o método tiver sucesso; caso contrário, E_FAIL ou algum outro código de erro.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Confira também

- [Interface ISymUnmanagedVariable](isymunmanagedvariable-interface.md)
