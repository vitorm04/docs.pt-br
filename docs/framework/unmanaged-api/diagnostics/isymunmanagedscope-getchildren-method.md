---
title: "Método ISymUnmanagedScope::GetChildren"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedScope.GetChildren
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedScope::GetChildren
helpviewer_keywords:
- ISymUnmanagedScope::GetChildren method [.NET Framework debugging]
- GetChildren method [.NET Framework debugging]
ms.assetid: 0bed524e-cc48-4bf0-b9fa-25d665e63ddb
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: a43a0f46532bfb0eeaa4e385946a5aaa1b50eba8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="isymunmanagedscopegetchildren-method"></a>Método ISymUnmanagedScope::GetChildren
Obtém o filho desse escopo.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetChildren(  
    [in]  ULONG32  cChildren,  
    [out] ULONG32  *pcChildren,  
    [out, size_is(cChildren),  
        length_is(*pcChildren)] ISymUnmanagedScope* children[]);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `cChildren`  
 [in] Um `ULONG32` que indica o tamanho do `children` matriz.  
  
 `pcChildren`  
 [out] Um ponteiro para um `ULONG32` que recebe o tamanho do buffer necessário para conter os filhos.  
  
 `children`  
 [out] A matriz retornada de filhos.  
  
## <a name="return-value"></a>Valor de retorno  
 S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Consulte também  
 [Interface ISymUnmanagedScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)  
 [Método GetParent](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getparent-method.md)
