---
title: "Método ISymUnmanagedWriter::OpenMethod"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter.OpenMethod
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter::OpenMethod
helpviewer_keywords:
- ISymUnmanagedWriter::OpenMethod method [.NET Framework debugging]
- OpenMethod method [.NET Framework debugging]
ms.assetid: fb90cb7f-af88-45e8-a99f-80a0bbddb08b
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 61d63fb96635e34e07c3997c1aad838e67c70742
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="isymunmanagedwriteropenmethod-method"></a>Método ISymUnmanagedWriter::OpenMethod
Abre um método para o símbolo que informações são emitidas. O método dado torna-se o método atual para chamadas para definir pontos de sequência, parâmetros e escopos léxicos. Há um escopo léxico implícita ao redor de todo o método. Reabrir um método que foi fechado anteriormente apaga qualquer símbolos definidos anteriormente para esse método. Pode haver apenas um método aberto por vez.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT OpenMethod(  
    [in] mdMethodDef method);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `method`  
 [in] O token de metadados para o método a ser aberto.  
  
## <a name="return-value"></a>Valor de retorno  
 S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Consulte também  
 [Interface ISymUnmanagedWriter](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)  
 [Método CloseMethod](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closemethod-method.md)  
 [Método OpenMethod2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-openmethod2-method.md)
