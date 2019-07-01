---
title: Arquitetura das configurações do aplicativo
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application settings [Windows Forms], architecture
ms.assetid: c8eb2ad0-fac6-4ea2-9140-675a4a44d562
ms.openlocfilehash: 717abc8f54669a5ca814a61827a0865215204e1b
ms.sourcegitcommit: 2d42b7ae4252cfe1232777f501ea9ac97df31b63
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2019
ms.locfileid: "67487347"
---
# <a name="application-settings-architecture"></a>Arquitetura das configurações do aplicativo
Este tópico descreve como a arquitetura das configurações de aplicativo funciona e explora recursos avançados da arquitetura, como as configurações agrupadas e as chaves de configurações.  
  
 A arquitetura das configurações de aplicativo dá suporte à configuração de configurações fortemente tipadas com escopo do aplicativo ou do usuário e a persistência das configurações entre as sessões do aplicativo. A arquitetura oferece um mecanismo de persistência padrão para salvar as configurações e carregá-las do sistema de arquivos local. A arquitetura também define interfaces para fornecer um mecanismo personalizado de persistência.  
  
 As interfaces são fornecidas para permitir que componentes personalizados mantenham suas próprias configurações quando forem hospedados em um aplicativo. Ao usar chaves de configurações, os componentes podem manter separadas as configurações para várias instâncias do componente.  
  
## <a name="defining-settings"></a>configurando configurações  
 A arquitetura de configurações do aplicativo é usada dentro do ASP.NET e Windows Forms e contém um número de classes base que são compartilhados entre os dois ambientes. O mais importante é <xref:System.Configuration.SettingsBase>, que fornece acesso às configurações através de uma coleção e fornece métodos de baixo nível para carregar e salvar as configurações. Cada ambiente implementa sua própria classe derivada de <xref:System.Configuration.SettingsBase> para fornecer a funcionalidade de configurações adicionais para esse ambiente. Em um aplicativo baseado em Windows Forms, todas as configurações de aplicativo devem ser definidas em uma classe derivada de <xref:System.Configuration.ApplicationSettingsBase> classe, que adiciona a seguinte funcionalidade à classe base:  
  
- Operações de carregar e salvar de nível mais alto  
  
- Suporte a configurações de escopo do usuário  
  
- Reverter as configurações do usuário para os padrões predefinidos  
  
- Atualizar as configurações de uma versão anterior do aplicativo  
  
- Validar configurações, antes que sejam alteradas ou antes que sejam salvas  
  
 As configurações podem ser descritas usando um número de atributos definidos dentro de <xref:System.Configuration> namespace; elas são descritas nas [atributos de configurações do aplicativo](application-settings-attributes.md). Quando você define uma configuração, você deverá aplicá-la com um <xref:System.Configuration.ApplicationScopedSettingAttribute> ou <xref:System.Configuration.UserScopedSettingAttribute>, que descreve se a configuração se aplica ao aplicativo inteiro ou apenas para o usuário atual.  
  
 O exemplo de código a seguir define uma classe de configurações personalizadas com uma única configuração, `BackgroundColor`.  
  
 [!code-csharp[ApplicationSettings.Create#1](~/samples/snippets/csharp/VS_Snippets_Winforms/ApplicationSettings.Create/CS/MyAppSettings.cs#1)]
 [!code-vb[ApplicationSettings.Create#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ApplicationSettings.Create/VB/MyAppSettings.vb#1)]  
  
## <a name="settings-persistence"></a>Persistência das configurações  
 O <xref:System.Configuration.ApplicationSettingsBase> classe não próprio persistir ou carregar configurações; este trabalho recai sobre o provedor de configurações, uma classe que deriva de <xref:System.Configuration.SettingsProvider>. Se uma classe derivada de <xref:System.Configuration.ApplicationSettingsBase> não especifica um provedor de configurações por meio de <xref:System.Configuration.SettingsProviderAttribute>, em seguida, o provedor padrão, <xref:System.Configuration.LocalFileSettingsProvider>, é usado.  
  
 O sistema de configuração que foi originalmente lançado com o .NET Framework dá suporte ao fornecimento de dados de configuração estática do aplicativo por meio do arquivo Machine. config de qualquer um dos locais do computador ou em um `app.`arquivo exe. config que você implanta com seu aplicativo. O <xref:System.Configuration.LocalFileSettingsProvider> classe expande esse suporte nativo das seguintes maneiras:  
  
- As configurações de escopo do aplicativo podem ser armazenadas nos arquivos machine.config ou `app.`exe.config. O machine.config é sempre somente leitura, enquanto que o `app`.exe.config é restrito, por considerações de segurança, como somente leitura para a maioria dos aplicativos.  
  
- As configurações de escopo do usuário podem ser armazenadas em arquivos `app`.exe.config, caso em que são tratadas como padrões estáticos.  
  
- As configurações de escopo do usuário não padrão são armazenadas em um novo arquivo, *user*.config, em que *user* é o nome de usuário da pessoa que está executando o aplicativo no momento. Você pode especificar um padrão para uma configuração de escopo do usuário com <xref:System.Configuration.DefaultSettingValueAttribute>. Como as configurações de escopo do usuário geralmente são alteradas durante a execução do aplicativo, o `user`.config é sempre de leitura/gravação.  
  
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
  
 Uma configuração de aplicativo só pode ser associado a um componente que dá suporte a <xref:System.Windows.Forms.IBindableComponent> interface. Além disso, o componente deve implementar um evento de alteração para uma determinada propriedade associada ou notificar as configurações do aplicativo que a propriedade foi alterada por meio de <xref:System.ComponentModel.INotifyPropertyChanged> interface. Se o componente não implementar <xref:System.Windows.Forms.IBindableComponent> e você estiver associando através do Visual Studio, as propriedades associadas serão definidas na primeira vez, mas não serão atualizadas. Se o componente implementa <xref:System.Windows.Forms.IBindableComponent> , mas as notificações de alteração não suporte à propriedade, a associação não será atualizado no arquivo de configurações quando a propriedade é alterada.  
  
 Alguns componentes do Windows Forms, tal como <xref:System.Windows.Forms.ToolStripItem>, não dão suporte a associações de configurações.  
  
### <a name="settings-serialization"></a>Serialização de configurações  
 Quando <xref:System.Configuration.LocalFileSettingsProvider> deve salvar as configurações em disco, ele executa as seguintes ações:  
  
1. Usa a reflexão para examinar todas as propriedades definidas no seu <xref:System.Configuration.ApplicationSettingsBase> derivado da classe, localizando aquelas que são aplicadas com um <xref:System.Configuration.ApplicationScopedSettingAttribute> ou <xref:System.Configuration.UserScopedSettingAttribute>.  
  
2. Serializa a propriedade para o disco. Ela primeiro tenta chamar o <xref:System.ComponentModel.TypeConverter.ConvertToString%2A> ou <xref:System.ComponentModel.TypeConverter.ConvertFromString%2A> sobre o tipo associado à <xref:System.ComponentModel.TypeConverter>. Se isso não for bem-sucedido, ela usará a serialização de XML.  
  
3. Determina quais configurações vão em quais arquivos, com base no atributo da configuração.  
  
 Se você implementar sua própria classe de configurações, você pode usar o <xref:System.Configuration.SettingsSerializeAsAttribute> para marcar uma configuração para a serialização binária ou personalizada usando o <xref:System.Configuration.SettingsSerializeAs> enumeração. Para obter mais informações sobre como criar sua própria classe de configurações no código, consulte [como: Criar configurações de aplicativo](how-to-create-application-settings.md).  
  
### <a name="settings-file-locations"></a>Locais de arquivo de configurações  
 O local dos arquivos `app`.exe.config e *user*.config serão diferentes com base em como o aplicativo é instalado. Para um aplicativo baseado em Windows Forms copiado para o computador local, `app`. exe. config residirá no mesmo diretório que o diretório base do arquivo de executável principal do aplicativo, e *usuário*. config residirá no local especificado pelo <xref:System.Windows.Forms.Application.LocalUserAppDataPath%2A?displayProperty=nameWithType> propriedade. Para um aplicativo instalado por meio do ClickOnce, ambos os arquivos residirão no diretório de dados do ClickOnce, sob %InstallRoot%\Documents e configurações\\*nome de usuário*\Local Settings.  
  
 O local de armazenamento desses arquivos será um pouco diferente se um usuário tiver habilitado perfis móveis, que permite que um usuário defina diferentes configurações de aplicativo e do Windows quando estiver usando outros computadores em um domínio. Nesse caso, os aplicativos ClickOnce e aplicativos não-ClickOnce terão seus `app`. exe e *usuário*arquivos. config armazenados em %InstallRoot%\Documents and Settings\\  *nome de usuário*\Application Data.  
  
 Para obter mais informações sobre como o recurso de configurações de aplicativo funciona com a nova tecnologia de implantação, consulte [ClickOnce e configurações de aplicativo](/visualstudio/deployment/clickonce-and-application-settings). Para obter mais informações sobre o diretório de dados do ClickOnce, consulte [acessando dados locais e remotos em aplicativos ClickOnce](/visualstudio/deployment/accessing-local-and-remote-data-in-clickonce-applications).  
  
## <a name="application-settings-and-security"></a>Segurança e configurações de aplicativo  
 As configurações de aplicativo são projetadas para trabalhar em confiança parcial, um ambiente restrito que é o padrão para aplicativos dos Windows Forms hospedados na Internet ou intranet. Não é necessária nenhuma permissão especial, além da confiança parcial, para usar as configurações de aplicativo com o provedor de configurações padrão.  
  
 Quando as configurações do aplicativo são usadas em um aplicativo ClickOnce, o `user`arquivo. config é armazenado no diretório de dados do ClickOnce. O tamanho da caixa de diálogo `user`arquivo. config não pode exceder a cota de diretório de dados definida pelo ClickOnce. Para obter mais informações, consulte [ClickOnce e as configurações de aplicativo](/visualstudio/deployment/clickonce-and-application-settings).  
  
## <a name="custom-settings-providers"></a>Provedores de configurações personalizadas  
 Na arquitetura de configurações do aplicativo, há um acoplamento fraco entre as configurações de aplicativos classe wrapper, derivada de <xref:System.Configuration.ApplicationSettingsBase>, e o provedor de configurações associado ou provedores, derivados <xref:System.Configuration.SettingsProvider>. Essa associação é definida apenas pelo <xref:System.Configuration.SettingsProviderAttribute> aplicado à classe wrapper ou suas propriedades individuais. Se as configurações de um provedor não é explicitamente especificado, o provedor padrão, <xref:System.Configuration.LocalFileSettingsProvider>, é usado. Como resultado, essa arquitetura dá suporte à criação e uso de provedores de configurações personalizados.  
  
 Por exemplo, suponha que você queira desenvolver e usar o `SqlSettingsProvider`, um provedor que armazenará todos os dados de configurações em um banco de dados do Microsoft SQL Server. Sua <xref:System.Configuration.SettingsProvider>-classe derivada deve receber essas informações no seu `Initialize` o método como um parâmetro de tipo <xref:System.Collections.Specialized.NameValueCollection?displayProperty=nameWithType>. Em seguida, você poderia implementar o <xref:System.Configuration.SettingsProvider.GetPropertyValues%2A> método para recuperar as configurações de armazenamento de dados, e <xref:System.Configuration.SettingsProvider.SetPropertyValues%2A> para salvá-los. O provedor pode usar o <xref:System.Configuration.SettingsPropertyCollection> fornecido para <xref:System.Configuration.SettingsProvider.GetPropertyValues%2A> para determinar o nome da propriedade, tipo e escopo, bem como quaisquer outros atributos de configurações definidos para essa propriedade.  
  
 Seu provedor precisará implementar uma propriedade e um método cujas implementações podem não ser óbvias. O <xref:System.Configuration.SettingsProvider.ApplicationName%2A> é uma propriedade abstrata do <xref:System.Configuration.SettingsProvider>; você deve programá-lo para retornar o seguinte:  
  
 [!code-csharp[ApplicationSettings.Architecture#2](~/samples/snippets/csharp/VS_Snippets_Winforms/ApplicationSettings.Architecture/CS/DummyClass.cs#2)]
 [!code-vb[ApplicationSettings.Architecture#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ApplicationSettings.Architecture/VB/DummyProviderClass.vb#2)]  
  
 Sua classe derivada também deve implementar um método `Initialize` que não recebe argumentos e não retorna nenhum valor. Esse método não é definido pelo <xref:System.Configuration.SettingsProvider>.  
  
 Finalmente, você implementa <xref:System.Configuration.IApplicationSettingsProvider> no seu provedor para fornecer suporte para atualizar as configurações, revertendo as configurações para seus padrões e atualizar as configurações de uma versão do aplicativo para outro.  
  
 Depois de ter implementado e compilado seu provedor, você precisa instruir a classe de configurações para usar este provedor em vez do padrão. Você fazer isso por meio de <xref:System.Configuration.SettingsProviderAttribute>. Se aplicado a uma classe configurações inteira, o provedor é usado para cada configuração que define a classe; Se aplicado a configurações individuais, a arquitetura das configurações do aplicativo usa esse provedor para essas configurações somente e usa <xref:System.Configuration.LocalFileSettingsProvider> para o restante. O exemplo de código a seguir mostra como instruir a classe de configurações para usar o provedor personalizado.  
  
 [!code-csharp[ApplicationSettings.Architecture#1](~/samples/snippets/csharp/VS_Snippets_Winforms/ApplicationSettings.Architecture/CS/DummyClass.cs#1)]
 [!code-vb[ApplicationSettings.Architecture#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ApplicationSettings.Architecture/VB/DummyProviderClass.vb#1)]  
  
 Um provedor pode ser chamado simultaneamente de vários threads, mas ele sempre gravará no mesmo local de armazenamento. Portanto, a arquitetura das configurações de aplicativo somente instanciará uma única instância de sua classe de provedor.  
  
> [!IMPORTANT]
>  Você deve garantir que seu provedor seja thread-safe e permita que apenas um thread por vez grave nos arquivos de configuração.  
  
 Seu provedor não precisa dar suporte a todas as configurações de atributos definidos na <xref:System.Configuration?displayProperty=nameWithType> namespace, embora ele deva em um suporte mínimo <xref:System.Configuration.ApplicationScopedSettingAttribute> e <xref:System.Configuration.UserScopedSettingAttribute>e também deve dar suporte <xref:System.Configuration.DefaultSettingValueAttribute>. Para os atributos aos quais ele não oferece suporte, o provedor deve apenas falhar, sem notificação. Ele não deve lançar uma exceção. Se a classe de configurações usa uma combinação inválida de atributos, no entanto, como a aplicação <xref:System.Configuration.ApplicationScopedSettingAttribute> e <xref:System.Configuration.UserScopedSettingAttribute> à mesma configuração — seu provedor deve lançar uma exceção e interromper a operação.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Configuration.ApplicationSettingsBase>
- <xref:System.Configuration.SettingsProvider>
- <xref:System.Configuration.LocalFileSettingsProvider>
- [Visão Geral das Configurações do Aplicativo](application-settings-overview.md)
- [Configurações do Aplicativo para Controles Personalizados](application-settings-for-custom-controls.md)
- [O ClickOnce e as configurações de aplicativo](/visualstudio/deployment/clickonce-and-application-settings)
- [Esquema de configurações de aplicativo](../../configure-apps/file-schema/application-settings-schema.md)
