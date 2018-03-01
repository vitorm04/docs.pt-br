---
title: Interface ISymUnmanagedDocument
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
- ISymUnmanagedDocument
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument
helpviewer_keywords:
- ISymUnmanagedDocument interface [.NET Framework debugging]
ms.assetid: 5c26b366-6e81-467c-9dd0-02dd26fee0a3
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 2e176679b4fdb4d0a2c5c4fbcbc09403e45f1ad1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanageddocument-interface"></a>Interface ISymUnmanagedDocument
Representa um documento referenciado por um repositório de símbolo. Um documento é definido por um localizador de recursos uniforme (URL) e um GUID de tipo de documento. Você pode localizar o documento, independentemente de como ele é armazenado usando a URL e GUID do tipo de documento. Você pode armazenar a origem do documento no repositório de símbolos e recuperá-lo por meio dessa interface.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método FindClosestLine](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-findclosestline-method.md)|Retorna a linha mais próxima que seja um ponto de sequência, de acordo com uma linha neste documento que pode ou não ser um ponto de sequência.|  
|[Método GetCheckSum](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getchecksum-method.md)|Obtém a soma de verificação.|  
|[Método GetCheckSumAlgorithmId](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getchecksumalgorithmid-method.md)|Obtém o identificador de algoritmo de soma de verificação ou retorna um GUID de zeros, se não houver nenhuma soma de verificação.|  
|[Método GetDocumentType](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getdocumenttype-method.md)|Obtém o tipo de documento deste documento.|  
|[Método GetLanguage](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getlanguage-method.md)|Obtém o identificador de idioma deste documento.|  
|[Método GetLanguageVendor](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getlanguagevendor-method.md)|Obtém o fornecedor do idioma deste documento.|  
|[Método GetSourceLength](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getsourcelength-method.md)|Obtém o comprimento, em bytes, da fonte incorporada.|  
|[Método GetSourceRange](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getsourcerange-method.md)|Retorna o intervalo especificado da fonte incorporada no buffer fornecido.|  
|[Método GetURL](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-geturl-method.md)|Retorna a URL deste documento.|  
|[Método HasEmbeddedSource](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-hasembeddedsource-method.md)|Retorna `true` se o documento tem origem inserida nos símbolos de depuração; caso contrário, retornará `false`.|  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces do repositório de símbolos de diagnóstico](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
