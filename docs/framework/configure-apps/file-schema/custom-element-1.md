---
title: Elemento personalizado para SingleTagSectionHandler
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName
helpviewer_keywords:
- custom element
ms.assetid: e62056c6-b351-40eb-afc0-cc13fc44e45e
ms.openlocfilehash: 0d765a9789ad566428b1fbda6c0863b10b98c363
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/27/2020
ms.locfileid: "80345070"
---
# <a name="custom-element-for-singletagsectionhandler"></a>Elemento personalizado para SingleTagSectionHandler

Define configurações em uma seção de \<configuração personalizada definida <xref:System.Configuration.SingleTagSectionHandler> por uma seção> elemento e usa a classe.

configuração &nbsp; &nbsp; [** \<>**](configuration-element.md) * \<seçãoNome>*

## <a name="syntax"></a>Sintaxe

```xml
<sectionName key="value" key2="value2" />
```

## <a name="attributes"></a>Atributos

Atributos e valores de atributos são definidos pelo usuário.

## <a name="parent-element"></a>Elemento pai

|     | Descrição |
| --- | ----------- |
| [**\<>de configuração**](configuration-element.md) | O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework. |

## <a name="child-elements"></a>Elementos filho

Nenhum

## <a name="remarks"></a>Comentários

O ** \<** elemento sectionName>é um elemento personalizado definido por uma [** \<seção>**](section-element.md) tag no [** \<elemento>configSeções.**](configsections-element-for-configuration.md) O sistema de <xref:System.Collections.IDictionary> configuração <xref:System.Configuration.Configuration.GetSection(System.String)?displayProperty=nameWithType>retorna um objeto quando você chama .

## <a name="example"></a>Exemplo

O exemplo a seguir declara um elemento personalizado chamado <xref:System.Configuration.SingleTagSectionHandler> ** \<sampleSection>** que contém configurações lidas pela classe:

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

Esse elemento pode ser usado no arquivo de configuração do aplicativo, no arquivo de configuração da máquina *(Machine.config)* e nos arquivos *Web.config* que não estão no nível do diretório do aplicativo.

## <a name="see-also"></a>Confira também

- [Esquema de arquivo de configuração para o Framework .NET](index.md)
