---
title: Elementos da diretiva de tempo de execução
ms.date: 03/30/2017
ms.assetid: 3fe5848c-ecd7-4136-970b-8e48d250bde6
ms.openlocfilehash: c900516382c8e526a6b0021bb2b681486283f3ab
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128166"
---
# <a name="runtime-directive-elements"></a>Elementos da diretiva de tempo de execução
O formato do arquivo de diretivas (rd.xml) do tempo de execução suporta os seguintes elementos de diretiva de tempo de execução. Consulte a [Referência do arquivo de configuração (rd.xml) de diretivas de tempo de execução](runtime-directives-rd-xml-configuration-file-reference.md) para uma representação hierárquica.  
  
 [\<Application>](application-element-net-native.md)  
 Aplica a política de reflexão de tempo de execução a todos os tipos usados pelo aplicativo e serve como um contêiner para tipos amplos de aplicativos e membros de tipo cujos metadados estão disponíveis para reflexão no tempo de execução. Este é um filho do elemento [\<Directives>](directives-element-net-native.md).  
  
 [\<Assembly>](assembly-element-net-native.md)  
 Aplica a política de tempo de execução a todos os tipos em um assembly. Esse é um filho dos elementos [\<Application>](application-element-net-native.md) e [\<Library>](library-element-net-native.md).  
  
 [\<AttributeImplies>](attributeimplies-element-net-native.md)  
 Se sua diretiva recipiente [\<Type>](type-element-net-native.md) for um atributo, ela se aplicará à política de tempo de execução para elementos de código aos quais esse atributo é aplicado.  
  
 [\<Directives>](directives-element-net-native.md)  
 O elemento raiz em cada arquivo de diretivas de tempo de execução para .NET Native. Seus elementos filhos são [\<Application>](application-element-net-native.md) e [\<Library>](library-element-net-native.md).  
  
 [\<Event>](event-element-net-native.md)  
 Aplica a política de tempo de execução a um evento. Esse é um filho dos elementos [\<Type>](type-element-net-native.md) e [\<TypeInstantiation>](typeinstantiation-element-net-native.md).  
  
 [\<Field>](field-element-net-native.md)  
 Aplica a política de tempo de execução a um campo. Esse é um filho dos elementos [\<Type>](type-element-net-native.md) e [\<TypeInstantiation>](typeinstantiation-element-net-native.md).  
  
 [\<GenericParameter>](genericparameter-element-net-native.md)  
 Aplica a política de tempo de execução ao tipo de parâmetro de um tipo ou método genérico.  
  
 [\<ImpliesType>](impliestype-element-net-native.md)  
 Aplica a política de tempo de execução a um tipo, se ela tiver sido aplicada ao tipo ou método recipiente.  
  
 [\<Library>](library-element-net-native.md)  
 Aplica a política de tempo de execução a todos os tipos em um assembly. Esse é um filho dos elementos [\<Application>](application-element-net-native.md) e [\<Library>](library-element-net-native.md).  
  
 [\<Method>](method-element-net-native.md)  
 Aplica a política de tempo de execução a um método. Esse é um filho dos elementos [\<Type>](type-element-net-native.md) e [\<TypeInstantiation>](typeinstantiation-element-net-native.md).  
  
 [\<MethodInstantiation>](methodinstantiation-element-net-native.md)  
 Aplica a diretiva de tempo de execução para um método genérico construído. Esse é um filho dos elementos [\<Type>](type-element-net-native.md) e [\<TypeInstantiation>](typeinstantiation-element-net-native.md).  
  
 [\<Namespace>](namespace-element-net-native.md)  
 Aplica a política de tempo de execução a todos os tipos em um namespace.  
  
 [\<Parameter>](parameter-element-net-native.md)  
 Aplica a política de tempo de execução ao tipo do argumento passado para um método.  
  
 [\<Property>](property-element-net-native.md)  
 Aplica a política de tempo de execução a uma propriedade. Esse é um filho dos elementos [\<Type>](type-element-net-native.md) e [\<TypeInstantiation>](typeinstantiation-element-net-native.md).  
  
 [\<Subtypes>](subtypes-element-net-native.md)  
 Aplica a política de tempo de execução a todas as classes herdadas do tipo recipiente.  
  
 [\<Type>](type-element-net-native.md)  
 Aplica a política de tempo de execução a um tipo.  
  
 [\<TypeInstantiation>](typeinstantiation-element-net-native.md)  
 Aplica a política de tempo de execução a um tipo genérico construído.  
  
 [\<TypeParameter>](typeparameter-element-net-native.md)  
 Aplica a política de tempo de execução ao tipo representado por um argumento <xref:System.Type> passado para um método.  
  
## <a name="see-also"></a>Consulte também

- [Referência do arquivo de configuração rd.xml](runtime-directives-rd-xml-configuration-file-reference.md)
