---
title: '&lt;Limpar&gt; elemento para &lt;configSections&gt;'
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/clear
helpviewer_keywords:
- clear Element
- <clear> Element
ms.assetid: 77f1d761-ff45-4001-8f36-3a3e5c41fa63
author: guardrex
ms.author: mairaw
ms.openlocfilehash: 42a44d66a3f70d0572484adf4c8dd946edf2297f
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="clear-element-for-configsections"></a>\<Limpar > elemento \<configSections >

Limpa todas as seções definidas anteriormente e grupos de seções.

[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md)   
&nbsp;&nbsp;[**\<configSections >**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md)   
&nbsp;&nbsp;&nbsp;&nbsp;**\<Limpar >**

## <a name="syntax"></a>Sintaxe

```xml
<clear/>
```

## <a name="attribute"></a>Atributo

|           | Descrição |
| --------- | ----------- |
| **name**  | Atributo obrigatório.<br><br>Especifica o nome da seção ou grupo da seção para remover. |

## <a name="parent-element"></a>Elemento pai

|     | Descrição |
| --- | ----------- |
| [**\<configSections >** elemento](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) | Contém declarações de namespace e de seção de configuração. |

# <a name="child-elements"></a>Elementos filho

Nenhum

## <a name="remarks"></a>Comentários

O  **\<limpar >** elemento remove todas as seções e grupos de seções do seu aplicativo que foram definidas anteriormente no arquivo de configuração atual ou em um nível superior na hierarquia de arquivos de configuração.

## <a name="example"></a>Exemplo

Este exemplo define um arquivo de configuração do computador e um arquivo de configuração do aplicativo e mostra como usar o  **\<limpar >** elemento em um arquivo de configuração do aplicativo para limpar seções definidas anteriormente no arquivo de configuração de máquina.

O seguinte código de arquivo de configuração de máquina declara duas seções,  **\<sampleSection >** e  **\<anotherSampleSection >**, que são lidas antes do aplicativo arquivo de configuração:

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

O seguinte código de arquivo de configuração de aplicativo limpa todas as seções declaradas anteriormente. O aplicativo não pode usar ou recuperar as configurações em uma das seções que foram declaradas no arquivo de configuração da máquina. No entanto, ele pode usar as configurações do  **\<anotherSection >** porque ele vem após o  **\<limpar >** elemento.

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

## <a name="configuration-file"></a>arquivo de configuração

Esse elemento pode ser usado no arquivo de configuração do aplicativo, o arquivo de configuração de máquina (*Machine. config*), e *Web. config* arquivos que não estão no nível de diretório do aplicativo.

## <a name="see-also"></a>Consulte também

[Esquema de arquivo de configuração para o .NET Framework](~/docs/framework/configure-apps/file-schema/index.md)
