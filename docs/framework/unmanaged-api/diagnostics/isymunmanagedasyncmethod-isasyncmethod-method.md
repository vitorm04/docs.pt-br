---
title: Método ISymUnmanagedAsyncMethod::IsAsyncMethod
ms.date: 03/30/2017
ms.assetid: 670a7653-dac6-4171-98ee-d669e3adf4b2
ms.openlocfilehash: 0ea4c21e9e6a49d7bbbad5e1853598c440cd6410
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129205"
---
# <a name="isymunmanagedasyncmethodisasyncmethod-method"></a>Método ISymUnmanagedAsyncMethod::IsAsyncMethod
Verifica se o método tem informações assíncronas ou não.  
  
 Se esse método retornar `FALSE`, ele não será válido para chamar outros métodos nesta interface. Eles serão retornados `E_UNEXPECTED` nesse caso.  
  
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
  
## <a name="see-also"></a>Consulte também

- [Interface ISymUnmanagedAsyncMethod](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-interface.md)
