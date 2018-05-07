---
title: '&lt;Limpar&gt; elemento para NameValueSectionHandler e DictionarySectionHandler'
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName/clear
helpviewer_keywords:
- clear Element
- <clear> Element
ms.assetid: ff2294ec-fb82-4b0c-933e-ae185433fc7b
author: guardrex
ms.author: mairaw
ms.openlocfilehash: a1cbd682faa4c60e50bc3b73b58ef226dd599da2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="clear-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a>\<Limpar > elemento NameValueSectionHandler e DictionarySectionHandler

Limpa todas as configurações previamente definidas em uma seção.

[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md)   
&nbsp;&nbsp;[**\<sectionName >**](~/docs/framework/configure-apps/file-schema/custom-element-2.md)   
&nbsp;&nbsp;&nbsp;&nbsp;**\<Limpar >**

## <a name="syntax"></a>Sintaxe

```xml
<clear />
```

## <a name="attributes"></a>Atributos

Nenhum

## <a name="parent-element"></a>Elemento pai

|     | Descrição |
| --- | ------------|
| [**\<sectionName >** elemento](~/docs/framework/configure-apps/file-schema/custom-element-2.md) | Define as configurações para as seções de configuração personalizadas que usam o <xref:System.Configuration.NameValueSectionHandler> e <xref:System.Configuration.DictionarySectionHandler> classes. |

## <a name="child-elements"></a>Elementos filho

Nenhum

## <a name="remarks"></a>Comentários

Você pode usar o  **\<limpar >** elemento para remover todas as configurações do aplicativo que foram definidas em um nível superior na hierarquia de arquivos de configuração.

## <a name="example"></a>Exemplo

Este exemplo define um arquivo de configuração do computador e um arquivo de configuração do aplicativo e mostra como usar o  **\<limpar >** elemento em um arquivo de configuração do aplicativo para limpar seções definidas anteriormente no arquivo de configuração de máquina.

O seguinte código de arquivo de configuração de máquina declara a seção  **\<mySection >**:

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

O seguinte código de arquivo de configuração de aplicativo remove todas as configurações de  **\<mySection >**. O aplicativo não é possível recuperar as configurações que foram declarados no no  **\<mySection >** seção do arquivo de configuração de máquina.

```xml
<!-- Application configuration file -->
<configuration>
  <mySection>
    <clear/>
  </mySection>
</configuration>
```

## <a name="configuration-file"></a>arquivo de configuração

Esse elemento pode ser usado no arquivo de configuração do aplicativo, o arquivo de configuração de máquina (*Machine. config*), e *Web. config* arquivos que não estão no nível de diretório do aplicativo.

## <a name="see-also"></a>Consulte também

[Esquema de arquivo de configuração para o .NET Framework](~/docs/framework/configure-apps/file-schema/index.md)
