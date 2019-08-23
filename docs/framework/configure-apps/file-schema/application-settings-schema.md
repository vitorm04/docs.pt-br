---
title: Esquema de configurações do aplicativo
ms.date: 03/30/2017
helpviewer_keywords:
- schema application settings
- application settings, schema [Windows Forms]
- Windows Forms, application settings schema
- configuration schema [.NET Framework], application settings
ms.assetid: 5797fcff-6081-4e8c-bebf-63d9c70cf14b
ms.openlocfilehash: 89a08434332b0242fe57e9dcaa3b3ebcc5692d06
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927758"
---
# <a name="application-settings-schema"></a>Esquema de configurações do aplicativo

As configurações de aplicativo permitem que um aplicativo Windows Forms ou ASP.NET armazene e recupere as configurações no escopo do aplicativo e em escopo do usuário. Nesse contexto, uma *configuração* é qualquer informação que possa ser específica para o aplicativo ou específica para o usuário atual — tudo, desde uma cadeia de conexão de banco de dados até o tamanho de janela padrão preferencial do usuário.

Por padrão, as configurações do aplicativo em um aplicativo Windows Forms <xref:System.Configuration.LocalFileSettingsProvider> usam a classe, que usa o sistema de configuração do .net para armazenar as configurações em um arquivo de configuração XML. Para obter mais informações sobre os arquivos usados pelas configurações do aplicativo, consulte [arquitetura de configurações do aplicativo](../../winforms/advanced/application-settings-architecture.md).

Configurações de aplicativo define os seguintes elementos como parte dos arquivos de configuração que ele usa.

| Elemento                    | Descrição                                                                           |
| -------------------------- | ------------------------------------------------------------------------------------- |
| **\<applicationSettings>** | Contém todas  **\<** as marcas de > de configuração específicas do aplicativo.                         |
| **\<userSettings>**        | Contém todas  **\<** as marcas de > de configuração específicas do usuário atual.                        |
| **\<> de configuração**             | Define uma configuração. **O\<filho de ApplicationSettings >** ou  **\<UserSettings >** . |
| **\<value>**               | Define o valor de uma configuração. Filho da  **\<configuração >** .                                   |

## <a name="applicationsettings-element"></a>\<elemento applicationSettings >

Esse elemento contém todas  **\<** as marcas de > de configuração que são específicas para uma instância do aplicativo em um computador cliente. Não define nenhum atributo.

## <a name="usersettings-element"></a>\<UserSettings > elemento

Esse elemento contém todas  **\<** as marcas de > de configuração que são específicas para o usuário que está usando o aplicativo no momento. Não define nenhum atributo.

## <a name="setting-element"></a>\<definindo > elemento

Esse elemento define uma configuração. Ele tem os atributos a seguir.

| Atributo        | Descrição |
| ---------------- | ----------- |
| **name**         | Necessário. A ID exclusiva da configuração. As configurações criadas por meio do Visual Studio são salvas com o nome `ProjectName.Properties.Settings`. |
| **serializedAs** | Necessário. O formato a ser usado para serializar o valor para texto. Os valores válidos são:<br><br>- `string`. O valor é serializado como uma cadeia de caracteres <xref:System.ComponentModel.TypeConverter>usando um.<br>- `xml`. O valor é serializado usando a serialização XML.<br>- `binary`. O valor é serializado como binário codificado por texto usando serialização binária.<br />- `custom`. O provedor de configurações tem um conhecimento inerente dessa configuração e a serializa e a desserializa. |

## <a name="value-element"></a>\<elemento de > de valor

Esse elemento contém o valor de uma configuração.

## <a name="example"></a>Exemplo

O exemplo a seguir mostra um arquivo de configurações do aplicativo que define duas configurações no escopo do aplicativo e duas configurações no escopo do usuário:

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <configSections>
    <sectionGroup name="applicationSettings" type="System.Configuration.ApplicationSettingsGroup, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">
      <section name="WindowsApplication1.Properties.Settings" type="System.Configuration.ClientSettingsSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />
    </sectionGroup>
    <sectionGroup name="userSettings" type="System.Configuration.UserSettingsGroup, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">
      <section name="WindowsApplication1.Properties.Settings" type="System.Configuration.ClientSettingsSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" allowExeDefinition="MachineToLocalUser" />
    </sectionGroup>
  </configSections>
  <applicationSettings>
    <WindowsApplication1.Properties.Settings>
      <setting name="Cursor" serializeAs="String">
        <value>Default</value>
      </setting>
      <setting name="DoubleBuffering" serializeAs="String">
        <value>False</value>
      </setting>
    </WindowsApplication1.Properties.Settings>
  </applicationSettings>
  <userSettings>
    <WindowsApplication1.Properties.Settings>
      <setting name="FormTitle" serializeAs="String">
        <value>Form1</value>
      </setting>
      <setting name="FormSize" serializeAs="String">
        <value>595, 536</value>
      </setting>
    </WindowsApplication1.Properties.Settings>
  </userSettings>
</configuration>
```

## <a name="see-also"></a>Consulte também

- [Visão Geral das Configurações do Aplicativo](../../winforms/advanced/application-settings-overview.md)
- [Arquitetura das Configurações do Aplicativo](../../winforms/advanced/application-settings-architecture.md)
