---
title: "Método ISymUnmanagedScope::GetStartOffset"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedScope.GetStartOffset
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedScope::GetStartOffset
helpviewer_keywords:
- GetStartOffset method, ISymUnmanagedScope interface [.NET Framework debugging]
- ISymUnmanagedScope::GetStartOffset method [.NET Framework debugging]
ms.assetid: da6bbc75-94d1-4354-9722-0d455b4428fb
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 8e24924607cad1922f2d1b5a816dc635eb6c7820
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="isymunmanagedscopegetstartoffset-method"></a>Método ISymUnmanagedScope::GetStartOffset
Obtém o deslocamento de início para esse escopo.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetStartOffset(  
    [out, retval] ULONG32* pRetVal);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pRetVal`  
 [out] Um ponteiro para um `ULONG32` que contém o deslocamento inicial.  
  
## <a name="return-value"></a>Valor de retorno  
 S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Consulte também  
 [Interface ISymUnmanagedScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)  
 [Método GetEndOffset](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getendoffset-method.md)
