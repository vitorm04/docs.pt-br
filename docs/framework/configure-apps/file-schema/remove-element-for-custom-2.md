---
title: <remove>elemento para NameValueSectionHandler e DictionarySectionHandler
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName/remove
helpviewer_keywords:
- remove Element
- <remove> Element
ms.assetid: 8d8af7f5-26c9-4db9-bbe4-b2a4e6949568
author: rpetrusha
ms.author: mairaw
ms.openlocfilehash: cd338ff2d613be31ab1524f6baed6107f803a688
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920944"
---
# <a name="remove-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a>\<Remover > elemento para NameValueSectionHandler e DictionarySectionHandler

Remove uma configuração definida anteriormente.

[ **\<configuration>** ](configuration-element.md)   
&nbsp;&nbsp;[ **\<sectionName>** ](custom-element-2.md)   
&nbsp;&nbsp;&nbsp;&nbsp; **\<remove>**

## <a name="syntax"></a>Sintaxe

```xml
<add remove="key" />
```

## <a name="attribute"></a>Atributo

|           | Descrição |
| --------- | ----------- |
| **key**   | Atributo obrigatório.<br><br>Especifica o nome da configuração a ser removida. |

## <a name="parent-element"></a>Elemento pai

| Elemento | Descrição |
| ------- | ------------|
| [elemento >name  **\<** ](custom-element-2.md) | Define as configurações para seções de configuração personalizadas que <xref:System.Configuration.NameValueSectionHandler> usam <xref:System.Configuration.DictionarySectionHandler> as classes e. |

## <a name="child-elements"></a>Elementos filho

Nenhum

## <a name="remarks"></a>Comentários

Você pode usar o  **\<elemento remover >** para remover as configurações de seu aplicativo que foram definidas em um nível superior na hierarquia do arquivo de configuração.

## <a name="example"></a>Exemplo

O exemplo a seguir mostra como usar o  **\<elemento remove >** em um arquivo de configuração de aplicativo para remover as configurações definidas anteriormente no arquivo de configuração do computador.

O código do arquivo de configuração de computador a seguir declara a seção `key1` `key2`  **\<myseção >** e adiciona duas configurações e, a ela:

```xml
<!-- Machine.config file -->
<configuration>
  <configSections>
    <section name="mySection" type="System.Configuration.NameValueSectionHandler,System" />
  </configSections>
  <mySection>
    <add key="key1" value="value1" />
    <add key="key2" value="value2" />
  </mySection>
</configuration>
```

O código do arquivo de configuração de aplicativo `key2` a seguir remove a configuração de  **\<myseção >** :

```xml
<!--Application configuration file -->
<configuration>
  <mySection>
    <remove key="key2" />
  </mySection>
</configuration>
```

## <a name="configuration-file"></a>arquivo de configuração

Esse elemento pode ser usado no arquivo de configuração do aplicativo, no arquivo de configuração do computador (*Machine. config*) e nos arquivos *Web. config* que não estão no nível do diretório do aplicativo.

## <a name="see-also"></a>Consulte também

- [Esquema do arquivo de configuração para o .NET Framework](index.md)
