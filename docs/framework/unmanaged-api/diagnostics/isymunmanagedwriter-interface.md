---
title: Interface ISymUnmanagedWriter
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter
helpviewer_keywords:
- ISymUnmanagedWriter interface [.NET Framework debugging]
ms.assetid: 7d6733ec-f081-4166-bc17-de09e16dc304
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4ac95cd5b79a2e1762fa9adf29d4d7926ab4ab7a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59150573"
---
# <a name="isymunmanagedwriter-interface"></a>Interface ISymUnmanagedWriter
Representa um gravador de símbolo e fornece métodos para definir pontos de sequência, documentos, escopos léxicos e variáveis.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método Abort](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-abort-method.md)|Fecha o gravador de símbolo sem confirmar os símbolos para o repositório de símbolos.|  
|[Método Close](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-close-method.md)|Fecha o gravador de símbolo depois de confirmar os símbolos para o repositório de símbolos.|  
|[Método CloseMethod](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closemethod-method.md)|Fecha o método atual. Quando um método é fechado, nenhuma mais símbolos podem ser definidos dentro dele.|  
|[Método CloseNamespace](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closenamespace-method.md)|Fecha abriu mais recentemente namespace.|  
|[Método CloseScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closescope-method.md)|Fecha o escopo léxico atual.|  
|[Método DefineConstant](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-defineconstant-method.md)|Define um nome para um valor constante.|  
|[Método DefineDocument](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-definedocument-method.md)|Define um documento de origem.|  
|[Método DefineField](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-definefield-method.md)|Define uma única variável que não está dentro de um método.|  
|[Método DefineGlobalVariable](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-defineglobalvariable-method.md)|Define uma única variável global.|  
|[Método DefineLocalVariable](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-definelocalvariable-method.md)|Define uma única variável no escopo léxico atual.|  
|[Método DefineParameter](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-defineparameter-method.md)|Define um único parâmetro no método atual.|  
|[Método DefineSequencePoints](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-definesequencepoints-method.md)|Define um grupo de pontos de sequência dentro do método atual.|  
|[Método GetDebugInfo](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-getdebuginfo-method.md)|Retorna as informações necessárias para que um compilador gravar a entrada de diretório de depuração no cabeçalho de arquivo executável (PE) da portátil.|  
|[Método Initialize](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-initialize-method.md)|Define a interface do emissor de metadados com o qual este gravador será associado e define o nome do arquivo de saída para o qual os símbolos de depuração serão gravados.|  
|[Método Initialize2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-initialize2-method.md)|Define a interface do emissor de metadados com o qual este gravador serão associado, define o nome do arquivo de saída para o qual os símbolos de depuração serão gravados e define o local final do arquivo de banco de dados (PDB) do programa.|  
|[Método OpenMethod](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md)|Abre um método em qual símbolo informações são emitidas.|  
|[Método OpenNamespace](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-opennamespace-method.md)|Abre um novo namespace.|  
|[Método OpenScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openscope-method.md)|Abre um novo escopo léxico no método atual.|  
|[Método RemapToken](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-remaptoken-method.md)|Notifica o gravador de símbolo que um token de metadados foi remapeado, pois os metadados foi emitido.|  
|[Método SetMethodSourceRange](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setmethodsourcerange-method.md)|Especifica os verdadeiros início e término de um método de dentro de um arquivo de origem.|  
|[Método SetScopeRange](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setscoperange-method.md)|Define o intervalo de deslocamento do escopo léxico especificado.|  
|[Método SetSymAttribute](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setsymattribute-method.md)|Define um atributo personalizado com base em seu nome.|  
|[Método SetUserEntryPoint](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setuserentrypoint-method.md)|Especifica o método definido pelo usuário que é o ponto de entrada para esse módulo.|  
|[Método UsingNamespace](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-usingnamespace-method.md)|Especifica que o nome totalmente qualificado do namespace fornecido está sendo usado dentro do escopo léxico aberto no momento.|  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Consulte também

- [Interfaces do repositório de símbolos de diagnóstico](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [Interface ISymUnmanagedWriter2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-interface.md)
- [Interface ISymUnmanagedWriter3](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-interface.md)
