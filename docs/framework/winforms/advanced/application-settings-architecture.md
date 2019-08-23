---
title: Arquitetura das configurações do aplicativo
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application settings [Windows Forms], architecture
ms.assetid: c8eb2ad0-fac6-4ea2-9140-675a4a44d562
ms.openlocfilehash: c3858cfab59b63761f43f6b3eaad9bf8ca4c1dbc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69916702"
---
# <a name="application-settings-architecture"></a>Arquitetura das configurações do aplicativo
Este tópico descreve como a arquitetura das configurações de aplicativo funciona e explora recursos avançados da arquitetura, como as configurações agrupadas e as chaves de configurações.

 A arquitetura das configurações de aplicativo dá suporte à configuração de configurações fortemente tipadas com escopo do aplicativo ou do usuário e a persistência das configurações entre as sessões do aplicativo. A arquitetura oferece um mecanismo de persistência padrão para salvar as configurações e carregá-las do sistema de arquivos local. A arquitetura também define interfaces para fornecer um mecanismo personalizado de persistência.

 As interfaces são fornecidas para permitir que componentes personalizados mantenham suas próprias configurações quando forem hospedados em um aplicativo. Ao usar chaves de configurações, os componentes podem manter separadas as configurações para várias instâncias do componente.

## <a name="defining-settings"></a>configurando configurações
 A arquitetura de configurações do aplicativo é usada em ASP.NET e Windows Forms e contém várias classes base que são compartilhadas entre os dois ambientes. O mais importante é <xref:System.Configuration.SettingsBase>, que fornece acesso às configurações por meio de uma coleção e fornece métodos de baixo nível para carregar e salvar as configurações. Cada ambiente implementa sua própria classe derivada do <xref:System.Configuration.SettingsBase> para fornecer funcionalidade de configurações adicionais para esse ambiente. Em um aplicativo baseado em Windows Forms, todas as configurações de aplicativo devem ser definidas em uma classe derivada <xref:System.Configuration.ApplicationSettingsBase> da classe, o que adiciona a seguinte funcionalidade à classe base:

- Operações de carregar e salvar de nível mais alto

- Suporte a configurações de escopo do usuário

- Reverter as configurações do usuário para os padrões predefinidos

- Atualizar as configurações de uma versão anterior do aplicativo

- Validar configurações, antes que sejam alteradas ou antes que sejam salvas

 As configurações podem ser descritas usando vários atributos definidos no <xref:System.Configuration> namespace; elas são descritas em atributos de configurações do [aplicativo](application-settings-attributes.md). Ao definir uma configuração, você deve aplicá-la com um <xref:System.Configuration.ApplicationScopedSettingAttribute> ou <xref:System.Configuration.UserScopedSettingAttribute>, que descreve se a configuração se aplica a todo o aplicativo ou apenas ao usuário atual.

 O exemplo de código a seguir define uma classe de configurações personalizadas com uma única configuração, `BackgroundColor`.

 [!code-csharp[ApplicationSettings.Create#1](~/samples/snippets/csharp/VS_Snippets_Winforms/ApplicationSettings.Create/CS/MyAppSettings.cs#1)]
 [!code-vb[ApplicationSettings.Create#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ApplicationSettings.Create/VB/MyAppSettings.vb#1)]

## <a name="settings-persistence"></a>Persistência das configurações
 A <xref:System.Configuration.ApplicationSettingsBase> classe não mantém nem carrega configurações; esse trabalho se enquadra ao provedor de configurações, uma classe derivada de <xref:System.Configuration.SettingsProvider>. Se uma classe derivada de <xref:System.Configuration.ApplicationSettingsBase> não especificar um provedor de configurações por meio <xref:System.Configuration.SettingsProviderAttribute>do, o provedor padrão, <xref:System.Configuration.LocalFileSettingsProvider>, será usado.

 O sistema de configuração que foi lançado originalmente com o .NET Framework dá suporte ao fornecimento de dados de configuração de aplicativos estáticos por meio do arquivo Machine. `app.`config do computador local ou de um arquivo exe. config que você implanta com seu aplicativo. A <xref:System.Configuration.LocalFileSettingsProvider> classe expande esse suporte nativo das seguintes maneiras:

- As configurações de escopo do aplicativo podem ser armazenadas nos arquivos machine.config ou `app.`exe.config. O machine.config é sempre somente leitura, enquanto que o `app`.exe.config é restrito, por considerações de segurança, como somente leitura para a maioria dos aplicativos.

- As configurações de escopo do usuário podem ser armazenadas em arquivos `app`.exe.config, caso em que são tratadas como padrões estáticos.

- As configurações de escopo do usuário não padrão são armazenadas em um novo arquivo, *user*.config, em que *user* é o nome de usuário da pessoa que está executando o aplicativo no momento. Você pode especificar um padrão para uma configuração no escopo do usuário com <xref:System.Configuration.DefaultSettingValueAttribute>. Como as configurações de escopo do usuário geralmente são alteradas durante a execução do aplicativo, o `user`.config é sempre de leitura/gravação.

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

 Você só pode associar uma configuração de aplicativo a um componente que dá <xref:System.Windows.Forms.IBindableComponent> suporte à interface. Além disso, o componente deve implementar um evento de alteração para uma propriedade associada específica ou notificar as configurações do aplicativo que a propriedade <xref:System.ComponentModel.INotifyPropertyChanged> foi alterada por meio da interface. Se o componente não for implementado <xref:System.Windows.Forms.IBindableComponent> e você estiver ligando por meio do Visual Studio, as propriedades associadas serão definidas pela primeira vez, mas não serão atualizadas. Se o componente implementar <xref:System.Windows.Forms.IBindableComponent> , mas não oferecer suporte a notificações de alteração de propriedade, a associação não será atualizada no arquivo de configurações quando a propriedade for alterada.

 Alguns componentes Windows Forms, como, <xref:System.Windows.Forms.ToolStripItem>não dão suporte a associações de configurações.

### <a name="settings-serialization"></a>Serialização de configurações
 Quando <xref:System.Configuration.LocalFileSettingsProvider> o deve salvar as configurações no disco, ele executa as seguintes ações:

1. Usa reflexão para examinar todas as propriedades definidas em sua <xref:System.Configuration.ApplicationSettingsBase> classe derivada, localizando aquelas que são aplicadas com um <xref:System.Configuration.ApplicationScopedSettingAttribute> ou. <xref:System.Configuration.UserScopedSettingAttribute>

2. Serializa a propriedade para o disco. Ele primeiro tenta chamar o <xref:System.ComponentModel.TypeConverter.ConvertToString%2A> ou <xref:System.ComponentModel.TypeConverter.ConvertFromString%2A> no associado <xref:System.ComponentModel.TypeConverter>do tipo. Se isso não for bem-sucedido, ela usará a serialização de XML.

3. Determina quais configurações vão em quais arquivos, com base no atributo da configuração.

 Se você implementar sua própria classe de configurações, poderá usar o <xref:System.Configuration.SettingsSerializeAsAttribute> para marcar uma configuração para a serialização binária ou personalizada usando a <xref:System.Configuration.SettingsSerializeAs> enumeração. Para obter mais informações sobre como criar sua própria classe de configurações no [código, consulte Como: Criar configurações](how-to-create-application-settings.md)do aplicativo.

### <a name="settings-file-locations"></a>Locais de arquivo de configurações
 O local dos arquivos `app`.exe.config e *user*.config serão diferentes com base em como o aplicativo é instalado. Para um aplicativo baseado em Windows Forms copiado para o computador local `app`, o. exe. config residirá no mesmo diretório que o diretório base do arquivo executável principal do aplicativo, e o *User*. config residirá no local especificado por a <xref:System.Windows.Forms.Application.LocalUserAppDataPath%2A?displayProperty=nameWithType> propriedade. Para um aplicativo instalado por meio do ClickOnce, ambos os arquivos residirão no diretório de dados do ClickOnce abaixo de%InstallRoot%\Documents e\\configurações nome de*usuário*\ Configurações.

 O local de armazenamento desses arquivos será um pouco diferente se um usuário tiver habilitado perfis móveis, que permite que um usuário defina diferentes configurações de aplicativo e do Windows quando estiver usando outros computadores em um domínio. Nesse caso, os aplicativos ClickOnce e os aplicativos não-ClickOnce `app`terão seus arquivos. exe. config e *User*. config armazenados em%InstallRoot%\Documents e configurações\\*nome_do_usuário*\Application Data.

 Para obter mais informações sobre como o recurso de configurações de aplicativo funciona com a nova tecnologia de implantação, consulte [ClickOnce e configurações de aplicativo](/visualstudio/deployment/clickonce-and-application-settings). Para obter mais informações sobre o diretório de dados do ClickOnce, consulte Acessando [dados locais e remotos em aplicativos ClickOnce](/visualstudio/deployment/accessing-local-and-remote-data-in-clickonce-applications).

## <a name="application-settings-and-security"></a>Segurança e configurações de aplicativo
 As configurações de aplicativo são projetadas para trabalhar em confiança parcial, um ambiente restrito que é o padrão para aplicativos dos Windows Forms hospedados na Internet ou intranet. Não é necessária nenhuma permissão especial, além da confiança parcial, para usar as configurações de aplicativo com o provedor de configurações padrão.

 Quando as configurações do aplicativo são usadas em um aplicativo ClickOnce `user`, o arquivo. config é armazenado no diretório de dados do ClickOnce. O tamanho do arquivo `user`. config do aplicativo não pode exceder a cota do diretório de dados definida pelo ClickOnce. Para obter mais informações, consulte [ClickOnce e as configurações de aplicativo](/visualstudio/deployment/clickonce-and-application-settings).

## <a name="custom-settings-providers"></a>Provedores de configurações personalizadas
 Na arquitetura de configurações do aplicativo, há um acoplamento flexível entre a classe wrapper das configurações de aplicativos, derivada <xref:System.Configuration.ApplicationSettingsBase>de e o provedor de configurações associado ou provedores, derivados <xref:System.Configuration.SettingsProvider>de. Essa associação é definida somente pelo <xref:System.Configuration.SettingsProviderAttribute> aplicado à classe wrapper ou suas propriedades individuais. Se um provedor de configurações não for especificado explicitamente, o provedor padrão <xref:System.Configuration.LocalFileSettingsProvider>,, será usado. Como resultado, essa arquitetura dá suporte à criação e uso de provedores de configurações personalizados.

 Por exemplo, suponha que você queira desenvolver e usar o `SqlSettingsProvider`, um provedor que armazenará todos os dados de configurações em um banco de dados do Microsoft SQL Server. Sua <xref:System.Configuration.SettingsProvider>classe derivada receberia essas informações em seu `Initialize` método como um parâmetro do tipo <xref:System.Collections.Specialized.NameValueCollection?displayProperty=nameWithType>. Em seguida, você implementaria o <xref:System.Configuration.SettingsProvider.GetPropertyValues%2A> método para recuperar as configurações do armazenamento de dados e <xref:System.Configuration.SettingsProvider.SetPropertyValues%2A> salvá-las. Seu provedor pode usar o <xref:System.Configuration.SettingsPropertyCollection> fornecido para <xref:System.Configuration.SettingsProvider.GetPropertyValues%2A> para determinar o nome, o tipo e o escopo da propriedade, bem como quaisquer outros atributos de configurações definidos para essa propriedade.

 Seu provedor precisará implementar uma propriedade e um método cujas implementações podem não ser óbvias. A <xref:System.Configuration.SettingsProvider.ApplicationName%2A> propriedade é uma propriedade abstrata de <xref:System.Configuration.SettingsProvider>; você deve programá-la para retornar o seguinte:

 [!code-csharp[ApplicationSettings.Architecture#2](~/samples/snippets/csharp/VS_Snippets_Winforms/ApplicationSettings.Architecture/CS/DummyClass.cs#2)]
 [!code-vb[ApplicationSettings.Architecture#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ApplicationSettings.Architecture/VB/DummyProviderClass.vb#2)]

 Sua classe derivada também deve implementar um método `Initialize` que não recebe argumentos e não retorna nenhum valor. Esse método não é definido pelo <xref:System.Configuration.SettingsProvider>.

 Por fim, você <xref:System.Configuration.IApplicationSettingsProvider> implementa em seu provedor para dar suporte à atualização de configurações, à reversão de configurações para seus padrões e à atualização de configurações de uma versão de aplicativo para outra.

 Depois de ter implementado e compilado seu provedor, você precisa instruir a classe de configurações para usar este provedor em vez do padrão. Você realiza isso por meio <xref:System.Configuration.SettingsProviderAttribute>do. Se aplicado a uma classe de configurações inteira, o provedor será usado para cada configuração que a classe define; Se aplicado a configurações individuais, a arquitetura de configurações do aplicativo usa esse provedor apenas para essas configurações <xref:System.Configuration.LocalFileSettingsProvider> e usa para o restante. O exemplo de código a seguir mostra como instruir a classe de configurações para usar o provedor personalizado.

 [!code-csharp[ApplicationSettings.Architecture#1](~/samples/snippets/csharp/VS_Snippets_Winforms/ApplicationSettings.Architecture/CS/DummyClass.cs#1)]
 [!code-vb[ApplicationSettings.Architecture#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ApplicationSettings.Architecture/VB/DummyProviderClass.vb#1)]

 Um provedor pode ser chamado simultaneamente de vários threads, mas ele sempre gravará no mesmo local de armazenamento. Portanto, a arquitetura das configurações de aplicativo somente instanciará uma única instância de sua classe de provedor.

> [!IMPORTANT]
> Você deve garantir que seu provedor seja thread-safe e permita que apenas um thread por vez grave nos arquivos de configuração.

 Seu provedor não precisa dar suporte a todos os atributos de configurações definidos no namespace <xref:System.Configuration?displayProperty=nameWithType> , embora ele deva ter suporte <xref:System.Configuration.ApplicationScopedSettingAttribute> mínimo e <xref:System.Configuration.UserScopedSettingAttribute>e também deve dar suporte <xref:System.Configuration.DefaultSettingValueAttribute>a. Para os atributos aos quais ele não oferece suporte, o provedor deve apenas falhar, sem notificação. Ele não deve lançar uma exceção. No entanto, se a classe Settings usar uma combinação inválida de atributos — <xref:System.Configuration.ApplicationScopedSettingAttribute> como <xref:System.Configuration.UserScopedSettingAttribute> aplicar e à mesma configuração — seu provedor deverá lançar uma exceção e interromper a operação.

## <a name="see-also"></a>Consulte também

- <xref:System.Configuration.ApplicationSettingsBase>
- <xref:System.Configuration.SettingsProvider>
- <xref:System.Configuration.LocalFileSettingsProvider>
- [Visão Geral das Configurações do Aplicativo](application-settings-overview.md)
- [Configurações do Aplicativo para Controles Personalizados](application-settings-for-custom-controls.md)
- [O ClickOnce e as configurações de aplicativo](/visualstudio/deployment/clickonce-and-application-settings)
- [Esquema de configurações de aplicativo](../../configure-apps/file-schema/application-settings-schema.md)
