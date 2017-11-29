---
title: Interface ISymUnmanagedWriter5
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 15b8526e-4f5d-475c-a1e3-d8b2d145c879
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c5ac543ad98cc14382f0fb6d0d04fafa7136136e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="isymunmanagedwriter5-interface"></a>Interface ISymUnmanagedWriter5
Interface ISymUnmanagedWriter5.  
  
## <a name="syntax"></a>Sintaxe  
  
```idl  
[object,uuid(DCF7780D-BDE9-45DF-ACFE-21731A32000C),pointer_default(unique)]interface ISymUnmanagedWriter5 : ISymUnmanagedWriter4  
```  
  
## <a name="methods"></a>Métodos  
 Essa interface contém os seguintes métodos:  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método CloseMapTokensToSourceSpans](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-closemaptokenstosourcespans-method.md)|Feche a seção de dados personalizada especial para informações de mapeamento de extensão de token para a fonte. Depois de fechado, não há mais informações de mapeamento podem ser adicionadas.|  
|[Método MapTokenToSourceSpan](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-maptokentosourcespan-method.md)|Mapeia o token de metadados fornecidos para a linha de origem span no arquivo de origem especificado.<br /><br /> Deve ser chamado entre as chamadas para [método OpenMapTokensToSourceSpans](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-openmaptokenstosourcespans-method.md) e [método CloseMapTokensToSourceSpans](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-closemaptokenstosourcespans-method.md).|  
|[Método OpenMapTokensToSourceSpans](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-openmaptokenstosourcespans-method.md)|Abra uma seção de dados personalizada especial para emitir informações de mapeamento de span da fonte de token em. Abrir esta seção quando um método já estiver aberto, ou vice-versa, é um erro.|  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces de armazenamento de símbolo de diagnóstico](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)  
 [Interface ISymUnmanagedWriter4](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter4-interface.md)
