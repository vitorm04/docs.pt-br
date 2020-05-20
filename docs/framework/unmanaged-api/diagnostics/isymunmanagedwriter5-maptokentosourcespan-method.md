---
title: Método ISymUnmanagedWriter5::MapTokenToSourceSpan
ms.date: 03/30/2017
ms.assetid: d0fbbf61-71c6-4fb1-8c9f-d619ca5d7d68
ms.openlocfilehash: f5898cab08f332314fb33684399dcb4f2ff71cc7
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83609450"
---
# <a name="isymunmanagedwriter5maptokentosourcespan-method"></a>Método ISymUnmanagedWriter5::MapTokenToSourceSpan
Mapeia o token de metadados fornecido para o span de linha de origem fornecido no arquivo de origem especificado.  
  
 Deve ser chamado entre as chamadas para o [método OpenMapTokensToSourceSpans](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-openmaptokenstosourcespans-method.md) e o [método CloseMapTokensToSourceSpans](isymunmanagedwriter5-closemaptokenstosourcespans-method.md).  
  
## <a name="syntax"></a>Sintaxe  
  
```idl  
HRESULT MapTokenToSourceSpan(    [in] mdToken token,    [in] ISymUnmanagedDocumentWriter* document,    [in] ULONG32 line,    [in] ULONG32 column,    [in] ULONG32 endLine,    [in] ULONG32 endColumn);  
```  
  
## <a name="parameters"></a>Parâmetros  
  
|Parâmetro|Descrição|  
|---------------|-----------------|  
|`token`||  
|`document`||  
|`line`||  
|`column`||  
|`endLine`||  
|`endColumn`||  
  
## <a name="return-value"></a>Valor retornado  
 Retorna `HRESULT`.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Confira também

- [Interface ISymUnmanagedWriter5](isymunmanagedwriter5-interface.md)
