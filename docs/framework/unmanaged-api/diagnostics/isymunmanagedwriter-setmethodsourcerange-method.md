---
title: Método ISymUnmanagedWriter::SetMethodSourceRange
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.SetMethodSourceRange
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::SetMethodSourceRange
helpviewer_keywords:
- SetMethodSourceRange method [.NET Framework debugging]
- ISymUnmanagedWriter::SetMethodSourceRange method [.NET Framework debugging]
ms.assetid: c698b86e-ace7-4b21-9549-f52d6a034959
topic_type:
- apiref
ms.openlocfilehash: 85e65f6a3ec13c2acc31b8f87dbe4b4476ffc2a5
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74427869"
---
# <a name="isymunmanagedwritersetmethodsourcerange-method"></a>Método ISymUnmanagedWriter::SetMethodSourceRange
Especifica os verdadeiros início e término de um método de dentro de um arquivo de origem. Use this method to specify the extent of a method independently of the sequence points that exist within the method.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT SetMethodSourceRange(  
    [in] ISymUnmanagedDocumentWriter  *startDoc,  
    [in] ULONG32                      startLine,  
    [in] ULONG32                      startColumn,  
    [in] ISymUnmanagedDocumentWriter  *endDoc,  
    [in] ULONG32                      endLine,  
    [in] ULONG32                      endColumn);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `startDoc`  
 [in] A pointer to the document containing the starting position.  
  
 `startLine`  
 [in] The starting line number.  
  
 `startColumn`  
 [in] The starting column.  
  
 `endDoc`  
 [in] A pointer to the document containing the ending position.  
  
 `endLine`  
 [in] The ending line number.  
  
 `endColumn`  
 [in] The ending column number.  
  
## <a name="return-value"></a>Valor retornado  
 S_OK if the method succeeds; otherwise, E_FAIL or some other error code.  
  
## <a name="requirements"></a>Requisitos  
 **Header:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Consulte também

- [Interface ISymUnmanagedWriter](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
