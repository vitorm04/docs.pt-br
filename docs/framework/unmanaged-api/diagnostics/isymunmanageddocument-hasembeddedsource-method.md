---
title: Método ISymUnmanagedDocument::HasEmbeddedSource
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument.HasEmbeddedSource
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::HasEmbeddedSource
helpviewer_keywords:
- HasEmbeddedSource method [.NET Framework debugging]
- ISymUnmanagedDocument::HasEmbeddedSource method [.NET Framework debugging]
ms.assetid: 385fc4d3-365c-4645-b7b0-6c4c5344b79f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1d6c79be95ff80c8de9b07cb33be46a5f5db22b1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59094262"
---
# <a name="isymunmanageddocumenthasembeddedsource-method"></a>Método ISymUnmanagedDocument::HasEmbeddedSource
Retorna `true` se o documento tem o código-fonte inserido em símbolos de depuração; caso contrário, retornará `false`.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT HasEmbeddedSource(  
   [out, retval]  BOOL  *pRetVal);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pRetVal`  
 [out] Um ponteiro para uma variável que indica se o documento tem incorporado os símbolos de depuração de código-fonte.  
  
## <a name="return-value"></a>Valor de retorno  
 S_OK se o método for bem-sucedido.  
  
## <a name="see-also"></a>Consulte também

- [Interface ISymUnmanagedDocument](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
