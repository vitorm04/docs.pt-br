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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d057201c7d7bec3070027bb1d9de62735d583cf6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33428996"
---
# <a name="isymunmanagedwritersetmethodsourcerange-method"></a>Método ISymUnmanagedWriter::SetMethodSourceRange
Especifica os verdadeiros início e término de um método de dentro de um arquivo de origem. Use esse método para especificar a extensão de um método independentemente dos pontos de sequência que existe dentro do método.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT SetMethodSourceRange(  
    [in] ISymUnmanagedDocumentWriter  *startDoc,  
    [in] ULONG32                      startLine,  
    [in] ULONG32                      startColumn,  
    [in] ISymUnmanagedDocumentWriter  *endDoc,  
    [in] ULONG32                      endLine,  
    [in] ULONG32                      endColumn);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `startDoc`  
 [in] Um ponteiro para o documento que contém a posição inicial.  
  
 `startLine`  
 [in] O número de linha inicial.  
  
 `startColumn`  
 [in] A coluna de início.  
  
 `endDoc`  
 [in] Um ponteiro para o documento que contém a posição final.  
  
 `endLine`  
 [in] O número de linha final.  
  
 `endColumn`  
 [in] O número de coluna final.  
  
## <a name="return-value"></a>Valor de retorno  
 S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Consulte também  
 [Interface ISymUnmanagedWriter](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
