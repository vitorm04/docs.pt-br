---
title: Namespaces e DTDs em DOM
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 1e9b55c4-76ad-4f54-8d96-7ce4b4cf1e05
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bc8a1de8ab10eff88757720a35aa9668125cfbfa
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48582155"
---
# <a name="namespaces-and-dtds-in-the-dom"></a>Namespaces e DTDs em DOM
Definições de tipo (DTDs) de documento complicam suporte de namespace. Por exemplo, o seguinte XML contém os atributos padrões que contém dois-pontos em seus nomes.  
  
```xml  
<!ATTLIST item x:id CDATA #IMPLIED>  
```  
  
 Os seguintes são possíveis resoluções se esta compilação é permitida:  
  
-   `x:` é tratado como um prefixo de namespace, mas esse prefixo deve ser resolvível usando uma declaração de namespace de `xmlns:x` , que também deve existir em qualquer lugar no DTD. É um erro para mapear esse prefixo a algo diferente no documento de instância.  
  
-   `x:` é tratado como um prefixo de namespace, mas esse prefixo é sempre resolvido no contexto de elementos da instância. Isso significa que o prefixo pode realmente mapear ao namespace diferente de recurso uniformes (URIs), dependendo do escopo de namespace no qual o elemento de `item` aparece. Esse comportamento é mais previsível da resolução determinada no marcador anterior, mas tem outras ramificação complicadas porque ela requer os atributos padrão é materializado.  
  
-   O separador dois-pontos é ignorada porque ele é um DTD, e o nome do atributo é `x:y`, nenhum prefixo e nenhum URI de namespace.  
  
-   O separador dois-pontos no atributo padrão gerencie uma exceção, dizer que os dois-pontos nos nomes em um DTD não são suportados. Isso resulta em um comportamento previsível, mas mídia que você não pode carregar muitos do World Wide Web Consortium DTDs publicado (W3C).  
  
-   Quando a validação de DTD de um usuário, suporte de namespace para o documento inteiro é desativada. Isso torna possível carregar o W3C DTDs e resultados em um comportamento previsível.  
  
 O XML no Microsoft .NET Framework implementa a segunda opção para compatibilidade máxima com o W3C.  
  
## <a name="see-also"></a>Consulte também

- [DOM (Modelo de Objeto do Documento) de XML](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
