---
title: Método ISymUnmanagedWriter5::OpenMapTokensToSourceSpans
ms.date: 03/30/2017
ms.assetid: 93ad2517-b0dc-464c-8688-a58a30eda18d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5d3bc8b00b568f96cd55b7811f310d34c1ff700d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="isymunmanagedwriter5openmaptokenstosourcespans-method"></a>Método ISymUnmanagedWriter5::OpenMapTokensToSourceSpans
Abra uma seção de dados personalizada especial para emitir informações de mapeamento de span da fonte de token em. Abrir esta seção quando um método já estiver aberto, ou vice-versa, é um erro.  
  
## <a name="syntax"></a>Sintaxe  
  
```idl  
HRESULT OpenMapTokensToSourceSpans();  
```  
  
## <a name="return-value"></a>Valor de retorno  
 Retorna `HRESULT`.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Consulte também  
 [Interface ISymUnmanagedWriter5](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-interface.md)
