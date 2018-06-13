---
title: 'Instruções passo a passo: usando serviços de aplicativo cliente'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application services host [client application services]
- client application services, walkthroughs
ms.assetid: bb7c8950-4517-4dae-b705-b74a14059b26
ms.openlocfilehash: 9193dc56a0f92daf486d95666ba820cb09d588d0
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32745364"
---
# <a name="walkthrough-using-client-application-services"></a>Instruções passo a passo: usando serviços de aplicativo cliente
Este tópico descreve como criar um aplicativo do Windows que usa serviços de aplicativo cliente para autenticar usuários e recuperar funções de usuário e configurações.  
  
 Nesta instrução passo a passo, as seguintes tarefas serão executadas:  
  
-   Crie um aplicativo do Windows Forms e use o Designer de Projeto do Visual Studio para habilitar e configurar serviços do aplicativo cliente.  
  
-   Crie um aplicativo de serviço Web ASP.NET simples para hospedar os serviços de aplicativo e testar a configuração do cliente.  
  
-   Adicione autenticação de formulários ao seu aplicativo. Você começará usando um nome de usuário embutidos em código e uma senha para testar o serviço. Você adicionará um formulário de logon especificando-o como um provedor de credenciais em sua configuração de aplicativo.  
  
-   Adicione a funcionalidade baseada em função, habilitando e exibindo um botão somente para os usuários na função "gerente".  
  
-   Acesse as configurações da Web. Você iniciará carregando configurações da Web para um usuário autenticado (teste) na página **Configurações** do designer de projeto. Em seguida, usará o Designer de Formulários do Windows para associar uma caixa de texto a uma configuração da Web. Finalmente, você salvará o valor modificado de volta para o servidor.  
  
-   Implemente o logout. Você adicionará uma opção de logoff ao formulário e chamará um método de logoff.  
  
-   Habilitar modo offline. Você fornecerá uma caixa de seleção para que os usuários possam especificar o status da conexão. Em seguida, você usará esse valor para especificar se os provedores de serviço de aplicativos cliente usarão os dados armazenados em cache localmente em vez de acessar seus serviços Web. Finalmente, você reautenticará o usuário atual quando o aplicativo retornar ao modo online.  
  
## <a name="prerequisites"></a>Pré-requisitos  
 Você precisa do seguinte componente para concluir esta instrução passo a passo:  
  
-   [!INCLUDE[vs_orcas_long](../../../includes/vs-orcas-long-md.md)].  
  
## <a name="creating-the-client-application"></a>Criando o aplicativo cliente  
 A primeira coisa que você fará é criar um projeto do Windows Forms. Este passo a passo usa o Windows Forms porque mais pessoas estão familiarizadas com ele, mas o processo é semelhante para projetos do Windows Presentation Foundation (WPF).  
  
#### <a name="to-create-a-client-application-and-enable-client-application-services"></a>Para criar um aplicativo cliente e habilitar serviços de aplicativo cliente  
  
1.  No Visual Studio, selecione a opção de menu **Arquivo &#124; Novo &#124; Projeto**.  
  
2.  Na caixa de diálogo **Novo Projeto** no painel **Tipos de Projeto**, expanda o nó **Visual Basic** ou **Visual C#** e selecione o tipo de projeto **Windows**.  
  
3.  Verifique se **.NET Framework 3.5** está selecionado e, em seguida, selecione o modelo **Aplicativo do Windows Forms**.  
  
4.  Altere o **Nome** do projeto para `ClientAppServicesDemo` e, em seguida, clique em **OK**.  
  
     Um novo projeto do Windows Forms será exibido no Visual Studio.  
  
5.  No menu **Projeto**, selecione **Propriedades do ClientAppServicesDemo**.  
  
     O designer de projeto é exibido.  
  
6.  Na guia **Serviços**, selecione **Habilitar serviços do aplicativo cliente**.  
  
7.  Verifique se **Usar autenticação de Formulários** está selecionado e, em seguida, defina **Local do serviço de autenticação**, **Local do serviço de funções** e **Local do serviço de configurações da Web** para `http://localhost:55555/AppServices`.  
  
8.  Para o Visual Basic, na guia **Aplicativo**, defina **Modo de autenticação** para **Definido pelo aplicativo**.  
  
 O designer armazena as configurações especificadas no arquivo app.config do aplicativo.  
  
 Neste ponto, o aplicativo está configurado para acessar todos os três serviços do mesmo host. Na próxima seção, você criará o host como um aplicativo simples de serviço Web, permitindo que você teste a configuração do cliente.  
  
## <a name="creating-the-application-services-host"></a>Criação do host dos serviços de aplicativo  
 Nesta seção, você criará um aplicativo simples de serviço Web que acessa dados do usuário de um arquivo de banco de dados local do SQL Server Compact. Em seguida, você preencherá o banco de dados usando a [ferramenta de Administração de Site do ASP.NET](http://msdn.microsoft.com/library/100ddd8b-7d11-4df9-91ef-0bbbe92e5aec). Esta configuração simples permite que você teste rapidamente o aplicativo cliente. Como alternativa, você pode configurar o host de serviço Web para acessar dados do usuário de um banco de dados completo do SQL Server ou por meio das classes personalizadas <xref:System.Web.Security.MembershipProvider> e <xref:System.Web.Security.RoleProvider>. Para saber mais, confira [Criação e configuração do banco de dados de serviços de aplicativo para o SQL Server](http://msdn.microsoft.com/library/ab894e83-7e2f-4af8-a116-b1bff8f815b2).  
  
 No procedimento a seguir, você criará e configurará o serviço Web AppServices.  
  
#### <a name="to-create-and-configure-the-application-services-host"></a>Para criar e configurar os serviços de aplicativo do host  
  
1.  No **Gerenciador de Soluções**, selecione a solução ClientAppServicesDemo e, em seguida, o menu **Arquivo**, selecione **Adicionar &#124; Novo Projeto**.  
  
2.  Na caixa de diálogo **Adicionar Novo Projeto** no painel **Tipos de Projeto**, expanda o nó **Visual Basic** ou **Visual C#** e selecione o tipo de projeto **Web**.  
  
3.  Verifique se **.NET Framework 3.5** está selecionado e, em seguida, selecione o modelo **Aplicativo de Serviço Web do ASP.NET**.  
  
4.  Altere o **Nome** do projeto para `AppServices` e, em seguida, clique em **OK**.  
  
     Um novo projeto de aplicativo de serviço Web do ASP.NET é adicionado à solução e o arquivo Service1.asmx.vb ou Service1.asmx.cs aparece no editor.  
  
    > [!NOTE]
    >  O arquivo Service1.asmx.vb ou Service1.asmx.cs não é usado neste exemplo. Se você quiser manter organizado a seu ambiente de trabalho, feche-o e o exclua do **Gerenciador de Soluções**.  
  
5.  No **Gerenciador de Soluções**, selecione o projeto AppServices e, em seguida, o menu **Projeto**, selecione **Propriedades do AppServices**.  
  
     O designer de projeto é exibido.  
  
6.  Na guia **Web**, verifique se **Usar o Visual Studio Development Server** está selecionado.  
  
7.  Selecione **Porta específica**, especifique um valor de `55555`e, em seguida, defina o **Caminho virtual** como `/AppServices`.  
  
8.  Salve todos os arquivos.  
  
9. No **Gerenciador de Soluções**, abra Web.config e localize a marca de abertura `<system.web>`.  
  
10. Adicione a seguinte marcação antes da marca `<system.web>`.  
  
     Os elementos `authenticationService`, `profileService` e `roleService` nessa marcação habilitam e configuram os serviços de aplicativo. Para fins de teste, o atributo `requireSSL` do elemento `authenticationService` é definido como "false". Os atributos `readAccessProperties` e `writeAccessProperties` do elemento `profileService` indicam que a propriedade `WebSettingsTestText` é leitura/gravação.  
  
    > [!NOTE]
    >  No código de produção, você sempre deve acessar o serviço de autenticação sobre o SSL (usando o protocolo HTTPS). Para saber mais sobre como configurar o SSL, confira [Configuração do SSL (Guia de Operações do IIS 6.0)](http://go.microsoft.com/fwlink/?LinkId=91844).  
  
    ```xml  
    <system.web.extensions>  
      <scripting>  
        <webServices>  
          <authenticationService enabled="true" requireSSL = "false"/>  
          <profileService enabled="true"  
            readAccessProperties="WebSettingsTestText"  
            writeAccessProperties="WebSettingsTestText" />  
          <roleService enabled="true"/>  
        </webServices>  
      </scripting>  
    </system.web.extensions>  
    ```  
  
11. Adicionar a marcação a seguir após a marca de abertura `<system.web>` para que ela esteja dentro do elemento `<system.web>`.  
  
     O elemento `profile` configura uma única configuração Web denominada `WebSettingsTestText`.  
  
    ```xml  
    <profile enabled="true" >  
      <properties>  
        <add name="WebSettingsTestText" type="string"   
          readOnly="false" defaultValue="DefaultText"   
          serializeAs="String" allowAnonymous="false" />  
      </properties>  
    </profile>  
    ```  
  
 No procedimento a seguir, você poderá usar a ferramenta de Administração de Site do ASP.NET para concluir a configuração do serviço e preencher o arquivo do banco de dados local. Você adicionará dois usuários chamados `employee` e `manager` que pertencem a duas funções com os mesmos nomes. As senhas de usuário são `employee!` e `manager!` respectivamente.  
  
#### <a name="to-configure-membership-and-roles"></a>Para configurar associação e funções  
  
1.  No **Gerenciador de Soluções**, selecione o projeto AppServices e, em seguida, o menu **Projeto**, selecione **Configuração do ASP.NET**.  
  
     A **ferramenta de Administração de Site do ASP.NET** é exibida.  
  
2.  Na guia **Segurança**, clique em **Usar o Assistente para Configuração da Segurança a fim de configurar a segurança, passo a passo**.  
  
     O **Assistente de configuração de segurança** aparece e exibe a etapa **Bem-vindo**.  
  
3.  Clique em **Avançar**.  
  
     A etapa **Selecionar método de acesso** é exibida.  
  
4.  Selecione **Pela Internet**. Isso configura o serviço para usar a autenticação de Formulários em vez da autenticação do Windows.  
  
5.  Clique em **Avançar** duas vezes.  
  
     A etapa **Definir funções** é exibida.  
  
6.  Selecione **Habilita as funções para este site**.  
  
7.  Clique em **Avançar**. O formulário **Criar Nova Função** é exibido.  
  
8.  Na caixa de texto **Nome da Nova Função**, digite `manager` e clique em **Adicionar Função**.  
  
     A tabela **Funções Existentes** aparece com o valor especificado.  
  
9. Na caixa de texto **Nome da Nova Função**, substitua `manager` por `employee` e clique em **Adicionar Função**.  
  
     O novo valor aparecerá na tabela **Funções Existentes**.  
  
10. Clique em **Avançar**.  
  
     A etapa **Adicionar Novos Usuários** é exibida.  
  
11. No formulário **Criar Usuário**, especifique os seguintes valores.  
  
  	|||  
  	|-|-|  
  	|**Nome de usuário**|`manager`|  
  	|**Senha**|`manager!`|  
  	|**Confirmar senha**|`manager!`|  
  	|**Email**|`manager@contoso.com`|  
  	|**Pergunta de Segurança**|`manager`|  
  	|**Resposta de Segurança**|`manager`|  
  
12. Clique em **Criar Usuário**.  
  
     Uma mensagem de êxito é exibida.  
  
    > [!NOTE]
    >  Os valores de **Email**, **Pergunta de Segurança** e **Resposta de Segurança** são exigidos pelo formulário, mas não são usados neste exemplo.  
  
13. Clique em **Continue**.  
  
     O formulário **Criar Usuário** será exibido novamente.  
  
14. No formulário **Criar Usuário**, especifique os seguintes valores.  
  
  	|||  
  	|-|-|  
  	|**Nome de usuário**|`employee`|  
  	|**Senha**|`employee!`|  
  	|**Confirmar senha**|`employee!`|  
  	|**Email**|`employee@contoso.com`|  
  	|**Pergunta de Segurança**|`Employee`|  
  	|**Resposta de Segurança**|`employee`|  
  
15. Clique em **Criar Usuário**.  
  
     Uma mensagem de êxito é exibida.  
  
16. Clique em **Finalizar**.  
  
     A **Ferramenta de Administração de Site** reaparece.  
  
17. Clique em **Gerenciar usuários**.  
  
     A lista de usuários é exibida.  
  
18. Clique em **Editar funções** para o usuário **Funcionário** e selecione a função **Funcionário**.  
  
19. Clique em **Editar funções** para o usuário **Gerente** e selecione a função **Gerente**.  
  
20. Feche a janela do navegador que hospeda a **ferramenta de Administração de Site**.  
  
21. Se uma caixa de mensagem é exibida perguntando se você deseja recarregar o arquivo Web.config modificado, clique em **Sim**.  
  
 Isso conclui a instalação do serviço Web. Neste ponto, você pode pressionar F5 para executar o aplicativo cliente e o **ASP.NET Development Server** será iniciado automaticamente junto com o aplicativo cliente. O servidor continuará a ser executado após você sair do aplicativo, mas será reiniciado quando você reiniciar o aplicativo. Isso permite que ele detecte as alterações feitas em Web.config.  
  
 Para parar o servidor manualmente, clique com o botão direito no ícone do ASP.NET Development Server na área de notificação da barra de tarefas e, em seguida, clique em **Parar**. Isso é útil ocasionalmente para garantir uma reinicialização limpa.  
  
## <a name="adding-forms-authentication"></a>Adicionar autenticação de Formulários  
 No procedimento a seguir, você adiciona código ao formulário principal que tenta validar o usuário e nega acesso quando o usuário fornece credenciais inválidas. Você usará um nome de usuário embutidos em código e uma senha para testar o serviço.  
  
#### <a name="to-validate-the-user-in-your-application-code"></a>Para validar o usuário no código do aplicativo  
  
1.  No **Gerenciador de Soluções**, no projeto ClientAppServicesDemo, adicione uma referência ao assembly System.Web.  
  
2.  Selecione o arquivo Formulário1 e escolha **Exibir &#124; Código**, no menu principal do Visual Studio.  
  
3.  No editor de códigos, adicione as seguintes declarações na parte superior do arquivo Form1.  
  
     [!code-csharp[ClientApplicationServices#001](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Form1.cs#001)]
     [!code-vb[ClientApplicationServices#001](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Form1.vb#001)]  
  
4.  No **Solution Explorer**, clique duas vezes em Form1 para exibir o designer.  
  
5.  No designer, clique duas vezes na superfície do formulário para gerar um manipulador de eventos <xref:System.Windows.Forms.Form.Load?displayProperty=nameWithType> chamado `Form1_Load`.  
  
     O editor de códigos é exibido com o cursor no método `Form1_Load`.  
  
6.  Adicione o seguinte código ao método de `Form1_Load` .  
  
     Esse código nega acesso a usuários não autenticados saindo do aplicativo. Como alternativa, você pode permitir que usuários não autenticados acessem o formulário, mas negar acesso à funcionalidade específica. Normalmente, você não embutirá no código o nome de usuário e a senha dessa maneira, mas é útil para fins de teste. Na próxima seção, você substituirá esse código por um código mais robusto que exibe uma caixa de diálogo de logon e inclui tratamento de exceção.  
  
     Observe que o método `static` <xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=nameWithType> está no [!INCLUDE[dnprdnext](../../../includes/dnprdnext-md.md)]. Este método delega seu trabalho para o provedor de autenticação configurado e retornará `true` se a autenticação for bem-sucedida. Seu aplicativo não exige uma referência direta para o provedor de autenticação do cliente.  
  
     [!code-csharp[ClientApplicationServices#300](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Class1.cs#300)]
     [!code-vb[ClientApplicationServices#300](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Class1.vb#300)]  
  
 Agora você pode pressionar F5 para executar o aplicativo e, como você forneceu nome de usuário e senha corretos, verá o formulário.  
  
> [!NOTE]
>  Se não for possível executar o aplicativo, tente interromper o ASP.NET Development Server. Quando o servidor for reiniciado, verifique se que a porta está definida para 55555.  
  
 Para ver a mensagem de erro em vez disso, altere os parâmetros <xref:System.Web.Security.Membership.ValidateUser%2A>. Por exemplo, substitua o segundo parâmetro `"manager!"` por uma senha incorreta, como `"MANAGER"`.  
  
## <a name="adding-a-login-form-as-a-credentials-provider"></a>Adição de um formulário de logon como provedor de credenciais  
 Você pode adquirir as credenciais do usuário no seu código do aplicativo e passá-los para o método <xref:System.Web.Security.Membership.ValidateUser%2A>. No entanto, geralmente é útil manter seu código de aquisição de credenciais separado do seu código do aplicativo, caso queira alterá-lo mais tarde.  
  
 No procedimento a seguir, você configura seu aplicativo para usar um provedor de credenciais e, em seguida, alterar sua chamada de método <xref:System.Web.Security.Membership.ValidateUser%2A> para passar <xref:System.String.Empty> para os dois parâmetros. As cadeias de caracteres vazias sinalizam o método <xref:System.Web.Security.Membership.ValidateUser%2A> para chamar o método <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider.GetCredentials%2A> do provedor de credenciais configurado.  
  
#### <a name="to-configure-your-application-to-use-a-credentials-provider"></a>Para configurar seu aplicativo para usar um provedor de credenciais  
  
1.  No **Gerenciador de Soluções**, selecione o projeto ClientAppServicesDemo e, em seguida, o menu **Projeto**, selecione **Propriedades do ClientAppServicesDemo**.  
  
     O designer de projeto é exibido.  
  
2.  Na guia **Serviços**, defina **Opcional: Provedor de credenciais** como o valor a seguir. Este valor indica o nome de tipo qualificado pelo assembly.  
  
    ```  
    ClientAppServicesDemo.Login, ClientAppServicesDemo  
    ```  
  
3.  No arquivo de código Form1, substitua o código no método `Form1_Load` pelo código a seguir.  
  
     Esse código exibe uma mensagem de boas-vindas e, em seguida, chama o método `ValidateUsingCredentialsProvider` que você adicionará na próxima etapa. Se o usuário não for autenticado, o método `ValidateUsingCredentialsProvider` retorna `false` e o método `Form1_Load` retorna. Isso impede que qualquer código adicional seja executado antes de sair do aplicativo. A mensagem de boas-vindas é útil para deixar claro quando o aplicativo é reiniciado. Você adicionará código para reiniciar o aplicativo quando implementar o logoff mais tarde nessa explicação passo a passo.  
  
     [!code-csharp[ClientApplicationServices#011](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Form1.cs#011)]
     [!code-vb[ClientApplicationServices#011](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Form1.vb#011)]  
  
4.  Adicione o seguinte método depois do método `Form1_Load`.  
  
     Esse método passa cadeias de caracteres vazias para o método `static` <xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=nameWithType>, que faz com que a caixa de diálogo Logon apareça. Se o serviço de autenticação não estiver disponível, o método <xref:System.Web.Security.Membership.ValidateUser%2A> gerará um <xref:System.Net.WebException>. Nesse caso, o método `ValidateUsingCredentialsProvider` exibe uma mensagem de aviso e pergunta se o usuário deseja tentar novamente no modo offline. Essa funcionalidade exige o recurso **Salvar o hash de senha localmente para habilitar o logon offline** descrito em [Como: configurar serviços de aplicativo cliente](../../../docs/framework/common-client-technologies/how-to-configure-client-application-services.md). Esse recurso é habilitado por padrão para novos projetos.  
  
     Se o usuário não for validado, o método `ValidateUsingCredentialsProvider` exibirá uma mensagem de erro e sairá do aplicativo. Por fim, esse método retorna o resultado da tentativa de autenticação.  
  
     [!code-csharp[ClientApplicationServices#020](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Form1.cs#020)]
     [!code-vb[ClientApplicationServices#020](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Form1.vb#020)]  
  
### <a name="creating-a-login-form"></a>Criação de um formulário de logon  
 Um provedor de credenciais é uma classe que implementa a interface <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider>. Essa interface tem um único método chamado <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider.GetCredentials%2A> que retorna um objeto <xref:System.Web.ClientServices.Providers.ClientFormsAuthenticationCredentials>. Os procedimentos a seguir descrevem como criar uma caixa de diálogo de logon que implementa <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider.GetCredentials%2A> para exibir a si próprio e retornar as credenciais especificadas pelo usuário.  
  
 Procedimentos separados são fornecidos para Visual Basic e C#, porque o Visual Basic oferece um modelo de **Formulário de Logon**. Isso economiza tempo e esforço de codificação.  
  
##### <a name="to-create-a-login-dialog-box-as-a-credentials-provider-in-visual-basic"></a>Para criar uma caixa de diálogo de logon como um provedor de credenciais no Visual Basic  
  
1.  No **Gerenciador de Soluções**, selecione o projeto ClientAppServicesDemo e, em seguida, o menu **Projeto**, selecione **Adicionar Novo Item**.  
  
2.  Na caixa de diálogo **Adicionar Novo Item**, selecione o modelo **Formulário de Logon**, altere o item **Nome** para `Login.vb` e, em seguida, clique em **Adicionar**.  
  
     A caixa de diálogo de logon é exibida no Designer de Formulários do Windows.  
  
3.  No designer, selecione o botão **OK** e, em seguida, na janela **Propriedades**, defina `DialogResult` como `OK`.  
  
4.  No designer, adicione um controle `CheckBox` ao formulário na caixa de texto **Senha**.  
  
5.  Na janela **Propriedades**, especifique um valor **(Nome)** de `rememberMeCheckBox` e um valor de **Texto** de `&Remember me`.  
  
6.  Selecione **Exibir &#124; Código**, no menu principal do Visual Studio.  
  
7.  No editor de códigos, adicione o seguinte código à parte superior do arquivo.  
  
     [!code-vb[ClientApplicationServices#101](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Login.vb#101)]  
  
8.  Modifique a assinatura de classe para que a classe implemente a interface <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider>.  
  
     [!code-vb[ClientApplicationServices#110](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Class1.vb#110)]  
  
9. Verifique se o cursor esteja depois de `IClientformsAuthenticationCredentialsProvider` e pressione ENTER para gerar o método `GetCredentials`.  
  
10. Localize a implementação <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider.GetCredentials%2A> e substitua-a pelo código a seguir.  
  
     [!code-vb[ClientApplicationServices#120](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Login.vb#120)]  
  
 O procedimento de C# a seguir fornece toda a listagem de código para uma caixa de diálogo de logon simples. O layout dessa caixa de diálogo é um pouco rudimentar, mas a parte importante é a implementação <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider.GetCredentials%2A>.  
  
##### <a name="to-create-a-login-dialog-box-as-a-credentials-provider-in-c"></a>Para criar uma caixa de diálogo de logon como um provedor de credenciais no C#  
  
1.  No **Gerenciador de Soluções**, selecione o projeto ClientAppServicesDemo e, em seguida, o menu **Projeto**, selecione **Adicionar Classe**.  
  
2.  Na caixa de diálogo **Adicionar novo item**, altere o **Nome** para `Login.cs` e clique em **Adicionar**.  
  
     O arquivo Login.cs é aberto no editor de códigos.  
  
3.  Substitua o código padrão pelo código a seguir.  
  
     [!code-csharp[ClientApplicationServices#200](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Login.cs#200)]  
  
 Agora você pode executar o aplicativo e ver a caixa de diálogo de logon aparecer. Para testar esse código, tente diferentes credenciais, válidas e inválidas, e confirme que você pode acessar o formulário somente com credenciais válidas. Nomes de usuário válidos são `employee` e `manager` com senhas `employee!` e `manager!` respectivamente.  
  
> [!NOTE]
>  Não selecione **Lembrar-me** nesse ponto ou você não poderá fazer logon como outro usuário até implementar o mais tarde nessa explicação passo a passo.  
  
## <a name="adding-role-based-functionality"></a>Adição de funcionalidade baseada em função  
 No procedimento a seguir, você adiciona um botão ao formulário e exibe-o somente para usuários na função de gerente.  
  
#### <a name="to-change-the-user-interface-based-on-user-role"></a>Para alterar a interface do usuário com base na função de usuário  
  
1.  No **Gerenciador de Soluções**, vá até o projeto ClientAppServicesDemo, selecione Formulário1 e escolha **Exibir &#124; Designer**, no menu principal do Visual Studio.  
  
2.  No designer, adicione um controle <xref:System.Windows.Forms.Button> ao formulário da **Caixa de Ferramentas**.  
  
3.  Na janela **Propriedades**, defina as seguintes propriedades para o botão.  
  
  	|propriedade|Valor|  
  	|--------------|-----------|  
  	|**(Nome)**|managerOnlyButton|  
  	|**Texto**|&Manager task|  
  	|**Visível**|`False`|  
  
4.  No editor de códigos para Form1, adicione o seguinte código ao final do método `Form1_Load`.  
  
     Esse código chama o método `DisplayButtonForManagerRole` que você adicionará na próxima etapa.  
  
     [!code-csharp[ClientApplicationServices#012](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Form1.cs#012)]
     [!code-vb[ClientApplicationServices#012](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Form1.vb#012)]  
  
5.  Adicione o seguinte método ao final da classe Form1.  
  
     Esse método chama o método <xref:System.Security.Principal.IPrincipal.IsInRole%2A> do <xref:System.Security.Principal.IPrincipal> retornado pela propriedade `static` <xref:System.Threading.Thread.CurrentPrincipal%2A?displayProperty=nameWithType>. Para aplicativos configurados para usar serviços de aplicativos cliente, essa propriedade retorna um <xref:System.Web.ClientServices.ClientRolePrincipal>. Como essa classe implementa a interface <xref:System.Security.Principal.IPrincipal>, você não precisa referenciá-la explicitamente.  
  
     Se o usuário está na função “manager”, o método `DisplayButtonForManagerRole` define a propriedade <xref:System.Windows.Forms.Control.Visible%2A> do `managerOnlyButton` para `true`. Esse método também exibe uma mensagem de erro se uma <xref:System.Net.WebException> for gerada, o que indica que o serviço de funções está indisponível.  
  
    > [!NOTE]
    >  O método <xref:System.Web.ClientServices.ClientRolePrincipal.IsInRole%2A> sempre retornará `false` se o logon do usuário tiver expirado. Isso não ocorrerá se o aplicativo chamar o método <xref:System.Security.Principal.IPrincipal.IsInRole%2A> uma vez logo depois da autenticação, conforme mostrado no código de exemplo para essa explicação passo a passo. Se seu aplicativo precisar recuperar funções de usuário em outros momentos, convém adicionar código para revalidar usuários cujo logon tiver expirado. Se todos os usuários válidos forem atribuídos às funções, você poderá determinar se o logon expirou chamando o método <xref:System.Web.ClientServices.Providers.ClientRoleProvider.GetRolesForUser%2A?displayProperty=nameWithType>. Se nenhuma função tiver sido retornada, isso significará que o logon expirou. Para ver um exemplo dessa funcionalidade, consulte o método <xref:System.Web.ClientServices.Providers.ClientRoleProvider.GetRolesForUser%2A>. Essa funcionalidade somente será necessária se você tiver selecionado **Exigir que os usuários façam logon novamente sempre que o cookie de servidor expirar** na configuração do aplicativo. Para obter mais informações, consulte [Como configurar serviços de aplicativo cliente](../../../docs/framework/common-client-technologies/how-to-configure-client-application-services.md).  
  
     [!code-csharp[ClientApplicationServices#030](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Form1.cs#030)]
     [!code-vb[ClientApplicationServices#030](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Form1.vb#030)]  
  
 Se a autenticação for bem-sucedida, o provedor de autenticação do cliente definirá a propriedade <xref:System.Threading.Thread.CurrentPrincipal%2A?displayProperty=nameWithType> para uma instância da classe <xref:System.Web.ClientServices.ClientRolePrincipal>. Essa classe implementa o método <xref:System.Security.Principal.IPrincipal.IsInRole%2A> para que o trabalho seja delegado ao provedor de função configurado. Como vimos antes, o código do seu aplicativo não exige uma referência direta para o provedor de serviço.  
  
 Agora você pode executar o aplicativo e fazer logon como funcionário para ver que o botão não aparece e, em seguida, fazer logon como gerente para ver o botão.  
  
## <a name="accessing-web-settings"></a>Acesso às configurações da Web  
 No procedimento a seguir, adicione uma caixa de texto ao formulário e vincule-o a uma configuração da Web. Como o código anterior que usa a autenticação e funções, seu código de configurações não acessa o provedor de configurações diretamente. Em vez disso, ele usa a classe `Settings` fortemente tipada (acessada como `Properties.Settings.Default` no C# e como `My.Settings` no Visual Basic), gerada para o projeto pelo Visual Studio.  
  
#### <a name="to-use-web-settings-in-your-user-interface"></a>Para usar as configurações da Web na interface do usuário  
  
1.  Verifique se o **ASP.NET Web Development Server** ainda está sendo executado verificando a área de notificação da barra de tarefas. Se você parar o servidor, reinicie o aplicativo (que inicia o servidor automaticamente), em seguida, feche a caixa de diálogo de logon.  
  
2.  No **Gerenciador de Soluções**, selecione o projeto ClientAppServicesDemo e, em seguida, o menu **Projeto**, selecione **Propriedades do ClientAppServicesDemo**.  
  
     O designer de projeto é exibido.  
  
3.  Na guia **Configurações**, clique em **Carregar Configurações da Web**.  
  
     Uma caixa de diálogo **Entrar** é exibida.  
  
4.  Insira as credenciais para funcionário ou gerente e clique em **Entrar**. A configuração da Web que você usará está configurada para acesso apenas por usuários autenticados, então clicar em **Ignorar Logon** não carregará as configurações.  
  
     A configuração `WebSettingsTestText` aparece no designer com o valor padrão de `DefaultText`. Além disso, uma classe `Settings` que contém uma propriedade `WebSettingsTestText` é gerada para o seu projeto.  
  
5.  No **Gerenciador de Soluções**, vá até o projeto ClientAppServicesDemo, selecione Formulário1 e escolha **Exibir &#124; Designer**, no menu principal do Visual Studio.  
  
6.  No designer, adicione um controle <xref:System.Windows.Forms.TextBox> ao formulário.  
  
7.  Na janela **Propriedades**, especifique um valor **(Nome)** de `webSettingsTestTextBox`.  
  
8.  No editor de códigos, adicione o seguinte código ao final do método `Form1_Load`.  
  
     Esse código chama o método `BindWebSettingsTestTextBox` que você adicionará na próxima etapa.  
  
     [!code-csharp[ClientApplicationServices#013](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Form1.cs#013)]
     [!code-vb[ClientApplicationServices#013](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Form1.vb#013)]  
  
9. Adicione o seguinte método ao final da classe Form1.  
  
     Este método associa a propriedade <xref:System.Windows.Forms.TextBox.Text%2A> do `webSettingsTestTextBox` para a propriedade `WebSettingsTestText` da classe `Settings` gerada anteriormente neste procedimento. Esse método também exibe uma mensagem de erro se uma <xref:System.Net.WebException> for gerada, o que indica que o serviço de configurações da Web está indisponível.  
  
     [!code-csharp[ClientApplicationServices#040](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Form1.cs#040)]
     [!code-vb[ClientApplicationServices#040](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Form1.vb#040)]  
  
    > [!NOTE]
    >  Normalmente você usará associação de dados para habilitar a comunicação bidirecional automática entre um controle e uma configuração da Web. No entanto, você também pode acessar as configurações da Web diretamente como mostrado no exemplo a seguir:  
  
     [!code-csharp[ClientApplicationServices#322](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Class1.cs#322)]
     [!code-vb[ClientApplicationServices#322](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Class1.vb#322)]  
  
10. No designer, selecione o formulário e, em seguida, na janela **Propriedades**, clique no botão **Eventos**.  
  
11. Selecione o evento <xref:System.Windows.Forms.Form.FormClosing> e pressione ENTER para gerar um manipulador de eventos.  
  
12. Substitua o método gerado pelo código a seguir.  
  
     O manipulador de eventos <xref:System.Windows.Forms.Form.FormClosing> chama o método `SaveSettings`, que também é usado pela funcionalidade logoff que você adicionará na próxima seção. O método `SaveSettings` primeiro confirma que o usuário não fez logoff. Ele faz isso verificando a propriedade <xref:System.Security.Principal.IIdentity.AuthenticationType%2A> do <xref:System.Security.Principal.IIdentity> retornado pela entidade atual. A entidade atual é recuperada por meio da propriedade `static` <xref:System.Threading.Thread.CurrentPrincipal%2A>. Se o usuário tiver sido autenticado para serviços de aplicativo cliente, o tipo de autenticação será "ClientForms". O método `SaveSettings` não pode apenas verificar a propriedade <xref:System.Security.Principal.IIdentity.IsAuthenticated%2A?displayProperty=nameWithType> porque o usuário pode ter uma identidade válida do Windows após o logoff.  
  
     Se o usuário não tiver feito logoff, o método `SaveSettings` chamará o método <xref:System.Configuration.ApplicationSettingsBase.Save%2A> da classe `Settings` gerada anteriormente neste procedimento. Esse método poderá gerar um <xref:System.Net.WebException> se o cookie de autenticação tiver expirado. Isso ocorrerá somente se você tiver selecionado **Exigir que os usuários façam logon novamente sempre que o cookie de servidor expirar** na configuração do aplicativo. Para obter mais informações, consulte [Como configurar serviços de aplicativo cliente](../../../docs/framework/common-client-technologies/how-to-configure-client-application-services.md). O método `SaveSettings` trata a expiração do cookie chamando <xref:System.Web.Security.Membership.ValidateUser%2A> para exibir a caixa de diálogo de logon. Se o usuário fizer logon com êxito, o método `SaveSettings` tentará salvar as configurações novamente chamando a si mesmo.  
  
     Como no código anterior, o método `SaveSettings` exibirá uma mensagem de erro se o serviço remoto não estiver disponível. Se o provedor de configurações não puder acessar o serviço remoto, as configurações ainda serão salvas no cache local e recarregadas quando o aplicativo for reiniciado.  
  
     [!code-csharp[ClientApplicationServices#050](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Form1.cs#050)]
     [!code-vb[ClientApplicationServices#050](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Form1.vb#050)]  
  
13. Adicione o seguinte método ao final da classe Form1.  
  
     Esse código manipula o evento <xref:System.Web.ClientServices.Providers.ClientSettingsProvider.SettingsSaved?displayProperty=nameWithType> e exibe um aviso se não for possível salvar alguma configuração. O evento <xref:System.Web.ClientServices.Providers.ClientSettingsProvider.SettingsSaved> não ocorrerá se o serviço configurações não estiver disponível ou se o cookie de autenticação tiver expirado. Um exemplo de quando o evento <xref:System.Web.ClientServices.Providers.ClientSettingsProvider.SettingsSaved> ocorre é quando o usuário já fez logoff. Você pode testar este manipulador de eventos adicionando código de logoff ao método `SaveSettings` diretamente antes da chamada do método <xref:System.Configuration.ApplicationSettingsBase.Save%2A>. O código de logoff que você pode usar está descrito na próxima seção.  
  
     [!code-csharp[ClientApplicationServices#090](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Form1.cs#090)]
     [!code-vb[ClientApplicationServices#090](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Form1.vb#090)]  
  
14. Para C#, adicione o código a seguir ao final do método `Form1_Load`. Esse código associa o método que você adicionou na etapa anterior com o evento <xref:System.Web.ClientServices.Providers.ClientSettingsProvider.SettingsSaved>.  
  
     [!code-csharp[ClientApplicationServices#015](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Form1.cs#015)]  
  
 Para testar o aplicativo neste ponto, execute-o várias vezes como funcionário e gerente, e digite valores diferentes na caixa de texto. Os valores persistirão em várias sessões de acordo com o usuário.  
  
## <a name="implementing-logout"></a>Implementação do logoff  
 Quando o usuário marcar a caixa de seleção **Lembrar-me** ao fazer logon, o aplicativo automaticamente autenticará o usuário nas execuções subsequentes. A autenticação automática continuará enquanto o aplicativo estiver no modo offline ou até que o cookie de autenticação tiver expirado. Às vezes, no entanto, vários usuários precisarão de acesso ao aplicativo ou um único usuário poderá ocasionalmente fazer logon com credenciais diferentes. Para habilitar esse cenário, você deverá implementar a funcionalidade de logoff, conforme descrito no procedimento a seguir.  
  
#### <a name="to-implement-logout-functionality"></a>Para implementar a funcionalidade de logoff  
  
1.  No designer do Form1, adicione um controle <xref:System.Windows.Forms.Button> ao formulário da **Caixa de Ferramentas**.  
  
2.  Na janela **Propriedades**, especifique um valor **(Nome)** de `logoutButton` e um valor de **Texto** de **&Logoff**.  
  
3.  Clique duas vezes no `logoutButton` para gerar um manipulador de eventos <xref:System.Windows.Forms.Control.Click>.  
  
     O editor de códigos é exibido com o cursor no método `logoutButton_Click`.  
  
4.  Substitua o método `logoutButton_Click` gerado pelo código a seguir.  
  
     Esse manipulador de eventos primeiro chama o método `SaveSettings` que você adicionou na seção anterior. Em seguida, o manipulador de eventos chama o método <xref:System.Web.ClientServices.Providers.ClientFormsAuthenticationMembershipProvider.Logout%2A?displayProperty=nameWithType>. Se o serviço de autenticação não estiver disponível, o método <xref:System.Web.ClientServices.Providers.ClientFormsAuthenticationMembershipProvider.Logout%2A> gerará um <xref:System.Net.WebException>. Nesse caso, o método `logoutButton_Click` exibe uma mensagem de aviso e muda temporariamente para o modo offline para desconectar o usuário. O modo offline será descrito na próxima seção.  
  
     O logoff exclui o cookie de autenticação local para que o logon seja necessário quando o aplicativo for reiniciado. Após o logoff, o manipulador de eventos reinicia o aplicativo. Quando o aplicativo for reiniciado, ele exibirá a mensagem de boas-vindas seguida pela caixa de diálogo de logon. A mensagem de boas-vindas deixa claro que o aplicativo foi reiniciado. Isso evitará confusão se o usuário precisar fazer logon para salvar as configurações e, em seguida, precisar fazer logon novamente porque o aplicativo foi reiniciado.  
  
     [!code-csharp[ClientApplicationServices#070](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Form1.cs#070)]
     [!code-vb[ClientApplicationServices#070](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Form1.vb#070)]  
  
 Para testar a funcionalidade de logoff, execute o aplicativo e selecione **Lembrar-me** na caixa de diálogo de logon. Em seguida, feche e reinicie o aplicativo para confirmar que você não precisa mais fazer logon. Finalmente, reinicie o aplicativo clicando em logoff.  
  
## <a name="enabling-offline-mode"></a>Como habilitar o modo offline  
 No procedimento a seguir, você adiciona uma caixa de seleção ao formulário para permitir que o usuário entre no modo offline. Seu aplicativo indica o modo offline, definindo a propriedade `static` <xref:System.Web.ClientServices.ConnectivityStatus.IsOffline%2A?displayProperty=nameWithType> para `true`. O status offline é armazenado no disco rígido local no local indicado pela propriedade <xref:System.Windows.Forms.Application.UserAppDataPath%2A?displayProperty=nameWithType>. Isso significa que o status offline é armazenado de acordo com o usuário e o aplicativo.  
  
 No modo offline, todas as solicitações de serviço de aplicativos cliente recuperam dados do cache local em vez de tentar acessar os serviços. Na configuração padrão, os dados locais incluem um formato criptografado da senha do usuário. Isso permite que o usuário faça logon enquanto o aplicativo estiver no modo offline. Para obter mais informações, consulte [Como configurar serviços de aplicativo cliente](../../../docs/framework/common-client-technologies/how-to-configure-client-application-services.md).  
  
#### <a name="to-enable-offline-mode-in-your-application"></a>Para habilitar o modo offline no seu aplicativo  
  
1.  No **Gerenciador de Soluções**, vá até o projeto ClientAppServicesDemo, selecione Formulário1 e escolha **Exibir &#124; Designer**, no menu principal do Visual Studio.  
  
2.  No designer, adicione um controle <xref:System.Windows.Forms.CheckBox> ao formulário.  
  
3.  Na janela **Propriedades**, especifique um valor **(Nome)** de `workOfflineCheckBox` e um valor de **Texto** de **&Trabalhar offline**.  
  
4.  Na janela **Propriedades**, clique no botão **Eventos**.  
  
5.  Selecione o evento <xref:System.Windows.Forms.CheckBox.CheckedChanged> e pressione ENTER para gerar um manipulador de eventos.  
  
6.  Substitua o método gerado pelo código a seguir.  
  
     Esse código atualiza o valor <xref:System.Web.ClientServices.ConnectivityStatus.IsOffline%2A> e revalida silenciosamente o usuário quando eles retornarem ao modo online. O método <xref:System.Web.ClientServices.ClientFormsIdentity.RevalidateUser%2A?displayProperty=nameWithType> usa as credenciais armazenadas em cache para que o usuário não precise entrar explicitamente. Se o serviço de autenticação não estiver disponível, será exibida uma mensagem de aviso e o aplicativo permanecerá offline.  
  
    > [!NOTE]
    >  O método <xref:System.Web.ClientServices.ClientFormsIdentity.RevalidateUser%2A> é apenas para conveniência. Como ele não tem um valor de retorno, não é possível indicar se a revalidação falhou. A revalidação pode falhar, por exemplo, se as credenciais do usuário tiverem sido alteradas no servidor. Nesse caso, você talvez queira incluir o código que valida usuários explicitamente após uma chamada de serviço falhar. Para saber mais, confira a seção Acesso às configurações da Web, anteriormente neste passo a passo.  
  
     Após revalidação, esse código salva as alterações às configurações locais da Web chamando o método `SaveSettings` que você adicionou anteriormente. Em seguida, ele recupera os novos valores no servidor chamando o método <xref:System.Configuration.ApplicationSettingsBase.Reload%2A> da classe `Settings` do projeto (acessada como `Properties.Settings.Default` em C# e `My.Settings` em Visual Basic).  
  
     [!code-csharp[ClientApplicationServices#080](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Form1.cs#080)]
     [!code-vb[ClientApplicationServices#080](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Form1.vb#080)]  
  
7.  Adicione o seguinte código ao final do método `Form1_Load` para ter certeza de que a caixa de seleção exibe o estado atual da conexão.  
  
     [!code-csharp[ClientApplicationServices#014](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Form1.cs#014)]
     [!code-vb[ClientApplicationServices#014](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Form1.vb#014)]  
  
 Isso conclui o aplicativo de exemplo. Para testar o recurso offline, execute o aplicativo, faça logon como funcionário ou gerente e, em seguida, selecione **Trabalhar offline**. Modifique o valor na caixa de texto e, em seguida, feche o aplicativo. Reinicialize o aplicativo. Antes de fazer logon, clique com o botão direito no ícone do ASP.NET Development Server na área de notificação da barra de tarefas e, em seguida, clique em **Parar**. Em seguida, faça logon normalmente. Mesmo quando o servidor não estiver em execução, você ainda poderá fazer logon. Modifique o valor da caixa de texto, saia e reinicie para ver o valor modificado.  
  
## <a name="summary"></a>Resumo  
 Neste passo a passo, você aprendeu a habilitar e usar os serviços de aplicativos cliente em um aplicativo do Windows Forms. Depois de configurar um servidor de teste, você adicionou o código ao seu aplicativo para autenticar usuários e recuperar funções de usuário e configurações de aplicativo do servidor. Você também aprendeu a habilitar o modo offline para que seu aplicativo use um cache de dados local em vez dos serviços remotos quando a conectividade não estiver disponível.  
  
## <a name="next-steps"></a>Próximas etapas  
 Em um aplicativo do mundo real, você acessará os dados para vários usuários de um servidor remoto que pode não estar sempre disponível ou pode parar de funcionar inesperadamente. Para deixar seu aplicativo robusto, você deverá responder adequadamente a situações onde o serviço não está disponível. Este passo a passo inclui blocos try/catch para capturar um <xref:System.Net.WebException> e exibir uma mensagem de erro quando o serviço não estiver disponível. No código de produção, você talvez queira manipular esse caso alternando para o modo offline, saindo do aplicativo ou negando acesso a funcionalidades específicas.  
  
 Para aumentar a segurança do seu aplicativo, teste o aplicativo e o servidor completamente antes da implantação.  
  
## <a name="see-also"></a>Consulte também  
 [Serviços de aplicativos cliente](../../../docs/framework/common-client-technologies/client-application-services.md)  
 [Visão geral dos serviços de aplicativos cliente](../../../docs/framework/common-client-technologies/client-application-services-overview.md)  
 [Como configurar serviços de aplicativo cliente](../../../docs/framework/common-client-technologies/how-to-configure-client-application-services.md)  
 [Ferramenta de Administração de Site ASP.NET](http://msdn.microsoft.com/library/100ddd8b-7d11-4df9-91ef-0bbbe92e5aec)  
 [Criando e configurando o banco de dados dos serviços de aplicativos para o SQL Server](http://msdn.microsoft.com/library/ab894e83-7e2f-4af8-a116-b1bff8f815b2)  
 [Instruções passo a passo: uso de serviços de aplicativo do ASP.NET](http://msdn.microsoft.com/library/f3f394f0-20d6-4361-aa8f-4b21bf4933eb)
