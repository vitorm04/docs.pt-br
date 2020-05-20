---
title: Método ISymUnmanagedAsyncMethod::IsAsyncMethod
ms.date: 03/30/2017
ms.assetid: 670a7653-dac6-4171-98ee-d669e3adf4b2
ms.openlocfilehash: 91b4c2688dadf12fa4a835a662622267d7831cf8
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441793"
---
# <a name="isymunmanagedasyncmethodisasyncmethod-method"></a>Método ISymUnmanagedAsyncMethod::IsAsyncMethod
Verifica se o método tem informações assíncronas ou não.  
  
 Se esse método retornar `FALSE` , ele será inválido para chamar outros métodos nesta interface. Eles serão retornados `E_UNEXPECTED` nesse caso.  
  
## <a name="syntax"></a>Sintaxe  
  
```idl  
HRESULT IsAsyncMethod(    [out, retval] BOOL* pRetVal);  
```  
  
## <a name="parameters"></a>Parâmetros  
  
|Parâmetro|Descrição|  
|---------------|-----------------|  
|`pRetVal`||  
  
## <a name="return-value"></a>Valor retornado  
 Retorna `HRESULT`.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Confira também

- [Interface ISymUnmanagedAsyncMethod](isymunmanagedasyncmethod-interface.md)
