---
title: Método ISymUnmanagedWriter::Abort
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.Abort
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::Abort
helpviewer_keywords:
- ISymUnmanagedWriter::Abort method [.NET Framework debugging]
- Abort method, ISymUnmanagedWriter interface [.NET Framework debugging]
ms.assetid: 416b220f-38d4-48e0-bb49-d2faa7366702
topic_type:
- apiref
ms.openlocfilehash: 09f39d3b6486e2ec3c04c5d1858a85ce56895527
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83610152"
---
# <a name="isymunmanagedwriterabort-method"></a>Método ISymUnmanagedWriter::Abort
Fecha o gravador de símbolo sem confirmar os símbolos para o repositório de símbolos. Após essa chamada, o gravador de símbolo se torna inválido para atualizações adicionais. Para confirmar os símbolos e fechar o gravador de símbolo, use o método [ISymUnmanagedWriter:: Close](isymunmanagedwriter-close-method.md) em vez disso.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT Abort();  
```  
  
## <a name="return-value"></a>Valor retornado  
 S_OK se o método tiver sucesso; caso contrário, E_FAIL ou algum outro código de erro.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Confira também

- [Interface ISymUnmanagedWriter](isymunmanagedwriter-interface.md)
