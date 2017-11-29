---
title: "Método ISymUnmanagedWriter::CloseNamespace"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter.CloseNamespace
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter::CloseNamespace
helpviewer_keywords:
- ISymUnmanagedWriter::CloseNamespace method [.NET Framework debugging]
- CloseNamespace method [.NET Framework debugging]
ms.assetid: 7f74d9c5-1377-4958-b842-6306d611cbd5
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 8423e21fbc868e4b6891279d19b2be7c1faef583
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="isymunmanagedwriterclosenamespace-method"></a>Método ISymUnmanagedWriter::CloseNamespace
Fecha a última aberto namespace.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT CloseNamespace();  
```  
  
## <a name="return-value"></a>Valor de retorno  
 S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Consulte também  
 [Interface ISymUnmanagedWriter](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)  
 [Método OpenNamespace](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-opennamespace-method.md)
