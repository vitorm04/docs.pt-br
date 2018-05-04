---
title: Esquema de configurações do aplicativo
ms.date: 05/01/2017
helpviewer_keywords:
- schema app settings
- app settings, schema [Windows Forms]
- Windows Forms, app settings schema
- configuration schema [.NET Framework], app settings
ms.assetid: 99347d62-3ea5-40b6-bfec-c31431011422
author: guardrex
ms.author: mairaw
ms.openlocfilehash: 154f38880225fb420f9944f336ff885bd116e2c3
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="app-settings-schema"></a>Esquema de configurações do aplicativo

Contém configurações de aplicativo personalizadas, como caminhos de arquivo, URLs de serviço da Web em XML ou qualquer outra informação de configuração personalizada para um aplicativo.

[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md)   
&nbsp;&nbsp;[**\<appSettings>**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md)   
&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](~/docs/framework/configure-apps/file-schema/appsettings/add-element-for-appsettings.md)   
&nbsp;&nbsp;&nbsp;&nbsp;[**\<clear>**](~/docs/framework/configure-apps/file-schema/appsettings/clear-element-for-appsettings.md)   
&nbsp;&nbsp;&nbsp;&nbsp;[**\<remove>**](~/docs/framework/configure-apps/file-schema/appsettings/remove-element-for-appsettings.md)

| Elemento | Descrição |
| ------- | ----------- |
| [**\<appSettings>**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) | Contém as marcas **\<add>**, **\<clear>** e **\<remove>** para controlar as configurações de aplicativo. Tem um atributo **file** opcional. |
| [**\<add>**](~/docs/framework/configure-apps/file-schema/appsettings/add-element-for-appsettings.md) | Define uma configuração. Filho de **\<appSettings>**. Requer os atributos **key** e **value**. |
| [**\<clear>**](~/docs/framework/configure-apps/file-schema/appsettings/clear-element-for-appsettings.md) | Limpa todas as configurações. Filho de **\<appSettings>**. Não tem atributos. |
| [**\<remove>**](~/docs/framework/configure-apps/file-schema/appsettings/remove-element-for-appsettings.md) | Remove uma configuração. Filho de **\<appSettings>**. Requer um atributo **key**. |

## <a name="appsettings-element"></a>Elemento \<appSettings>

Esse elemento contém as marcas **\<add>**, **\<clear>** e **\<remove>** para controlar as configurações de aplicativo. Define um atributo opcional para **file**.

## <a name="add-element"></a>Elemento \<add>

Adiciona uma configuração de aplicativo personalizada como um par nome/valor para a coleção de configurações do aplicativo. Define atributos de **key** e **value**.

## <a name="clear-element"></a>Elemento \<clear>

Remove todas as referências a configurações de aplicativo personalizadas herdadas e permite somente as referências que são adicionadas por elementos **\<add>** após o elemento **\<clear>**. Não define nenhum atributo.

## <a name="remove-element"></a>Elemento \<remove>

Remove uma referência a uma configuração de aplicativo personalizada herdada da coleção de configurações de aplicativo. Define um atributo para **key**.

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

## <a name="see-also"></a>Consulte também

[Visão geral sobre configurações de aplicativo](~/docs/framework/winforms/advanced/application-settings-overview.md)   
[Arquitetura das Configurações do Aplicativo](~/docs/framework/winforms/advanced/application-settings-architecture.md)
