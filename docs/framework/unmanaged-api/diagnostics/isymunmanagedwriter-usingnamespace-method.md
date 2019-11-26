---
title: Método ISymUnmanagedWriter::UsingNamespace
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.UsingNamespace
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::UsingNamespace
helpviewer_keywords:
- UsingNamespace method [.NET Framework debugging]
- ISymUnmanagedWriter::UsingNamespace method [.NET Framework debugging]
ms.assetid: 8d746e0a-d158-4983-88da-db0a0856bc0b
topic_type:
- apiref
ms.openlocfilehash: cb0af78092822875204f45ec3dca1484e5b5fc90
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74427462"
---
# <a name="isymunmanagedwriterusingnamespace-method"></a>Método ISymUnmanagedWriter::UsingNamespace
Specifies that the given fully qualified namespace name is being used within the currently open lexical scope. The namespace will be used within all scopes that inherit from the currently open scope. Closing the current scope will also stop the use of the namespace.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT UsingNamespace(  
    [in] const WCHAR *fullName);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `fullName`  
 [in] A pointer to the fully qualified name of the namespace.  
  
## <a name="return-value"></a>Valor retornado  
 S_OK if the method succeeds; otherwise, E_FAIL or some other error code.  
  
## <a name="requirements"></a>Requisitos  
 **Header:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Consulte também

- [Interface ISymUnmanagedWriter](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
