---
title: Elementos da diretiva de tempo de execução
ms.date: 03/30/2017
ms.assetid: 3fe5848c-ecd7-4136-970b-8e48d250bde6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6bf692ff93a575858d1d1a89346611cb9c5957b3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59137807"
---
# <a name="runtime-directive-elements"></a>Elementos da diretiva de tempo de execução
O formato do arquivo de diretivas (rd.xml) do tempo de execução suporta os seguintes elementos de diretiva de tempo de execução. Consulte a [Referência do arquivo de configuração (rd.xml) de diretivas de tempo de execução](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md) para uma representação hierárquica.  
  
 [\<Application>](../../../docs/framework/net-native/application-element-net-native.md)  
 Aplica a política de reflexão de tempo de execução a todos os tipos usados pelo aplicativo e serve como um contêiner para tipos amplos de aplicativos e membros de tipo cujos metadados estão disponíveis para reflexão no tempo de execução. Este é um filho do elemento [\<Directives>](../../../docs/framework/net-native/directives-element-net-native.md).  
  
 [\<Assembly>](../../../docs/framework/net-native/assembly-element-net-native.md)  
 Aplica a política de tempo de execução a todos os tipos em um assembly. Esse é um filho dos elementos [\<Application>](../../../docs/framework/net-native/application-element-net-native.md) e [\<Library>](../../../docs/framework/net-native/library-element-net-native.md).  
  
 [\<AttributeImplies>](../../../docs/framework/net-native/attributeimplies-element-net-native.md)  
 Se sua diretiva recipiente [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) for um atributo, ela se aplicará à política de tempo de execução para elementos de código aos quais esse atributo é aplicado.  
  
 [\<Directives>](../../../docs/framework/net-native/directives-element-net-native.md)  
 O elemento raiz em todos os arquivos de diretivas de tempo de execução para [!INCLUDE[net_native](../../../includes/net-native-md.md)]. Seus elementos filhos são [\<Application>](../../../docs/framework/net-native/application-element-net-native.md) e [\<Library>](../../../docs/framework/net-native/library-element-net-native.md).  
  
 [\<Event>](../../../docs/framework/net-native/event-element-net-native.md)  
 Aplica a política de tempo de execução a um evento. Esse é um filho dos elementos [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) e [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md).  
  
 [\<Field>](../../../docs/framework/net-native/field-element-net-native.md)  
 Aplica a política de tempo de execução a um campo. Esse é um filho dos elementos [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) e [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md).  
  
 [\<GenericParameter>](../../../docs/framework/net-native/genericparameter-element-net-native.md)  
 Aplica a política de tempo de execução ao tipo de parâmetro de um tipo ou método genérico.  
  
 [\<ImpliesType>](../../../docs/framework/net-native/impliestype-element-net-native.md)  
 Aplica a política de tempo de execução a um tipo, se ela tiver sido aplicada ao tipo ou método recipiente.  
  
 [\<Library>](../../../docs/framework/net-native/library-element-net-native.md)  
 Aplica a política de tempo de execução a todos os tipos em um assembly. Esse é um filho dos elementos [\<Application>](../../../docs/framework/net-native/application-element-net-native.md) e [\<Library>](../../../docs/framework/net-native/library-element-net-native.md).  
  
 [\<Method>](../../../docs/framework/net-native/method-element-net-native.md)  
 Aplica a política de tempo de execução a um método. Esse é um filho dos elementos [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) e [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md).  
  
 [\<MethodInstantiation>](../../../docs/framework/net-native/methodinstantiation-element-net-native.md)  
 Aplica a diretiva de tempo de execução para um método genérico construído. Esse é um filho dos elementos [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) e [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md).  
  
 [\<Namespace>](../../../docs/framework/net-native/namespace-element-net-native.md)  
 Aplica a política de tempo de execução a todos os tipos em um namespace.  
  
 [\<Parameter>](../../../docs/framework/net-native/parameter-element-net-native.md)  
 Aplica a política de tempo de execução ao tipo do argumento passado para um método.  
  
 [\<Property>](../../../docs/framework/net-native/property-element-net-native.md)  
 Aplica a política de tempo de execução a uma propriedade. Esse é um filho dos elementos [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) e [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md).  
  
 [\<Subtypes>](../../../docs/framework/net-native/subtypes-element-net-native.md)  
 Aplica a política de tempo de execução a todas as classes herdadas do tipo recipiente.  
  
 [\<Type>](../../../docs/framework/net-native/type-element-net-native.md)  
 Aplica a política de tempo de execução a um tipo.  
  
 [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)  
 Aplica a política de tempo de execução a um tipo genérico construído.  
  
 [\<TypeParameter>](../../../docs/framework/net-native/typeparameter-element-net-native.md)  
 Aplica a política de tempo de execução ao tipo representado por um argumento <xref:System.Type> passado para um método.  
  
## <a name="see-also"></a>Consulte também

- [Referência do arquivo de configuração rd.xml](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
