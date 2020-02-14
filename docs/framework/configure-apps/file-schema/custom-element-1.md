---
title: Elemento personalizado para SingleTagSectionHandler
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName
helpviewer_keywords:
- custom element
ms.assetid: e62056c6-b351-40eb-afc0-cc13fc44e45e
ms.openlocfilehash: 1d0431085a04d3fb817dfe0883779acc4d693084
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77214782"
---
# <a name="custom-element-for-singletagsectionhandler"></a>Elemento personalizado para SingleTagSectionHandler

Define as configurações em uma seção de configuração personalizada que é definida por um \<seção > elemento e usa a classe <xref:System.Configuration.SingleTagSectionHandler>.

[ **\<configuration>** ](configuration-element.md)   
&nbsp;&nbsp; *\<sectionname >*

## <a name="syntax"></a>Sintaxe

```xml
<sectionName key="value" key2="value2" ... />
```

## <a name="attributes"></a>Atributos

Atributos e valores de atributo são definidos pelo usuário.

## <a name="parent-element"></a>Elemento pai

|     | DESCRIÇÃO |
| --- | ----------- |
| [ **\<configuration>** ](configuration-element.md) | O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework. |

## <a name="child-elements"></a>Elementos filho

Nenhum

## <a name="remarks"></a>Comentários

O elemento **\<sectionname >** é um elemento personalizado definido por uma [**seção\<>** ](section-element.md) marca no elemento [ **\<configSections >** ](configsections-element-for-configuration.md) . O sistema de configuração retorna um objeto <xref:System.Collections.IDictionary> quando você chama <xref:System.Configuration.Configuration.GetSection(System.String)?displayProperty=nameWithType>.

## <a name="example"></a>Exemplo

O exemplo a seguir declara um elemento personalizado chamado **\<sampleSection >** que contém as configurações lidas pela classe <xref:System.Configuration.SingleTagSectionHandler>:

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

## <a name="configuration-file"></a>Arquivo de configuração

Esse elemento pode ser usado no arquivo de configuração do aplicativo, no arquivo de configuração do computador (*Machine. config*) e nos arquivos *Web. config* que não estão no nível do diretório do aplicativo.

## <a name="see-also"></a>Confira também

- [Esquema do arquivo de configuração para o .NET Framework](index.md)
