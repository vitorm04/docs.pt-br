---
title: Método ISymUnmanagedScope::GetChildren
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope.GetChildren
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope::GetChildren
helpviewer_keywords:
- ISymUnmanagedScope::GetChildren method [.NET Framework debugging]
- GetChildren method [.NET Framework debugging]
ms.assetid: 0bed524e-cc48-4bf0-b9fa-25d665e63ddb
topic_type:
- apiref
ms.openlocfilehash: c7e9d2fe94c33127d8b105333ad6dac9d6cc5af6
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446364"
---
# <a name="isymunmanagedscopegetchildren-method"></a>Método ISymUnmanagedScope::GetChildren
Obtém os filhos deste escopo.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetChildren(  
    [in]  ULONG32  cChildren,  
    [out] ULONG32  *pcChildren,  
    [out, size_is(cChildren),  
        length_is(*pcChildren)] ISymUnmanagedScope* children[]);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `cChildren`  
 no Um `ULONG32` que indica o tamanho da matriz de `children`.  
  
 `pcChildren`  
 fora Um ponteiro para um `ULONG32` que recebe o tamanho do buffer necessário para conter os filhos.  
  
 `children`  
 fora A matriz de filhos retornada.  
  
## <a name="return-value"></a>Valor retornado  
 S_OK se o método tiver sucesso; caso contrário, E_FAIL ou algum outro código de erro.  
  
## <a name="requirements"></a>{1&gt;{2&gt;Requisitos&lt;2}&lt;1}  
 **Cabeçalho:** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Consulte também

- [Interface ISymUnmanagedScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)
- [Método GetParent](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getparent-method.md)
