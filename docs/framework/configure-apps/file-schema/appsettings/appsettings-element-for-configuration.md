---
title: Elemento <appSettings> para <configuration>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings
helpviewer_keywords:
- appSettings Element
- <appSettings> Element
ms.assetid: 39694cc4-6b84-45a6-9329-385a0d8b48fe
author: guardrex
ms.author: mairaw
ms.openlocfilehash: dcdf8d0f11ae65353da08bba1f8d2fe5ab415c6b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61705552"
---
# <a name="appsettings-element-for-configuration"></a>\<appSettings > elemento para \<configuration >

Contém configurações de aplicativo personalizadas. Essa é uma seção de configuração predefinidos fornecida pelo .NET Framework.

[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md)   
&nbsp;&nbsp;**\<appSettings>**

## <a name="syntax"></a>Sintaxe

```xml
<appSettings>
  <!-- Elements to add, clear, or remove configuration settings -->
</appSettings>
```

## <a name="attribute"></a>Atributo

|           | Descrição |
| --------- | ----------- |
| **file**  | Atributo opcional.<br><br>Especifica um caminho relativo para um arquivo externo que contém as definições de configuração de aplicativo personalizado. O arquivo especificado contém o mesmo tipo de configurações que são especificadas na  **\<Adicionar >**,  **\<remover >**, e  **\<limpar >** elementos e usa o mesmo par de chave/valor de formato como esses elementos.<br><br>O caminho especificado é relativo ao arquivo de configuração principal. Para um aplicativo de formulários do Windows, essa é a pasta de binária (como */bin/debug*), não o local do arquivo de configuração do aplicativo. Para aplicativos Web Forms, o caminho é relativo a raiz do aplicativo, em que o *Web. config* arquivo está localizado.<br><br>Observe que o tempo de execução ignora o atributo se o arquivo especificado não pode ser encontrado. |

## <a name="parent-element"></a>Elemento pai

|     | Descrição |
| --- | ----------- |
| [**\<Configuração >** elemento](~/docs/framework/configure-apps/file-schema/configuration-element.md) | O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework. |

## <a name="child-elements"></a>Elementos filho

|     | Descrição |
| --- | ----------- |
| [**\<add>**](~/docs/framework/configure-apps/file-schema/appsettings/add-element-for-appsettings.md) | Adiciona uma configuração de aplicativo personalizado. |
| [**\<clear>**](~/docs/framework/configure-apps/file-schema/appsettings/clear-element-for-appsettings.md) | Limpa todas as configurações de aplicativo definida anteriormente. |
| [**\<remove>**](~/docs/framework/configure-apps/file-schema/appsettings/remove-element-for-appsettings.md) | Remove uma configuração de aplicativo definida anteriormente. |

## <a name="remarks"></a>Comentários

O  **\<appSettings >** elemento armazena informações de configuração de aplicativo personalizado, como cadeias de conexão de banco de dados, caminhos de arquivo, URLs de serviço Web XML ou qualquer outra informação de configuração personalizada para um aplicativo. Os pares chave/valor especificados na  **\<appSettings >** elemento são acessadas em código usando o <xref:System.Configuration.ConfigurationSettings> classe.

Você pode usar o **arquivo** atributo na  **\<appSettings >** elemento do *Web. config* e arquivos de configuração do aplicativo. Esse atributo especifica um arquivo de configuração que fornece configurações adicionais ou substitui as configurações especificadas na  **\<appSettings >** elemento. O **arquivo** atributo pode ser usado no código-fonte controle equipe cenários de desenvolvimento, como quando um usuário deseja substituir as configurações de projeto especificadas em um arquivo de configuração do aplicativo.

Arquivos de configuração especificados pelo **arquivo** atributo deve ter um nó raiz do  **\<appSettings >** vez  **\<Configuração >**.

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

Esse elemento pode ser usado no arquivo de configuração do aplicativo, arquivo de configuração de máquina (*Machine. config*), e *Web. config* arquivos que não estão no nível de diretório do aplicativo.

## <a name="see-also"></a>Consulte também

- [Esquema de arquivo de configuração para o .NET Framework](~/docs/framework/configure-apps/file-schema/index.md)
