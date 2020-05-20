---
title: Método ISymUnmanagedWriter::Close
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.Close
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::Close
helpviewer_keywords:
- Close method, ISymUnmanagedWriter interface [.NET Framework debugging]
- ISymUnmanagedWriter::Close method [.NET Framework debugging]
ms.assetid: 4cce59e1-80b9-4fc4-b3aa-126f1c5876bc
topic_type:
- apiref
ms.openlocfilehash: 0a7ecd475a8031fedb2c8474593b45045fcc6fb9
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83610126"
---
# <a name="isymunmanagedwriterclose-method"></a>Método ISymUnmanagedWriter::Close
Fecha o gravador de símbolo depois de confirmar os símbolos para o repositório de símbolos.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT Close();  
```  
  
## <a name="return-value"></a>Valor retornado  
 S_OK se o método tiver sucesso; caso contrário, E_FAIL ou algum outro código de erro.  
  
## <a name="remarks"></a>Comentários  
 Após essa chamada, o gravador de símbolo se torna inválido para atualizações adicionais. Para fechar o gravador de símbolo sem confirmar os símbolos, use o método [ISymUnmanagedWriter:: Abort](isymunmanagedwriter-abort-method.md) em vez disso.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Confira também

- [Interface ISymUnmanagedWriter](isymunmanagedwriter-interface.md)
