---
title: Interfaces de armazenamento de símbolo de diagnóstico
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], debugging
- diagnostics symbol store interfaces [.NET Framework]
- interfaces [.NET Framework], diagnostics symbol store
- unmanaged interfaces [.NET Framework], diagnostics symbol store
- debugging interfaces [.NET Framework]
- interfaces [.NET Framework debugging]
ms.assetid: f96987d5-e6a5-478b-ac5e-302e16545cce
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6fca7359888b8b73b2e1cf709ab708d71abf0db6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="diagnostics-symbol-store-interfaces"></a>Interfaces de armazenamento de símbolo de diagnóstico
Este tópico descreve as interfaces não gerenciadas que permitem que um compilador para gerar informações de símbolo para uso por um depurador.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Interface IBindingDisplay](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-interface.md)  
 Fornece métodos que exibem as informações de associação atuais sobre o aplicativo em execução.  
  
 [Interface IDebugAutoAttach](../../../../docs/framework/unmanaged-api/diagnostics/idebugautoattach-interface.md)  
 Define a interface para anexar um depurador de servidor chamado automaticamente.  
  
 [Interface INotifyConnection2](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-interface.md)  
 Declara os métodos para registrar e cancelar o registro de uma fonte de conexão de notificação.  
  
 [Interface INotifySink2](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)  
 Declara os métodos de notificação de coletor.  
  
 [Interface INotifySource2](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-interface.md)  
 Declara um método para definir filtros de notificação.  
  
 [Interface ISymENCUnmanagedMethod](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-interface.md)  
 Fornece informações para o recurso Editar e continuar.  
  
 [Interface ISymUnmanagedAsyncMethod](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-interface.md)  
 Essa interface é o complemento de leitura para [ISymUnmanagedAsyncMethodPropertiesWriter Interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md).  
  
 [Interface ISymUnmanagedAsyncMethodPropertiesWriter](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md)  
 Permite a definição das informações de método assíncrono opcional por símbolo do método. Deve usar um método aberto (ou seja, entre as chamadas para o [método OpenMethod](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md)e [método CloseMethod](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closemethod-method.md)).  
  
 [Interface ISymUnmanagedBinder](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md)  
 Representa um associador de símbolo para código não gerenciado.  
  
 [Interface ISymUnmanagedBinder2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-interface.md)  
 Representa um associador de símbolo para código não gerenciado e estende o `ISymUnmanagedBinder` interface.  
  
 [Interface ISymUnmanagedBinder3](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-interface.md)  
 Representa um associador de símbolo para código não gerenciado e estende o `ISymUnmanagedBinder` interface.  
  
 [Interface ISymUnmanagedConstant](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-interface.md)  
 Fornece acesso às constantes não gerenciados.  
  
 [Interface ISymUnmanagedDispose](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddispose-interface.md)  
 Libera recursos não gerenciados.  
  
 [Interface ISymUnmanagedDocument](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)  
 Representa um documento referenciado por um repositório de símbolos.  
  
 [Interface ISymUnmanagedDocumentWriter](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocumentwriter-interface.md)  
 Fornece métodos para gravar em um documento referenciado por um repositório de símbolos.  
  
 [Interface ISymUnmanagedENCUpdate](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-interface.md)  
 Fornece métodos para o recurso Editar e continuar.  
  
 [Interface ISymUnmanagedMethod](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)  
 Representa um método no repositório de símbolos.  
  
 [Interface ISymUnmanagedNamespace](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagednamespace-interface.md)  
 Representa um namespace.  
  
 [Interface ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)  
 Representa um leitor de símbolo que fornece acesso a documentos, métodos e variáveis em um armazenamento de símbolo.  
  
 [Interface ISymUnmanagedReader2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-interface.md)  
 Obtém um método de leitor de símbolo dado um token de método e um número de versão de editar e copiar.  
  
 [Interface ISymUnmanagedReaderSymbolSearchInfo](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreadersymbolsearchinfo-interface.md)  
 Fornece métodos que obtêm informações de pesquisa do símbolo.  
  
 [Interface ISymUnmanagedScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)  
 Representa um escopo léxico dentro de um método.  
  
 [Interface ISymUnmanagedScope2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope2-interface.md)  
 Representa um escopo léxico dentro de um método e estende o `ISymUnmanagedScope` interface com métodos que obtêm informações sobre constantes definidas dentro do escopo.  
  
 [Interface ISymUnmanagedSourceServerModule](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsourceservermodule-interface.md)  
 Fornece dados de servidor de origem para um módulo.  
  
 [Interface ISymUnmanagedSymbolSearchInfo](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-interface.md)  
 Fornece métodos que obtêm informações sobre o caminho de pesquisa.  
  
 [Interface ISymUnmanagedVariable](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)  
 Representa uma variável, como um parâmetro, uma variável local ou um campo.  
  
 [Interface ISymUnmanagedWriter](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)  
 Representa um gravador de símbolo e fornece métodos para definir documentos, pontos de sequência, escopos de léxicos e variáveis.  
  
 [Interface ISymUnmanagedWriter2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-interface.md)  
 Representa um gravador de símbolo e fornece métodos para definir documentos, pontos de sequência, escopos de léxicos e variáveis. Estende o `ISymUnmanagedWriter` interface.  
  
 [Interface ISymUnmanagedWriter3](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-interface.md)  
 Representa um gravador de símbolo e fornece métodos para definir documentos, pontos de sequência, escopos de léxicos e variáveis. Estende o `ISymUnmanagedWriter` interface.  
  
 [Interface ISymUnmanagedWriter4](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter4-interface.md)  
 Interface ISymUnmanagedWriter4.  
  
 [Interface ISymUnmanagedWriter5](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-interface.md)  
 Interface ISymUnmanagedWriter5.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Enumerações do repositório de símbolos de diagnóstico](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-enumerations.md)  
  
 [Estruturas de repositório de símbolos de diagnóstico](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-structures.md)  
  
 [Depuração](../../../../docs/framework/unmanaged-api/debugging/index.md)
