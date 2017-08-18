---
title: "Como configurar serviços de aplicativo cliente"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- client application services, configuring
ms.assetid: 34a8688a-a32c-40d3-94be-c8e610c6a4e8
caps.latest.revision: 23
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: a1d15e380b6b7e8b226f26b261f4d4540eeef88d
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-configure-client-application-services"></a>Como configurar serviços de aplicativo cliente
Este tópico descreve como usar o [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] **Designer de Projeto** para habilitar e configurar serviços de aplicativos cliente. Você pode usar serviços do aplicativo cliente para validar os usuários e recuperar funções de usuário e configurações de um serviço do aplicativo [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)] existente. Após a configuração, você pode acessar os serviços habilitados no código do aplicativo, conforme descrito em [Visão geral dos serviços de aplicativo cliente](../../../docs/framework/common-client-technologies/client-application-services-overview.md). Para obter mais informações sobre os serviços de aplicativos [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)], consulte [Visão geral sobre Serviços de Aplicativos ASP.NET](http://msdn.microsoft.com/library/1162e529-0d70-44b2-b3ab-83e60c695013).  
  
 Você pode habilitar e configurar serviços de aplicativos cliente na página **Serviços** do **Designer de Projeto**. A página **Serviços** atualiza os valores no arquivo App.config do projeto. Para acessar o **Designer de Projeto**, use o comando **Propriedades** no menu **Projeto**. Para obter mais informações sobre a página **Serviços**, consulte [Página Serviços, Designer de Projeto](https://msdn.microsoft.com/library/bb398109).  
  
 O procedimento a seguir descreve como executar a configuração básica para serviços do aplicativo cliente. As opções de configuração avançada são descritas nas próximas seções.  
  
### <a name="to-configure-client-application-services"></a>Para configurar os serviços do aplicativo cliente  
  
1.  No **Gerenciador de Soluções**, selecione um nó do projeto e, no menu **Projeto**, clique em **Propriedades**.  
  
     O **Designer de Projeto** é exibido.  
  
2.  Clique na guia **Serviços**. A página **Serviços** é exibida, conforme mostrado na ilustração a seguir.  
  
     ![A guia Serviços no designer de projeto](../../../docs/framework/common-client-technologies/media/casdesigner.png "casdesigner")  
  
3.  Na página **Serviços**, selecione **Habilitar serviços de aplicativos cliente**.  
  
    > [!NOTE]
    >  Os serviços do aplicativo cliente exigem a versão completa do .NET Framework e não há suporte para o .NET Framework Client Profile. Se a caixa de seleção **Habilitar serviços do aplicativo cliente** estiver desabilitada, verifique se a **Estrutura de destino** está definida como .NET Framework 3.5 ou posterior. Para exibir a configuração da **Estrutura de destino** em C#, abra o Designer de Projeto e clique na página **Aplicativo**. Para exibir a configuração **Estrutura de destino** no Visual Basic, abra o Designer de Projeto, clique na página **Compilar** e, em seguida, clique em **Opções Avançadas de Compilação**.  
  
4.  Selecione **Usar autenticação de Formulários** se você pretende fornecer seus próprios controles de logon ou a caixa de diálogo ou selecione **Usar autenticação do Windows** para usar a identidade fornecida pelo sistema operacional. Para obter mais informações, consulte [Visão geral dos serviços de aplicativo cliente](../../../docs/framework/common-client-technologies/client-application-services-overview.md).  
  
    > [!NOTE]
    >  Se você selecionar **Usar autenticação do Windows**, os serviços de aplicativos cliente serão automaticamente configurados para usar um banco de dados do SQL Server Compact. Isso é indicado na caixa de diálogo **Configurações Avançadas para Serviços**, conforme descrito na próxima seção. Se você selecionar **Usar autenticação de Formulários**, a configuração **Usar cadeia de conexão personalizada** não será limpa automaticamente. Isso pode resultar em erros se o banco de dados [!INCLUDE[ssEW](../../../includes/ssew-md.md)] já tiver sido gerado para uso com autenticação do Windows. Para corrigir esses erros, desmarque a configuração **Usar cadeia de conexão personalizada** na caixa de diálogo **Configurações Avançadas para Serviços**.  
  
5.  Se você selecionou **Usar autenticação de Formulários**, na caixa **Local do serviço de autenticação**, especifique a URL do host de serviço, sem incluir o nome do arquivo. O designer acrescentará automaticamente o nome de arquivo padrão (Authentication_JSON_AppService.axd) ao gravar o valor no arquivo de configuração.  
  
6.  Opcionalmente, se você selecionou **Usar autenticação de Formulários**, poderá especificar um valor na caixa **Provedor de credenciais**. O provedor de credenciais deve implementar a interface <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider>. Usando um provedor de credenciais, você pode separar sua interface de usuário de logon de outro código do aplicativo. Isso permite que você crie uma caixa de diálogo de logon único para uso em vários aplicativos. Para obter mais informações, consulte [Como implementar o logon do usuário com os serviços de aplicativo cliente](../../../docs/framework/common-client-technologies/how-to-implement-user-login-with-client-application-services.md).  
  
     Se você especificar um provedor de credenciais, deverá especificá-lo como um nome de tipo qualificado do assembly. Para obter mais informações, consulte <xref:System.Type.AssemblyQualifiedName%2A?displayProperty=fullName> e [Assembly Names](../../../docs/framework/app-domains/assembly-names.md) (Nomes de assembly). Em sua forma mais simples, um nome de tipo qualificado do assembly é semelhante ao exemplo a seguir:  
  
    ```  
    MyNamespace.MyLoginClass, MyAssembly  
    ```  
  
7.  Nas caixas de texto **Local do serviço de funções** e **Local do serviço de configurações da Web**, especifique o local de serviço para cada serviço, sem incluir o nome do arquivo. O designer acrescentará automaticamente o nome de arquivo padrão (Role_JSON_AppService.axd e Profile_JSON_AppService.axd) ao gravar o valor no arquivo de configuração.  
  
8.  Opcionalmente, clique em **Avançado** para modificar as configurações avançadas, como o comportamento de cache local. Para obter mais informações, consulte o procedimento a seguir.  
  
## <a name="advanced-configuration"></a>Configuração avançada  
 Os procedimentos a seguir descrevem como configurar os serviços do aplicativo cliente para cenários menos comuns. Por exemplo, você pode usar essas opções de configuração para aplicativos implantados em locais públicos, ou usar um banco de dados do SQL Server Compact criptografado como o cache de dados local.  
  
#### <a name="to-configure-advanced-settings-for-client-application-services"></a>Para definir configurações avançadas para serviços do aplicativo cliente  
  
1.  Na página **Serviços** do **Designer de Projeto**, clique em **Avançado**.  
  
     A caixa de diálogo **Configurações Avançadas para Serviços** é exibida, conforme mostrado na ilustração a seguir. Para obter mais informações sobre essa caixa de diálogo, consulte [Caixa de diálogo Configurações Avançadas para Serviços](/visualstudio/ide/reference/advanced-settings-for-services-dialog-box).  
  
     ![Caixa de diálogo Configurações Avançadas para Serviços](../../../docs/framework/common-client-technologies/media/casdialog.png "casdialog")  
  
2.  Marque ou desmarque **Salvar hash de senha localmente para habilitar o logon offline**. Quando você seleciona essa opção, um formato criptografado da senha do usuário será armazenado em cache localmente. Isso é útil se você implementar o modo offline para o seu aplicativo. Com essa opção selecionada, você pode validar usuários mesmo quando a propriedade <xref:System.Web.ClientServices.ConnectivityStatus.IsOffline%2A> tiver sido definida como `true`.  
  
3.  Marque ou desmarque **Requer que os usuários façam logon novamente sempre que o cookie de servidor expira**. O cookie de autenticação é configurado no serviço remoto e indica quanto tempo o logon do usuário permanecerá ativo. Para obter mais informações sobre como configurar o cookie, consulte o atributo `timeout` no [Elemento forms para autenticação (Esquema de Definições do ASP.NET)](http://msdn.microsoft.com/en-us/8163b8b5-ea6c-46c8-b5a9-c4c3de31c0b3).  
  
     Se você selecionar essa opção, tentar acessar as funções remotas ou os serviços de configurações da Web, após o cookie de autenticação ter expirado, irá gerar uma <xref:System.Net.WebException>. Você pode tratar essa exceção e exibir uma caixa de diálogo de logon para revalidar os usuários. Para obter um exemplo desse comportamento, consulte [Instruções passo a passo: usando serviços de aplicativo cliente](../../../docs/framework/common-client-technologies/walkthrough-using-client-application-services.md). Essa opção é útil para aplicativos implantados em locais públicos, para garantir que os usuários que deixam o aplicativo em execução após o uso não permanecerão autenticados indefinidamente.  
  
     Se você desmarcar essa opção e tentar acessar os serviços remotos após o cookie de autenticação ter expirado, os usuários serão revalidados automaticamente.  
  
4.  Especifique um valor para **Tempo limite de cache do serviço de função**. Defina esse intervalo de tempo como um valor pequeno quando as funções forem atualizadas com frequência ou como um valor maior quando as funções forem raramente atualizadas. Se você implementar o modo offline, defina o intervalo de tempo como um valor grande para impedir que as informações sobre a função expirem enquanto o aplicativo estiver offline.  
  
     O provedor de função acessa os valores de função em cache ou o serviço de funções quando você chama o método <xref:System.Web.Security.RolePrincipal.IsInRole%2A>. Para redefinir de forma programática o cache e forçar esse método a acessar o serviço remoto, chame o método <xref:System.Web.ClientServices.Providers.ClientRoleProvider.ResetCache%2A>.  
  
5.  Marque ou desmarque **Usar cadeia de conexão personalizada**. Para obter mais informações, consulte o procedimento a seguir.  
  
#### <a name="to-configure-client-application-services-to-use-a-database-for-the-local-cache"></a>Para configurar os serviços do aplicativo cliente para usar um banco de dados para o cache local  
  
1.  Na página **Serviços** do **Designer de Projeto**, clique em **Avançado**.  
  
     A caixa de diálogo **Configurações Avançadas para Serviços** é exibida.  
  
2.  Selecione **Usar cadeia de conexão personalizada**.  
  
     O valor padrão de `Data Source = |SQL/CE|` é exibido na caixa de texto.  
  
3.  Para gerar e usar um banco de dados do SQL Server Compact, mantenha o valor de cadeia de conexão padrão. [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] gerará um arquivo de banco de dados e o colocará no diretório indicado pela propriedade <xref:System.Windows.Forms.Application.UserAppDataPath%2A?displayProperty=fullName>.  
  
4.  Para gerar e usar um banco de dados [!INCLUDE[ssEW](../../../includes/ssew-md.md)] criptografado, adicione os valores `password` e `encrypt database` à sequência de conexão, conforme mostrado no exemplo a seguir.  
  
    > [!NOTE]
    >  Certifique-se de especificar uma senha forte. Você não pode alterar a senha depois que o banco de dados for gerado.  
  
    ```  
    Data Source = |SQL/CE|;password=<password>;encrypt database=true  
    ```  
  
5.  Para usar seu próprio banco de dados [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], especifique sua própria sequência de conexão. Para obter informações sobre formatos de sequências de conexão válidos, consulte a documentação do [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Esse banco de dados não é gerado automaticamente. A sequência de conexão deve se referir a um banco de dados existente que você pode criar usando as instruções SQL a seguir.  
  
    ```  
    CREATE TABLE ApplicationProperties (PropertyName nvarchar(256),  
        PropertyValue nvarchar(256))  
    CREATE TABLE UserProperties (PropertyName nvarchar(256),  
        PropertyValue nvarchar(256))  
    CREATE TABLE Roles (UserName nvarchar(256),   
        RoleName nvarchar(256))  
    CREATE TABLE Settings (PropertyName nvarchar(256),   
        PropertyStoredAs nvarchar(1), PropertyValue nvarchar(2048))  
    ```  
  
## <a name="using-custom-providers"></a>Usando provedores personalizados  
 Por padrão, o recurso de serviços do aplicativo cliente usa os provedores no namespace <xref:System.Web.ClientServices.Providers?displayProperty=fullName>. Quando você configura seu aplicativo usando a página **Serviços** do **Designer de Projeto**, referências a esses provedores são adicionadas ao seu arquivo App.config. Esses provedores padrão acessam provedores correspondentes no servidor. Os serviços da Web são geralmente configurados para acessar dados do usuário por meio de provedores como <xref:System.Web.Security.SqlMembershipProvider> e <xref:System.Web.Security.SqlRoleProvider>.  
  
 Se desejar usar provedores de serviço personalizado, você normalmente alterará os provedores no lado do servidor para que eles afetem todos os aplicativos cliente que acessam o servidor. No entanto, você tem a opção de usar provedores não padrão no lado do cliente. Você pode especificar provedores de autenticação ou de funções personalizados no arquivo App.config do seu projeto, conforme mostrado no procedimento a seguir. Para obter informações sobre como criar provedores de função e de autenticação personalizada, consulte [Implementando um Provedor de Associação](http://msdn.microsoft.com/library/d8658b8e-c962-4f64-95e1-4acce35e4582) e [Implementar um provedor de função](http://msdn.microsoft.com/library/851671ce-bf9b-43f2-aba4-bc9d28b11c7d). Também é possível usar um provedor de configurações personalizado, modificando a classe `Settings` do seu projeto (acessada como `Properties.Settings.Default` em C# e `My.Settings` em [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]). Para obter mais informações, consulte [Application Settings Architecture](../../../docs/framework/winforms/advanced/application-settings-architecture.md) (Arquitetura das configurações do aplicativo).  
  
#### <a name="to-configure-client-application-services-to-use-non-default-providers"></a>Para configurar os serviços do aplicativo cliente para usar provedores não padrão  
  
1.  Para usar um provedor de serviços de autenticação ou de funções não padrão, primeiro conclua todas as outras definições de configuração usando a página **Serviços**.  
  
2.  Feche o **Designer de Projeto**. Isso é necessário porque a página **Serviços** atualizará automaticamente o arquivo App.config mesmo se você não modificar as configurações. Se você modificar manualmente o arquivo App.config, conforme descrito neste procedimento e, em seguida, retornar à página **Serviços**, suas modificações serão redefinidas.  
  
3.  No **Gerenciador de Soluções**, clique duas vezes em App.config.  
  
     O arquivo de configuração do aplicativo é aberto no editor de texto.  
  
4.  Encontre o elemento `<providers>` dentro do elemento `<membership>` ou `<roleManager>`. Esses elementos são filhos do elemento `<system.web>`. O elemento `<membership>` é usado para especificar provedores de autenticação e o elemento `<roleManager>` é usado para especificar os provedores de função.  
  
5.  Adicione um elemento `<add>` como um filho do elemento `<providers>`. Você deve especificar os atributos `name` e `type`, conforme mostrado no exemplo a seguir. O valor do atributo `type` deve ser um nome de tipo qualificado do assembly. Para obter mais informações, consulte <xref:System.Type.AssemblyQualifiedName%2A?displayProperty=fullName> e [Assembly Names](../../../docs/framework/app-domains/assembly-names.md) (Nomes de assembly).  
  
    ```xml  
    <add name="MyCustomRoleProvider" type="MyNamespace.MyRoleProvider, MyAssembly" />  
    ```  
  
6.  Modifique o atributo `defaultProvider` do elemento `<membership>` ou `<roleManager>` para especificar o valor do nome do elemento `<add>` adicionado na etapa anterior.  
  
    ```xml  
    <roleManager enabled="true" defaultProvider="MyCustomRoleProvider">  
    ```  
  
## <a name="see-also"></a>Consulte também  
 [Serviços de aplicativo cliente](../../../docs/framework/common-client-technologies/client-application-services.md)   
 [Visão geral dos serviços de aplicativo cliente](../../../docs/framework/common-client-technologies/client-application-services-overview.md)   
 [Página Serviços, Designer de Projeto](https://msdn.microsoft.com/library/bb398109)   
 [Configurações Avançadas para a Caixa de Diálogo Serviços](/visualstudio/ide/reference/advanced-settings-for-services-dialog-box)   
 [Como implementar o logon do usuário com os serviços de aplicativo cliente](../../../docs/framework/common-client-technologies/how-to-implement-user-login-with-client-application-services.md)   
 [Instruções passo a passo: usando serviços de aplicativo cliente](../../../docs/framework/common-client-technologies/walkthrough-using-client-application-services.md)   
 [Implementando um provedor de associação](http://msdn.microsoft.com/library/d8658b8e-c962-4f64-95e1-4acce35e4582)   
 [Implementando um provedor de função](http://msdn.microsoft.com/library/851671ce-bf9b-43f2-aba4-bc9d28b11c7d)   
 [Arquitetura das Configurações do Aplicativo](../../../docs/framework/winforms/advanced/application-settings-architecture.md)   
 [Criando e configurando o banco de dados dos serviços de aplicativos para o SQL Server](http://msdn.microsoft.com/library/ab894e83-7e2f-4af8-a116-b1bff8f815b2)

