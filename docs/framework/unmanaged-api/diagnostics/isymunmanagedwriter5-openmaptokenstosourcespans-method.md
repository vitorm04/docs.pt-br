---
title: Método ISymUnmanagedWriter5::OpenMapTokensToSourceSpans
ms.date: 03/30/2017
ms.assetid: 93ad2517-b0dc-464c-8688-a58a30eda18d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 60c1984e6193481efdaaeb82a2bc025aef67a33f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54534428"
---
# <a name="isymunmanagedwriter5openmaptokenstosourcespans-method"></a>Método ISymUnmanagedWriter5::OpenMapTokensToSourceSpans
Abra uma seção especial de dados personalizados para emitir informações de mapeamento de span da fonte de token em. Abrir esta seção quando um método já está aberto, ou vice-versa, é um erro.  
  
## <a name="syntax"></a>Sintaxe  
  
```idl  
HRESULT OpenMapTokensToSourceSpans();  
```  
  
## <a name="return-value"></a>Valor de retorno  
 Retorna `HRESULT`.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Consulte também
- [Interface ISymUnmanagedWriter5](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-interface.md)
