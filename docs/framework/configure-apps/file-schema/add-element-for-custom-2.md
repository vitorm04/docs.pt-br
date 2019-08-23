---
title: <add>elemento para NameValueSectionHandler e DictionarySectionHandler
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName/add
helpviewer_keywords:
- add Element
- <add> Element
ms.assetid: 0d4ddb53-eb2b-49c0-9c33-a8dec5c39b46
author: rpetrusha
ms.author: mairaw
ms.openlocfilehash: ec6d5045580e887de5f05a05c8f39fa62c6e3f2e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69921319"
---
# <a name="add-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a>\<Adicionar > elemento para NameValueSectionHandler e DictionarySectionHandler

Adiciona configurações de aplicativo personalizadas. Cada marca Add > contém um par chave/valor.  **\<**

[ **\<configuration>** ](configuration-element.md)   
&nbsp;&nbsp;[ **\<sectionName>** ](custom-element-2.md)   
&nbsp;&nbsp;&nbsp;&nbsp; **\<add>**

## <a name="syntax"></a>Sintaxe

```xml
<add key="key" value="value" />
```

## <a name="attributes"></a>Atributos

| Atributo | Descrição |
| --------- | ----------- |
| **key**   | Atributo obrigatório.<br><br>Especifica o nome da configuração. |
| **value** | Atributo obrigatório.<br><br>Especifica o valor da configuração. |

## <a name="parent-element"></a>Elemento pai

| Elemento | Descrição |
| ------- | ------------|
| [elemento >name  **\<** ](custom-element-2.md) | Define as configurações para seções de configuração personalizadas que <xref:System.Configuration.NameValueSectionHandler> usam <xref:System.Configuration.DictionarySectionHandler> as classes e. |

## <a name="child-elements"></a>Elementos filho

Nenhum

## <a name="example"></a>Exemplo

O exemplo a seguir mostra como definir uma seção de configuração personalizada e usar o  **\<elemento add >** para colocar as configurações na seção:

```xml
<configuration>
  <configSections>
    <section name="dictionarySample" type="System.Configuration.DictionarySectionHandler,System" />
  </configSections>
  <dictionarySample>
    <add key="myKey" value="myValue" />
  </dictionarySample>
</configuration>
```

## <a name="configuration-file"></a>arquivo de configuração

Esse elemento pode ser usado no arquivo de configuração do aplicativo, no arquivo de configuração do computador (*Machine. config*) e nos arquivos *Web. config* que não estão no nível do diretório do aplicativo.

## <a name="see-also"></a>Consulte também

- [Esquema do arquivo de configuração para o .NET Framework](index.md)
