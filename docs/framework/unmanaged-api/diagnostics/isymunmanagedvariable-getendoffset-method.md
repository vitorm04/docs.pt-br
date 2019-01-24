---
title: Método ISymUnmanagedVariable::GetEndOffset
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable.GetEndOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable::GetEndOffset
helpviewer_keywords:
- ISymUnmanagedVariable::GetEndOffset method [.NET Framework debugging]
- GetEndOffset method, ISymUnmanagedVariable interface [.NET Framework debugging]
ms.assetid: e5d777c5-d450-4c0f-999c-b3953ee22cfb
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a4c474b2ea9bc80be156c8e1424eabe3d2384666
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54585257"
---
# <a name="isymunmanagedvariablegetendoffset-method"></a>Método ISymUnmanagedVariable::GetEndOffset
Obtém o deslocamento final dessa variável dentro de seu pai. Quando se trata de uma variável local dentro de um escopo, o deslocamento final se enquadram dentro dos deslocamentos definidos para o escopo.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetEndOffset(  
    [out, retval] ULONG32* pRetVal);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pRetVal`  
 [out] Um ponteiro para um `ULONG32` que recebe o deslocamento de fim.  
  
## <a name="return-value"></a>Valor de retorno  
 S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Consulte também
- [Interface ISymUnmanagedVariable](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)
- [Método GetStartOffset](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getstartoffset-method.md)
