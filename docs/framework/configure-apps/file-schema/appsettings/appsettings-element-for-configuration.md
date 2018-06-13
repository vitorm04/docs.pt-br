---
title: '&lt;appSettings&gt; elemento para &lt;configuração&gt;'
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings
helpviewer_keywords:
- appSettings Element
- <appSettings> Element
ms.assetid: 39694cc4-6b84-45a6-9329-385a0d8b48fe
author: guardrex
ms.author: mairaw
ms.openlocfilehash: d17400536b911ce0be4d2bf105b0b4d99d0916df
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32742959"
---
# <a name="appsettings-element-for-configuration"></a>\<appSettings > elemento \<Configuração >

Contém configurações de aplicativo personalizado. Essa é uma seção de configuração predefinidos fornecida pelo .NET Framework.

[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md)   
&nbsp;&nbsp;**\<appSettings >**

## <a name="syntax"></a>Sintaxe

```xml
<appSettings>
  <!-- Elements to add, clear, or remove configuration settings -->
</appSettings>
```

## <a name="attribute"></a>Atributo

|           | Descrição |
| --------- | ----------- |
| **file**  | Atributo opcional.<br><br>Especifica um caminho relativo para um arquivo externo que contém as definições de configuração de aplicativo personalizado. O arquivo especificado contém o mesmo tipo de configurações que são especificados no  **\<Adicionar >**,  **\<remover >**, e  **\<limpar >** elementos e usa o mesmo par chave/valor de formato como esses elementos.<br><br>O caminho especificado é relativo ao arquivo de configuração principais. Para um aplicativo de formulários do Windows, essa é a pasta de binária (como */bin/debug*), não o local do arquivo de configuração do aplicativo. Para aplicativos de formulários da Web, o caminho é relativo a raiz do aplicativo, onde o *Web. config* arquivo está localizado.<br><br>Observe que o tempo de execução ignora o atributo se o arquivo especificado não pode ser encontrado. |

## <a name="parent-element"></a>Elemento pai

|     | Descrição |
| --- | ----------- |
| [**\<Configuração >** elemento](~/docs/framework/configure-apps/file-schema/configuration-element.md) | O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework. |

## <a name="child-elements"></a>Elementos filho

|     | Descrição |
| --- | ----------- |
| [**\<add>**](~/docs/framework/configure-apps/file-schema/appsettings/add-element-for-appsettings.md) | Adiciona uma configuração de aplicativo personalizado. |
| [**\<clear>**](~/docs/framework/configure-apps/file-schema/appsettings/clear-element-for-appsettings.md) | Limpa todas as configurações de aplicativo definidas anteriormente. |
| [**\<remove>**](~/docs/framework/configure-apps/file-schema/appsettings/remove-element-for-appsettings.md) | Remove uma configuração de aplicativo definido anteriormente. |

## <a name="remarks"></a>Comentários

O  **\<appSettings >** elemento armazena informações de configuração de aplicativo personalizado, como cadeias de conexão de banco de dados, os caminhos de arquivo, URLs de serviço da Web em XML ou qualquer outra informação de configuração personalizada para um aplicativo. Os pares chave/valor especificados no  **\<appSettings >** elemento são acessadas em código usando o <xref:System.Configuration.ConfigurationSettings> classe.

Você pode usar o **arquivo** atributo no  **\<appSettings >** elemento o *Web. config* e arquivos de configuração do aplicativo. Esse atributo especifica um arquivo de configuração que fornece configurações adicionais ou substitui as configurações especificadas no  **\<appSettings >** elemento. O **arquivo** atributo pode ser usado na origem controle team cenários de desenvolvimento, como quando um usuário deseja substituir as configurações de projeto especificadas em um arquivo de configuração do aplicativo.

Arquivos de configuração especificados pelo **arquivo** atributo deve ter um nó de raiz de  **\<appSettings >** em vez de  **\<Configuração >**.

## <a name="example"></a>Exemplo

O exemplo a seguir mostra um arquivo de configurações de aplicativo externo (*custom.config*) que define uma configuração de aplicativo personalizada:

```xml
<?xml version="1.0" encoding="utf-8" ?>
<appSettings>
  <add key="MyCustomSetting" value="MyCustomSettingValue" />
</appSettings>
```

O exemplo a seguir mostra um arquivo de configuração de aplicativo que consome a configuração no arquivo de configurações externas e define sua própria configuração de aplicativo:

```xml
<configuration>
  <appSettings file="custom.config">
    <add key="ApplicationName" value="MyApplication" />
  </appSettings>
</configuration>
```

## <a name="configuration-file"></a>arquivo de configuração

Esse elemento pode ser usado no arquivo de configuração do aplicativo, o arquivo de configuração de máquina (*Machine. config*), e *Web. config* arquivos que não estão no nível de diretório do aplicativo.

## <a name="see-also"></a>Consulte também

[Esquema de arquivo de configuração para o .NET Framework](~/docs/framework/configure-apps/file-schema/index.md)
