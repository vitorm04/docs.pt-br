---
title: Arquitetura das configurações do aplicativo
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application settings [Windows Forms], architecture
ms.assetid: c8eb2ad0-fac6-4ea2-9140-675a4a44d562
ms.openlocfilehash: 078b5f3fc1cd4273af282580f41e68ca9bd8ff51
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182620"
---
# <a name="application-settings-architecture"></a>Arquitetura das configurações do aplicativo
Este tópico descreve como a arquitetura das configurações de aplicativo funciona e explora recursos avançados da arquitetura, como as configurações agrupadas e as chaves de configurações.

 A arquitetura das configurações de aplicativo dá suporte à configuração de configurações fortemente tipadas com escopo do aplicativo ou do usuário e a persistência das configurações entre as sessões do aplicativo. A arquitetura oferece um mecanismo de persistência padrão para salvar as configurações e carregá-las do sistema de arquivos local. A arquitetura também define interfaces para fornecer um mecanismo personalizado de persistência.

 As interfaces são fornecidas para permitir que componentes personalizados mantenham suas próprias configurações quando forem hospedados em um aplicativo. Ao usar chaves de configurações, os componentes podem manter separadas as configurações para várias instâncias do componente.

## <a name="defining-settings"></a>configurando configurações
 A arquitetura de configurações do aplicativo é usada em ASP.NET e no Windows Forms, e contém uma série de classes base que são compartilhadas em ambos os ambientes. O mais <xref:System.Configuration.SettingsBase>importante é, que fornece acesso às configurações através de uma coleção, e fornece métodos de baixo nível para configurações de carregamento e salvamento. Cada ambiente implementa sua própria <xref:System.Configuration.SettingsBase> classe derivada para fornecer funcionalidades de configurações adicionais para esse ambiente. Em um aplicativo baseado no Windows Forms, todas as configurações <xref:System.Configuration.ApplicationSettingsBase> do aplicativo devem ser definidas em uma classe derivada da classe, que adiciona a seguinte funcionalidade à classe base:

- Operações de carregar e salvar de nível mais alto

- Suporte a configurações de escopo do usuário

- Reverter as configurações do usuário para os padrões predefinidos

- Atualizar as configurações de uma versão anterior do aplicativo

- Validar configurações, antes que sejam alteradas ou antes que sejam salvas

 As configurações podem ser descritas usando uma <xref:System.Configuration> série de atributos definidos no namespace; estes são descritos em [Atributos de Configurações de Aplicativo](application-settings-attributes.md). Quando você define uma configuração, <xref:System.Configuration.ApplicationScopedSettingAttribute> você <xref:System.Configuration.UserScopedSettingAttribute>deve aplicá-la com um ou , que descreve se a configuração se aplica a todo o aplicativo ou apenas ao usuário atual.

 O exemplo de código a seguir define uma classe de configurações personalizadas com uma única configuração, `BackgroundColor`.

 [!code-csharp[ApplicationSettings.Create#1](~/samples/snippets/csharp/VS_Snippets_Winforms/ApplicationSettings.Create/CS/MyAppSettings.cs#1)]
 [!code-vb[ApplicationSettings.Create#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ApplicationSettings.Create/VB/MyAppSettings.vb#1)]

## <a name="settings-persistence"></a>Persistência das configurações
 A <xref:System.Configuration.ApplicationSettingsBase> classe em si não persiste ou carrega as configurações; este trabalho cabe ao provedor de configurações, <xref:System.Configuration.SettingsProvider>uma classe que deriva de . Se uma classe <xref:System.Configuration.ApplicationSettingsBase> derivada não especificar um <xref:System.Configuration.SettingsProviderAttribute>provedor de configurações através do provedor padrão, <xref:System.Configuration.LocalFileSettingsProvider>será usado.

 O sistema de configuração que foi originalmente lançado com o .NET Framework suporta fornecer dados de `app.`configuração de aplicativos estáticos através do arquivo machine.config do computador local ou dentro de um arquivo exe.config que você implanta com seu aplicativo. A <xref:System.Configuration.LocalFileSettingsProvider> classe expande esse suporte nativo das seguintes maneiras:

- As configurações de escopo do aplicativo podem ser armazenadas nos arquivos machine.config ou `app.`exe.config. O machine.config é sempre somente leitura, enquanto que o `app`.exe.config é restrito, por considerações de segurança, como somente leitura para a maioria dos aplicativos.

- As configurações de escopo do usuário podem ser armazenadas em arquivos `app`.exe.config, caso em que são tratadas como padrões estáticos.

- As configurações de escopo do usuário não padrão são armazenadas em um novo arquivo, *user*.config, em que *user* é o nome de usuário da pessoa que está executando o aplicativo no momento. Você pode especificar um padrão para <xref:System.Configuration.DefaultSettingValueAttribute>uma configuração com escopo de usuário com . Como as configurações de escopo do usuário geralmente são alteradas durante a execução do aplicativo, o `user`.config é sempre de leitura/gravação.

 Todos os três arquivos de configuração armazenam as configurações no formato XML. O elemento XML de nível superior para configurações de escopo do aplicativo é `<appSettings>`, enquanto que o `<userSettings>` é usado para configurações de escopo do usuário. Um arquivo `app`.exe.config que contém configurações de escopo do aplicativo e padrões para configurações de escopo do usuário teria esta aparência:

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
    <configSections>
        <sectionGroup name="applicationSettings" type="System.Configuration.ApplicationSettingsGroup, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" >
            <section name="WindowsApplication1.Properties.Settings" type="System.Configuration.ClientSettingsSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />
        </sectionGroup>
        <sectionGroup name="userSettings" type="System.Configuration.UserSettingsGroup, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" >
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

 Para obter uma configuração dos elementos da seção de configurações de aplicativo de um arquivo de configuração, consulte [Esquema de configurações de aplicativo](../../configure-apps/file-schema/application-settings-schema.md).

### <a name="settings-bindings"></a>Associações de configurações
 As configurações de aplicativo usam a arquitetura de vinculação de dados dos Windows Forms para fornecer comunicação bidirecional das atualizações de configurações entre o objeto de configurações e os componentes. Se você usar o Visual Studio para criar configurações de aplicativo e atribuí-las às propriedades do componente, essas associações serão geradas automaticamente.

 Você só pode vincular uma configuração de <xref:System.Windows.Forms.IBindableComponent> aplicativo a um componente que suporte a interface. Além disso, o componente deve implementar um evento de alteração para uma propriedade <xref:System.ComponentModel.INotifyPropertyChanged> vinculada específica ou notificar as configurações do aplicativo de que a propriedade foi alterada através da interface. Se o componente <xref:System.Windows.Forms.IBindableComponent> não for implementado e você estiver vinculado através do Visual Studio, as propriedades vinculadas serão definidas na primeira vez, mas não serão atualizadas. Se o componente <xref:System.Windows.Forms.IBindableComponent> implementar, mas não suportar notificações de alteração de propriedade, a vinculação não será atualizada no arquivo de configurações quando a propriedade for alterada.

 Alguns componentes do <xref:System.Windows.Forms.ToolStripItem>Windows Forms, como , não suportam vinculações de configurações.

### <a name="settings-serialization"></a>Serialização de configurações
 Quando <xref:System.Configuration.LocalFileSettingsProvider> deve salvar configurações em disco, ele executa as seguintes ações:

1. Usa a reflexão para examinar <xref:System.Configuration.ApplicationSettingsBase> todas as propriedades definidas em sua <xref:System.Configuration.ApplicationScopedSettingAttribute> <xref:System.Configuration.UserScopedSettingAttribute>classe derivada, encontrando aquelas que são aplicadas com um ou .

2. Serializa a propriedade para o disco. Primeiro tenta ligar <xref:System.ComponentModel.TypeConverter.ConvertToString%2A> para <xref:System.ComponentModel.TypeConverter.ConvertFromString%2A> o ou no <xref:System.ComponentModel.TypeConverter>tipo associado. Se isso não for bem-sucedido, ela usará a serialização de XML.

3. Determina quais configurações vão em quais arquivos, com base no atributo da configuração.

 Se você implementar sua própria classe de <xref:System.Configuration.SettingsSerializeAsAttribute> configurações, você pode usar a configuração para serialização binária ou personalizada usando a <xref:System.Configuration.SettingsSerializeAs> enumeração. Para obter mais informações sobre como criar sua própria classe de configurações no código, consulte [Como criar configurações de aplicativo](how-to-create-application-settings.md).

### <a name="settings-file-locations"></a>Locais do arquivo de configurações
 O local dos arquivos `app`.exe.config e *user*.config serão diferentes com base em como o aplicativo é instalado. Para um aplicativo baseado em Formulários do `app`Windows copiado para o computador local, .exe.config residirá no mesmo diretório que o diretório base do principal <xref:System.Windows.Forms.Application.LocalUserAppDataPath%2A?displayProperty=nameWithType> arquivo executável do aplicativo, e o *usuário*.config residirá no local especificado pela propriedade. Para um aplicativo instalado por meio do ClickOnce, ambos os arquivos residirão no Diretório de dados\\ClickOnce abaixo de %InstallRoot%\Documentos e Configurações nome de*usuário*\Configurações locais.

 A localização de armazenamento desses arquivos é ligeiramente diferente se um usuário tiver ativado perfis de roaming, o que permite que um usuário defina diferentes configurações do Windows e aplicativo quando estiver usando outros computadores dentro de um domínio. Nesse caso, tanto os aplicativos ClickOnce quanto os aplicativos `app`non-ClickOnce terão seus arquivos .exe.config e *user*.config armazenados em %InstallRoot\\Documents and Settings\\*username*\Application Data.

 Para obter mais informações sobre como o recurso de configurações de aplicativo funciona com a nova tecnologia de implantação, consulte [ClickOnce e configurações de aplicativo](/visualstudio/deployment/clickonce-and-application-settings). Para obter mais informações sobre o Diretório de dados do ClickOnce, consulte [Acessando dados locais e remotos em aplicativos ClickOnce](/visualstudio/deployment/accessing-local-and-remote-data-in-clickonce-applications).

## <a name="application-settings-and-security"></a>Segurança e configurações de aplicativo
 As configurações de aplicativo são projetadas para trabalhar em confiança parcial, um ambiente restrito que é o padrão para aplicativos dos Windows Forms hospedados na Internet ou intranet. Não é necessária nenhuma permissão especial, além da confiança parcial, para usar as configurações de aplicativo com o provedor de configurações padrão.

 Quando as configurações do aplicativo são `user`usadas em um aplicativo ClickOnce, o arquivo .config é armazenado no diretório de dados ClickOnce. O tamanho do arquivo `user`.config do aplicativo não pode exceder a cota de diretório de dados definida pelo ClickOnce. Para obter mais informações, consulte [ClickOnce e as configurações de aplicativo](/visualstudio/deployment/clickonce-and-application-settings).

## <a name="custom-settings-providers"></a>Provedores de configurações personalizadas
 Na arquitetura Configurações de aplicativo, há um acoplamento frouxo entre <xref:System.Configuration.ApplicationSettingsBase>as configurações de configurações da classe <xref:System.Configuration.SettingsProvider>wrapper, derivadas e as configurações associadas do provedor ou provedor, derivadas de . Esta associação é definida <xref:System.Configuration.SettingsProviderAttribute> apenas pelo aplicado à classe de invólucro ou suas propriedades individuais. Se um provedor de configurações não for explicitamente <xref:System.Configuration.LocalFileSettingsProvider>especificado, o provedor padrão, será usado. Como resultado, essa arquitetura dá suporte à criação e uso de provedores de configurações personalizados.

 Por exemplo, suponha que você queira desenvolver e usar o `SqlSettingsProvider`, um provedor que armazenará todos os dados de configurações em um banco de dados do Microsoft SQL Server. Sua <xref:System.Configuration.SettingsProvider>classe derivada receberia essas `Initialize` informações em seu método <xref:System.Collections.Specialized.NameValueCollection?displayProperty=nameWithType>como um parâmetro do tipo . Em seguida, <xref:System.Configuration.SettingsProvider.GetPropertyValues%2A> você implementaria o método para <xref:System.Configuration.SettingsProvider.SetPropertyValues%2A> recuperar suas configurações do armazenamento de dados e salvá-las. Seu provedor pode <xref:System.Configuration.SettingsPropertyCollection> usar <xref:System.Configuration.SettingsProvider.GetPropertyValues%2A> o fornecido para determinar o nome, tipo e escopo da propriedade, bem como quaisquer outros atributos de configurações definidos para essa propriedade.

 Seu provedor precisará implementar uma propriedade e um método cujas implementações podem não ser óbvias. A <xref:System.Configuration.SettingsProvider.ApplicationName%2A> propriedade é uma <xref:System.Configuration.SettingsProvider>propriedade abstrata de; você deve programá-lo para retornar o seguinte:

 [!code-csharp[ApplicationSettings.Architecture#2](~/samples/snippets/csharp/VS_Snippets_Winforms/ApplicationSettings.Architecture/CS/DummyClass.cs#2)]
 [!code-vb[ApplicationSettings.Architecture#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ApplicationSettings.Architecture/VB/DummyProviderClass.vb#2)]

 Sua classe derivada também deve implementar um método `Initialize` que não recebe argumentos e não retorna nenhum valor. Este método não <xref:System.Configuration.SettingsProvider>é definido por .

 Finalmente, você <xref:System.Configuration.IApplicationSettingsProvider> implementa em seu provedor para fornecer suporte para configurações refrescantes, reverter configurações para seus padrões e atualizar configurações de uma versão de aplicativo para outra.

 Depois de ter implementado e compilado seu provedor, você precisa instruir a classe de configurações para usar este provedor em vez do padrão. Você consegue isso <xref:System.Configuration.SettingsProviderAttribute>através do. Se aplicado a uma classe de configurações inteira, o provedor é usado para cada configuração definida pela classe; se aplicado a configurações individuais, a arquitetura Configurações de aplicativo <xref:System.Configuration.LocalFileSettingsProvider> usa esse provedor apenas para essas configurações e usa para o resto. O exemplo de código a seguir mostra como instruir a classe de configurações para usar o provedor personalizado.

 [!code-csharp[ApplicationSettings.Architecture#1](~/samples/snippets/csharp/VS_Snippets_Winforms/ApplicationSettings.Architecture/CS/DummyClass.cs#1)]
 [!code-vb[ApplicationSettings.Architecture#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ApplicationSettings.Architecture/VB/DummyProviderClass.vb#1)]

 Um provedor pode ser chamado simultaneamente de vários threads, mas ele sempre gravará no mesmo local de armazenamento. Portanto, a arquitetura das configurações de aplicativo somente instanciará uma única instância de sua classe de provedor.

> [!IMPORTANT]
> Você deve garantir que seu provedor seja thread-safe e permita que apenas um thread por vez grave nos arquivos de configuração.

 Seu provedor não precisa suportar todos os atributos <xref:System.Configuration?displayProperty=nameWithType> de configuração definidos no <xref:System.Configuration.ApplicationScopedSettingAttribute> <xref:System.Configuration.UserScopedSettingAttribute>namespace, embora <xref:System.Configuration.DefaultSettingValueAttribute>ele deve com um suporte mínimo e , e também deve suportar . Para os atributos aos quais ele não oferece suporte, o provedor deve apenas falhar, sem notificação. Ele não deve lançar uma exceção. Se a classe de configurações usar uma combinação inválida <xref:System.Configuration.ApplicationScopedSettingAttribute> de <xref:System.Configuration.UserScopedSettingAttribute> atributos, no entanto — como a aplicação e a mesma configuração — o provedor deve abrir uma exceção e cessar a operação.

## <a name="see-also"></a>Confira também

- <xref:System.Configuration.ApplicationSettingsBase>
- <xref:System.Configuration.SettingsProvider>
- <xref:System.Configuration.LocalFileSettingsProvider>
- [Visão geral das configurações do aplicativo](application-settings-overview.md)
- [Configurações do Aplicativo para Controles Personalizados](application-settings-for-custom-controls.md)
- [ClickOnce e configurações de aplicativo](/visualstudio/deployment/clickonce-and-application-settings)
- [Esquema de configurações de aplicativo](../../configure-apps/file-schema/application-settings-schema.md)
