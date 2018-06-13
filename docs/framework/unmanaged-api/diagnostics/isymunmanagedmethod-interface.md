---
title: Interface ISymUnmanagedMethod
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod
helpviewer_keywords:
- ISymUnmanagedMethod interface [.NET Framework debugging]
ms.assetid: f204d74c-cc79-4092-83bb-60654be95649
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 728acc09f739fe567fca4a2571cbabf1ba8838a2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33427425"
---
# <a name="isymunmanagedmethod-interface"></a>Interface ISymUnmanagedMethod
Representa um método no repositório de símbolos. Essa interface fornece acesso a apenas os atributos relacionados ao símbolo de um método, em vez dos atributos de tipo.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método GetNamespace](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getnamespace-method.md)|Obtém o namespace no qual esse método é definido.|  
|[Método GetOffset](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getoffset-method.md)|Retorna o deslocamento dentro desse método que corresponde à posição especificada dentro de um documento.|  
|[Método GetParameters](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getparameters-method.md)|Obtém os parâmetros para este método.|  
|[Método GetRanges](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getranges-method.md)|Fornecido uma posição em um documento, retorna uma matriz de pares deslocamentos de início e término que correspondem aos intervalos de Microsoft intermediate language (MSIL) que abrange a posição dentro desse método.|  
|[Método GetRootScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getrootscope-method.md)|Obtém o escopo léxico raiz dentro desse método. Esse escopo abrange todo o método.|  
|[Método GetScopeFromOffset](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getscopefromoffset-method.md)|Obtém o escopo léxico mais delimitador dentro desse método que inclui o deslocamento especificado.|  
|[Método GetSequencePointCount](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getsequencepointcount-method.md)|Obtém a contagem de pontos de sequência dentro desse método.|  
|[Método GetSequencePoints](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getsequencepoints-method.md)|Obtém todos os pontos de sequência dentro desse método.|  
|[Método GetSourceStartEnd](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getsourcestartend-method.md)|Obtém as posições de documento de início e término para a fonte deste método.|  
|[Método GetToken](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-gettoken-method.md)|Retorna o token de metadados para esse método.|  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces do repositório de símbolos de diagnóstico](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
