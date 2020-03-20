---
title: Elemento <appSettings> para <configuration>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings
helpviewer_keywords:
- appSettings Element
- <appSettings> Element
ms.assetid: 39694cc4-6b84-45a6-9329-385a0d8b48fe
ms.openlocfilehash: ea341d562f4b163a3a1771da0f20903b7d64bcdf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155525"
---
# <a name="appsettings-element-for-configuration"></a>\<appSettings> \<elemento para> de configuração

Contém configurações de aplicativos personalizadas. Esta é uma seção de configuração predefinida fornecida pelo .NET Framework.

configuração &nbsp; &nbsp; [** \<>**](../configuration-element.md) ** \<aplicativosConfigurações>**

## <a name="syntax"></a>Sintaxe

```xml
<appSettings>
  <!-- Elements to add, clear, or remove configuration settings -->
</appSettings>
```

## <a name="attribute"></a>Atributo

|           | Descrição |
| --------- | ----------- |
| **Arquivo**  | Atributo opcional.<br><br>Especifica um caminho relativo a um arquivo externo contendo configurações personalizadas de configuração de aplicativos. O arquivo especificado contém o mesmo tipo de configurações ** \< **especificadas no ** \<>de adicionar, **remover>e ** \<limpar elementos>** e usa o mesmo formato de par de tecla/valor que esses elementos.<br><br>O caminho especificado é relativo ao arquivo de configuração principal. Para um aplicativo do Windows Forms, esta é a pasta binária (como */bin/depuração),* não a localização do arquivo de configuração do aplicativo. Para aplicativos web forms, o caminho é relativo à raiz do aplicativo, onde o arquivo *Web.config* está localizado.<br><br>O tempo de execução ignora o atributo se o arquivo especificado não puder ser encontrado. |

## <a name="parent-element"></a>Elemento pai

|     | Descrição |
| --- | ----------- |
| [>de configuração ** \<** Elemento](../configuration-element.md) | O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework. |

## <a name="child-elements"></a>Elementos filho

|     | Descrição |
| --- | ----------- |
| [**\<adicionar>**](add-element-for-appsettings.md) | Adiciona uma configuração de aplicativo personalizada. |
| [**\<claro>**](clear-element-for-appsettings.md) | Limpa todas as configurações de aplicativo definidas anteriormente. |
| [**\<remover>**](remove-element-for-appsettings.md) | Remove uma configuração de aplicativo definida anteriormente. |

## <a name="remarks"></a>Comentários

O ** \<aplicativoConfigurações>** elemento armazena informações personalizadas de configuração de aplicativos, como strings de conexão de banco de dados, caminhos de arquivo, URLs de serviço web XML ou qualquer outra informação de configuração personalizada para um aplicativo. Os pares de chaves/valor especificados no ** \<elemento AppSettings**><xref:System.Configuration.ConfigurationSettings> são acessados em código usando a classe.

Você pode usar o atributo de **arquivo** no ** \<aplicativoConfigurações>** elemento dos arquivos de configuração *web.config* e de configuração de aplicativos. Este atributo especifica um arquivo de configuração que fornece configurações adicionais ou substitui as configurações especificadas no elemento ** \<Deconfigurações>.** O atributo **de arquivo** pode ser usado em cenários de desenvolvimento da equipe de controle de origem, como quando um usuário deseja substituir as configurações de projeto especificadas em um arquivo de configuração de aplicativo.

Os arquivos de configuração especificados pelo atributo **do arquivo** devem ter um nó raiz de ** \<configurações>** em vez de ** \<>de configuração **.

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

## <a name="configuration-file"></a>Arquivo de configuração

Esse elemento pode ser usado no arquivo de configuração do aplicativo, no arquivo de configuração da máquina *(Machine.config)* e nos arquivos *Web.config* que não estão no nível do diretório do aplicativo.

## <a name="see-also"></a>Confira também

- [Esquema de arquivo de configuração para o Framework .NET](../index.md)
