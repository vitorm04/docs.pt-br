---
title: Esquema de configurações de aplicativos
ms.date: 03/30/2017
helpviewer_keywords:
- schema application settings
- application settings, schema [Windows Forms]
- Windows Forms, application settings schema
- configuration schema [.NET Framework], application settings
ms.assetid: 5797fcff-6081-4e8c-bebf-63d9c70cf14b
ms.openlocfilehash: 90d471888950347c041b4824b659ce33fda512d7
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/13/2020
ms.locfileid: "81242823"
---
# <a name="application-settings-schema"></a>Esquema de configurações de aplicativos

As configurações do aplicativo permitem que um aplicativo do Windows Forms ou ASP.NET armazene e recupere configurações com escopo de aplicativo e escopo do usuário. Neste contexto, uma *configuração* é qualquer informação que possa ser específica para o aplicativo ou específica para o usuário atual — qualquer coisa, desde uma seqüência de conexão de banco de dados até o tamanho padrão de janela preferido do usuário.

Por padrão, as configurações do aplicativo <xref:System.Configuration.LocalFileSettingsProvider> em um aplicativo Do Windows Forms usam a classe, que usa o sistema de configuração .NET para armazenar configurações em um arquivo de configuração XML. Para obter mais informações sobre os arquivos usados pelas configurações do aplicativo, consulte [Arquitetura de configurações de aplicativo](../../winforms/advanced/application-settings-architecture.md).

As configurações do aplicativo definem os seguintes elementos como parte dos arquivos de configuração que ele usa.

| Elemento                    | Descrição                                                                           |
| -------------------------- | ------------------------------------------------------------------------------------- |
| **\<configurações de aplicativos>** | Contém todas as ** \<configurações>** tags específicas para o aplicativo.                         |
| **\<>de configurações de usuário**        | Contém todas as ** \<configurações>** tags específicas para o usuário atual.                        |
| **\<configuração>**             | Define uma configuração. Filho de ** \<configurações de aplicativosConfigurações>** ou ** \<>de configurações do usuário **. |
| **\<>de valores**               | Define o valor de uma configuração. Filho de ** \<configuração>**.                                   |

## <a name="applicationsettings-element"></a>\<aplicativoConfigurações> elemento

Este elemento contém todas as ** \<configurações>** tags específicas para uma instância do aplicativo em um computador cliente. Não define nenhum atributo.

## <a name="usersettings-element"></a>\<usuárioConfigurações> elemento

Este elemento contém todas as ** \<configurações>** tags específicas para o usuário que está usando o aplicativo no momento. Não define nenhum atributo.

## <a name="setting-element"></a>\<configuração> elemento

Este elemento define uma configuração. Tem os seguintes atributos.

| Atributo        | Descrição |
| ---------------- | ----------- |
| **name**         | Obrigatórios. A identificação única da configuração. As configurações criadas através do `ProjectName.Properties.Settings`Visual Studio são salvas com o nome . |
| **Serializeas** | Obrigatórios. O formato a ser usado para serializar o valor para texto. Os valores válidos são:<br><br>- `string`. O valor é serializado como <xref:System.ComponentModel.TypeConverter>uma seqüência usando um .<br>- `xml`. O valor é serializado usando serialização XML.<br>- `binary`. O valor é serializado como binário codificado por texto usando serialização binária.<br />- `custom`. O provedor de configurações tem conhecimento inerente a essa configuração e serializa e desserializa-o. |

## <a name="value-element"></a>\<elemento> de valor

Este elemento contém o valor de uma configuração.

## <a name="example"></a>Exemplo

O exemplo a seguir mostra um arquivo de configurações de aplicativo que define duas configurações com escopo de aplicativo e duas configurações com escopo do usuário:

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

## <a name="see-also"></a>Confira também

- [Visão geral das configurações do aplicativo](../../winforms/advanced/application-settings-overview.md)
- [Arquitetura das configurações do aplicativo](../../winforms/advanced/application-settings-architecture.md)
