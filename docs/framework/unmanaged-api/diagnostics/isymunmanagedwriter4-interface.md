---
title: Interface ISymUnmanagedWriter4
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 4af5e8c0-987d-405e-b934-8b9e70fcae6e
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f7ab7f06ba280675ca8349500e766364d30f9349
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="isymunmanagedwriter4-interface"></a>Interface ISymUnmanagedWriter4
Interface ISymUnmanagedWriter4.  
  
## <a name="syntax"></a>Sintaxe  
  
```idl  
[object,uuid(BC7E3F53-F458-4C23-9DBD-A189E6E96594),pointer_default(unique)]interface ISymUnmanagedWriter4 : ISymUnmanagedWriter3  
```  
  
## <a name="methods"></a>Métodos  
 Essa interface contém os seguintes métodos:  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método GetDebugInfoWithPadding](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter4-getdebuginfowithpadding-method.md)|Funciona da mesma forma [método GetDebugInfo](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-getdebuginfo-method.md) exceto que a cadeia de caracteres de caminho é preenchida com zeros após o caractere null de terminação para tornar os dados de cadeia de caracteres de tamanho fixo de `MAX_PATH`. O preenchimento é fornecido apenas se o comprimento da cadeia de caracteres de caminho em si é menor que `MAX_PATH`.<br /><br /> Isso torna mais fácil escrever ferramentas que arquivos de diferença PE.|  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces de armazenamento de símbolo de diagnóstico](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)  
 [Interface ISymUnmanagedWriter3](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-interface.md)
