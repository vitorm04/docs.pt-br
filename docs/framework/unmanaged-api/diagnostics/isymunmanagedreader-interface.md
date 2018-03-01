---
title: Interface ISymUnmanagedReader
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ISymUnmanagedReader
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader
helpviewer_keywords:
- ISymUnmanagedReader interface [.NET Framework debugging]
ms.assetid: aa3cc15d-058e-4e6f-b03e-39569646ba47
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9e8daea11292cb37deb8e956e6a666c14579fbfa
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedreader-interface"></a>Interface ISymUnmanagedReader
Representa um leitor de símbolo que fornece acesso a documentos, métodos e variáveis em um armazenamento de símbolo.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método GetDocument](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getdocument-method.md)|Localiza um documento.|  
|[Método GetDocuments](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getdocuments-method.md)|Retorna uma matriz de todos os documentos definidos no repositório de símbolos.|  
|[Método GetDocumentVersion](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getdocumentversion-method.md)|Obtém a versão especificada do documento especificado.|  
|[Método GetGlobalVariables](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getglobalvariables-method.md)|Retorna todas as variáveis globais.|  
|[Método GetMethod](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getmethod-method.md)|Obtém um método de leitor de símbolo, recebe um token de método.|  
|[Método GetMethodByVersion](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getmethodbyversion-method.md)|Obtém um método de leitor de símbolo, considerando um token de método e um número de versão de editar e copiar.|  
|[Método GetMethodFromDocumentPosition](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getmethodfromdocumentposition-method.md)|Retorna o método que contém o ponto de interrupção na posição fornecida em um documento.|  
|[Método GetMethodsFromDocumentPosition](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getmethodsfromdocumentposition-method.md)|Retorna uma matriz de métodos, cada qual contendo o ponto de interrupção na posição fornecida em um documento.|  
|[Método GetMethodVersion](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getmethodversion-method.md)|Obtém a versão do método.|  
|[Método GetNamespaces](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getnamespaces-method.md)|Obtém os namespaces definidos no escopo global esse armazenamento de símbolo.|  
|[Método GetSymAttribute](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getsymattribute-method.md)|Obtém um atributo personalizado com base no seu nome.|  
|[Método GetSymbolStoreFileName](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getsymbolstorefilename-method.md)|Fornece o nome de arquivo em disco do repositório de símbolos.|  
|[Método GetUserEntryPoint](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getuserentrypoint-method.md)|Retorna o método especificado como o ponto de entrada do usuário para o módulo, se houver.|  
|[Método GetVariables](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getvariables-method.md)|Retorna uma variável local não, dado seu pai e o nome.|  
|[Método Initialize](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-initialize-method.md)|Inicializa o leitor de símbolo com a interface de Importador de metadados que este leitor será associado, juntamente com o nome de arquivo do módulo.|  
|[Método ReplaceSymbolStore](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-replacesymbolstore-method.md)|Substitui o armazenamento de símbolo existente com um armazenamento de símbolo de delta.|  
|[Método UpdateSymbolStore](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-updatesymbolstore-method.md)|Atualiza o armazenamento de símbolo existente com um armazenamento de símbolo de delta.|  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces do repositório de símbolos de diagnóstico](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)  
 [Interface ISymUnmanagedReader2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-interface.md)
