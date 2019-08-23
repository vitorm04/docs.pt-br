---
title: Elemento personalizado para SingleTagSectionHandler
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName
helpviewer_keywords:
- custom element
ms.assetid: e62056c6-b351-40eb-afc0-cc13fc44e45e
author: rpetrusha
ms.author: mairaw
ms.openlocfilehash: 8fae3673fe72d036802cb1a8366aaa2430c38884
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927495"
---
# <a name="custom-element-for-singletagsectionhandler"></a>Elemento personalizado para SingleTagSectionHandler

Define as configurações em uma seção de configuração personalizada que é definida \<por uma seção > elemento e <xref:System.Configuration.SingleTagSectionHandler> usa a classe.

[ **\<configuration>** ](configuration-element.md)   
&nbsp;&nbsp; *\<sectionName>*

## <a name="syntax"></a>Sintaxe

```xml
<sectionName key="value" key2="value2" ... />
```

## <a name="attributes"></a>Atributos

Atributos e valores de atributo são definidos pelo usuário.

## <a name="parent-element"></a>Elemento pai

|     | Descrição |
| --- | ----------- |
| [ **\<configuration>** ](configuration-element.md) | O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework. |

## <a name="child-elements"></a>Elementos filho

Nenhum

## <a name="remarks"></a>Comentários

[ **\<** ](configsections-element-for-configuration.md)  **O\<elemento SectionName >** é um elemento personalizado definido por uma [ **\<seção >** ](section-element.md) tag no elemento configSections >. O sistema de configuração retorna <xref:System.Collections.IDictionary> um objeto quando você <xref:System.Configuration.Configuration.GetSection(System.String)?displayProperty=nameWithType>chama.

## <a name="example"></a>Exemplo

O exemplo a seguir declara um elemento personalizado chamado  **\<sampleSection >** que contém <xref:System.Configuration.SingleTagSectionHandler> as configurações lidas pela classe:

```xml
<configuration>
  <configSections>
    <section name="sampleSection" 
             type="System.Configuration.SingleTagSectionHandler" />
  </configSections>
  <sampleSection setting1="Value1" 
                 setting2="value two" 
                 setting3="third value" />
</configuration>
```

## <a name="configuration-file"></a>arquivo de configuração

Esse elemento pode ser usado no arquivo de configuração do aplicativo, no arquivo de configuração do computador (*Machine. config*) e nos arquivos *Web. config* que não estão no nível do diretório do aplicativo.

## <a name="see-also"></a>Consulte também

- [Esquema do arquivo de configuração para o .NET Framework](index.md)
