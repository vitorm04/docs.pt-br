---
title: Elemento <clear> para <configSections>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/clear
helpviewer_keywords:
- clear Element
- <clear> Element
ms.assetid: 77f1d761-ff45-4001-8f36-3a3e5c41fa63
ms.openlocfilehash: 66abd7f057bc6d060e50a889a945281d07c97592
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155421"
---
# <a name="clear-element-for-configsections"></a>\<elemento> \<clara para configuraçõesSeções>

Limpa todas as seções e grupos de seção previamente definidos.

&nbsp; &nbsp; &nbsp; &nbsp; ** \<** [** \<configuração>**](configuration-element.md) &nbsp; &nbsp;configSeções>>claras [** \<**](configsections-element-for-configuration.md)

## <a name="syntax"></a>Sintaxe

```xml
<clear/>
```

## <a name="attribute"></a>Atributo

|           | Descrição |
| --------- | ----------- |
| **name**  | Atributo obrigatório.<br><br>Especifica o nome da seção ou do grupo de seção a ser removido. |

## <a name="parent-element"></a>Elemento pai

|     | Descrição |
| --- | ----------- |
| [** \<configSeções>** Elemento](configsections-element-for-configuration.md) | Contém seção de configuração e declarações de namespace. |

## <a name="child-elements"></a>Elementos filho

Nenhum

## <a name="remarks"></a>Comentários

O elemento ** \<clear>** remove todas as seções e grupos de seção do seu aplicativo que foram definidos anteriormente no arquivo de configuração atual ou em um nível mais alto na hierarquia do arquivo de configuração.

## <a name="example"></a>Exemplo

Este exemplo define um arquivo de configuração da máquina ** \<** e um arquivo de configuração de aplicativo e mostra como usar o elemento clear>em um arquivo de configuração de aplicativo para limpar seções definidas anteriormente no arquivo de configuração da máquina.

O código de arquivo de configuração da máquina a seguir declara duas seções, ** \<sampleSection>** e ** \<outra>SampleSection **, que são lidas antes do arquivo de configuração do aplicativo:

```xml
<!-- Machine.config file -->
<configuration>
  <configSections>
    <section name="sampleSection"
             type="System.Configuration.SingleTagSectionHandler" />
    <section name="anotherSampleSection"
             type="System.Configuration.NameValueSectionHandler" />
  </configSections>
  <sampleSection setting1="Value1"
                 setting2="value two"
                 setting3="third value" />
</configuration>
```

O código de arquivo de configuração do aplicativo a seguir limpa todas as seções declaradas anteriormente. O aplicativo não pode usar ou recuperar configurações em qualquer uma das seções que foram declaradas no arquivo de configuração da máquina. No entanto, ele pode usar configurações de ** \<outra Seção>** porque vem depois do ** \<** elemento>claro.

```xml
<!-- Application configuration file -->
<configuration>
  <configSections>
    <clear/>
    <section name="anotherSection"
             type="System.Configuration.NameValueSectionHandler" />
  </configSections>
  <anotherSection setting1="Value1"
                 setting2="value two"
                 setting3="third value" />
</configuration>
```

## <a name="configuration-file"></a>Arquivo de configuração

Esse elemento pode ser usado no arquivo de configuração do aplicativo, no arquivo de configuração da máquina *(Machine.config)* e nos arquivos *Web.config* que não estão no nível do diretório do aplicativo.

## <a name="see-also"></a>Confira também

- [Esquema de arquivo de configuração para o Framework .NET](index.md)
