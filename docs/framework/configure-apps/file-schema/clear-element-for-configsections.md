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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79155421"
---
# <a name="clear-element-for-configsections"></a>Elemento \<clear> para \<configSections>

Limpa todas as seções e grupos de seções definidos anteriormente.

[**\<configuration>**](configuration-element.md) &nbsp;&nbsp;[**\<configSections>**](configsections-element-for-configuration.md) &nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**

## <a name="syntax"></a>Sintaxe

```xml
<clear/>
```

## <a name="attribute"></a>Atributo

|           | Descrição |
| --------- | ----------- |
| **name**  | Atributo obrigatório.<br><br>Especifica o nome da seção ou do grupo de seções a ser removido. |

## <a name="parent-element"></a>Elemento pai

|     | Descrição |
| --- | ----------- |
| [**\<configSections>** Elementos](configsections-element-for-configuration.md) | Contém as declarações de namespace e seção de configuração. |

## <a name="child-elements"></a>Elementos filho

Nenhum

## <a name="remarks"></a>Comentários

O **\<clear>** elemento remove todas as seções e grupos de seção do aplicativo que foram definidos anteriormente no arquivo de configuração atual ou em um nível superior na hierarquia do arquivo de configuração.

## <a name="example"></a>Exemplo

Este exemplo define um arquivo de configuração de computador e um arquivo de configuração de aplicativo e mostra como usar o **\<clear>** elemento em um arquivo de configuração de aplicativo para limpar as seções definidas anteriormente no arquivo de configuração de computador.

O código do arquivo de configuração do computador a seguir declara duas seções **\<sampleSection>** e **\<anotherSampleSection>** , que são lidas antes do arquivo de configuração do aplicativo:

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

O código do arquivo de configuração de aplicativo a seguir limpa todas as seções declaradas anteriormente. O aplicativo não pode usar ou recuperar as configurações em nenhuma das seções que foram declaradas no arquivo de configuração da máquina. No entanto, ele pode usar configurações de **\<anotherSection>** porque vem após o **\<clear>** elemento.

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

Esse elemento pode ser usado no arquivo de configuração do aplicativo, no arquivo de configuração do computador (*Machine. config*) e nos arquivos *Web. config* que não estão no nível do diretório do aplicativo.

## <a name="see-also"></a>Confira também

- [Esquema do arquivo de configuração para o .NET Framework](index.md)
