---
title: Considerações adicionais sobre segurança
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, secure calls to Windows API
- security [Windows Forms]
- security [Windows Forms], calling APIs
- Clipboard [Windows Forms], securing access
ms.assetid: 15abda8b-0527-47c7-aedb-77ab595f2bf1
ms.openlocfilehash: c8d51a57194f1dc536bc4b5d0376987dbfd3b2cf
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76739813"
---
# <a name="additional-security-considerations-in-windows-forms"></a>Considerações adicionais sobre Segurança do Windows Forms
.NET Framework configurações de segurança podem fazer com que seu aplicativo seja executado de forma diferente em um ambiente de confiança parcial do que no computador local. O .NET Framework restringe o acesso a recursos locais críticos como o sistema de arquivos, a rede e as APIs não gerenciadas, entre outras coisas. As configurações de segurança afetam a capacidade de chamar a API do Microsoft Windows ou outras APIs que não podem ser verificadas pelo sistema de segurança. A segurança também afeta outros aspectos do seu aplicativo, incluindo acesso a arquivos e dados e impressão. Para obter mais informações sobre o acesso a arquivos e dados em um ambiente de confiança parcial, consulte [acesso a dados e arquivos mais seguros em Windows Forms](more-secure-file-and-data-access-in-windows-forms.md). Para obter mais informações sobre como imprimir em um ambiente de confiança parcial, consulte [impressão mais segura em Windows Forms](more-secure-printing-in-windows-forms.md).  
  
 As seções a seguir discutem como trabalhar com a área de transferência, executar a manipulação de janela e chamar a API do Windows de aplicativos que estão sendo executados em um ambiente de confiança parcial.  
  
## <a name="clipboard-access"></a>Acesso à área de transferência  
 A classe <xref:System.Security.Permissions.UIPermission> controla o acesso à área de transferência e o valor de Enumeração associada <xref:System.Security.Permissions.UIPermissionClipboard> indica o nível de acesso. A tabela a seguir mostra os níveis de permissão possíveis.  
  
|Valor de UIPermissionClipboard|Descrição|  
|---------------------------------|-----------------|  
|<xref:System.Security.Permissions.UIPermissionClipboard.AllClipboard>|A área de transferência pode ser usada sem restrição.|  
|<xref:System.Security.Permissions.UIPermissionClipboard.OwnClipboard>|A área de transferência pode ser usada com algumas restrições. A capacidade de colocar dados na área de transferência (operações de comando copiar ou recortar) é irrestrita. Controles intrínsecos que aceitam colar, como uma caixa de texto, podem aceitar dados da área de transferência, mas os controles de usuário não podem ler programaticamente da área de transferência.|  
|<xref:System.Security.Permissions.UIPermissionClipboard.NoClipboard>|Não é possível usar a área de transferência.|  
  
 Por padrão, a zona da intranet local recebe <xref:System.Security.Permissions.UIPermissionClipboard.AllClipboard> acesso e a zona da Internet recebe acesso <xref:System.Security.Permissions.UIPermissionClipboard.OwnClipboard>. Isso significa que o aplicativo pode copiar dados para a área de transferência, mas o aplicativo não pode colar ou ler de forma programática a partir da área de transferência. Essas restrições impedem que programas sem confiança total leiam conteúdo copiado para a área de transferência por outro aplicativo. Se seu aplicativo exigir acesso completo à área de transferência, mas você não tiver as permissões, você precisará elevar as permissões para seu aplicativo. Para obter mais informações sobre como elevar permissões, consulte [Administração de política de segurança geral](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ed5htz45(v=vs.100)).  
  
## <a name="window-manipulation"></a>Manipulação de janela  
 A classe <xref:System.Security.Permissions.UIPermission> também controla a permissão para executar a manipulação de janela e outras ações relacionadas à interface do usuário, e o valor de enumeração associado <xref:System.Security.Permissions.UIPermissionWindow> indica o nível de acesso. A tabela a seguir mostra os níveis de permissão possíveis.  
  
 Por padrão, a zona da intranet local recebe <xref:System.Security.Permissions.UIPermissionWindow.AllWindows> acesso e a zona da Internet recebe acesso <xref:System.Security.Permissions.UIPermissionWindow.SafeTopLevelWindows>. Isso significa que, na zona da Internet, o aplicativo pode executar a maioria das ações da janela e da interface do usuário, mas a aparência da janela será modificada. A janela modificado exibe uma notificação de balão quando executada pela primeira vez, contém texto de barra de título modificado e requer um botão fechar na barra de título. A notificação de balão e a barra de título identificam o usuário do aplicativo que o aplicativo está executando sob confiança parcial.  
  
|Valor de UIPermissionWindow|Descrição|  
|------------------------------|-----------------|  
|<xref:System.Security.Permissions.UIPermissionWindow.AllWindows>|Os usuários podem usar todas as janelas e os eventos de entrada do usuário sem restrição.|  
|<xref:System.Security.Permissions.UIPermissionWindow.SafeTopLevelWindows>|Os usuários podem usar somente janelas de nível superior mais seguras e subjanelas mais seguras para desenhar e podem usar apenas eventos de entrada do usuário para a interface do usuário nessas janelas e subjanelas de nível superior. Essas janelas mais seguras são claramente rotuladas e têm restrições de tamanho mínimo e máximo. As restrições impedem ataques de falsificação potencialmente prejudiciais, como a imitação de telas de logon do sistema ou a área de trabalho do sistema, e restringem o acesso programático a janelas pai, APIs relacionadas ao foco e o uso do controle de <xref:System.Windows.Forms.ToolTip>,|  
|<xref:System.Security.Permissions.UIPermissionWindow.SafeSubWindows>|Os usuários podem usar somente subwindows mais seguros para desenhar e podem usar apenas eventos de entrada do usuário para a interface do usuário dentro dessa subjanela. Um controle exibido em um navegador é um exemplo de uma subjanela mais segura.|  
|<xref:System.Security.Permissions.UIPermissionWindow.NoWindows>|Os usuários não podem usar as janelas ou os eventos da interface do usuário. Nenhuma interface do usuário pode ser usada.|  
  
 Cada nível de permissão identificado pela enumeração de <xref:System.Security.Permissions.UIPermissionWindow> permite menos ações do que o nível acima. As tabelas a seguir indicam as ações que são restritas pelo <xref:System.Security.Permissions.UIPermissionWindow.SafeTopLevelWindows> e valores de <xref:System.Security.Permissions.UIPermissionWindow.SafeSubWindows>. Para obter permissões exatas que são necessárias para cada membro, consulte a referência para esse membro na documentação da biblioteca de classes do .NET Framework.  
  
 <xref:System.Security.Permissions.UIPermissionWindow.SafeTopLevelWindows> permissão restringe as ações listadas na tabela a seguir.  
  
|Componente|Ações restritas|  
|---------------|------------------------|  
|<xref:System.Windows.Forms.Application>|-Definindo a propriedade <xref:System.Windows.Forms.Application.SafeTopLevelCaptionFormat%2A>.|  
|<xref:System.Windows.Forms.Control>|-Obtendo a propriedade <xref:System.Windows.Forms.Control.Parent%2A>.<br />-Definindo a propriedade `Region`.<br />-Chamando o método <xref:System.Windows.Forms.Control.FindForm%2A>, <xref:System.Windows.Forms.Control.Focus%2A>, <xref:System.Windows.Forms.Control.FromChildHandle%2A> e <xref:System.Windows.Forms.Control.FromHandle%2A>, <xref:System.Windows.Forms.Control.PreProcessMessage%2A>, <xref:System.Windows.Forms.Control.ReflectMessage%2A>ou <xref:System.Windows.Forms.Control.SetTopLevel%2A>.<br />-Chamar o método <xref:System.Windows.Forms.Control.GetChildAtPoint%2A> se o controle retornado não for um filho do controle de chamada.<br />-Modificar o foco de controle dentro de um controle de contêiner.|  
|<xref:System.Windows.Forms.Cursor>|-Definindo a propriedade <xref:System.Windows.Forms.Cursor.Clip%2A>.<br />-Chamando o método <xref:System.Windows.Forms.Control.Hide%2A>.|  
|<xref:System.Windows.Forms.DataGrid>|-Chamando o método <xref:System.Windows.Forms.ContainerControl.ProcessTabKey%2A>.|  
|<xref:System.Windows.Forms.Form>|-Obtendo a propriedade <xref:System.Windows.Forms.Form.ActiveForm%2A> ou <xref:System.Windows.Forms.Form.MdiParent%2A>.<br />-Definindo a propriedade <xref:System.Windows.Forms.Form.ControlBox%2A>, <xref:System.Windows.Forms.Form.ShowInTaskbar%2A>ou <xref:System.Windows.Forms.Form.TopMost%2A>.<br />-Definindo a propriedade <xref:System.Windows.Forms.Form.Opacity%2A> abaixo de 50%.<br />-Definindo a propriedade <xref:System.Windows.Forms.Form.WindowState%2A> como <xref:System.Windows.Forms.FormWindowState.Minimized> programaticamente.<br />-Chamando o método <xref:System.Windows.Forms.Form.Activate%2A>.<br />-Usando o <xref:System.Windows.Forms.FormBorderStyle.None>, <xref:System.Windows.Forms.FormBorderStyle.FixedToolWindow>e <xref:System.Windows.Forms.FormBorderStyle.SizableToolWindow><xref:System.Windows.Forms.FormBorderStyle> valores de enumeração.|  
|<xref:System.Windows.Forms.NotifyIcon>|-O uso do componente <xref:System.Windows.Forms.NotifyIcon> é completamente restrito.|  
  
 O valor de <xref:System.Security.Permissions.UIPermissionWindow.SafeSubWindows> restringe as ações listadas na tabela a seguir, além das restrições colocadas pelo valor de <xref:System.Security.Permissions.UIPermissionWindow.SafeTopLevelWindows>.  
  
|Componente|Ações restritas|  
|---------------|------------------------|  
|<xref:System.Windows.Forms.CommonDialog>|-Mostrando uma caixa de diálogo derivada da classe <xref:System.Windows.Forms.CommonDialog>.|  
|<xref:System.Windows.Forms.Control>|-Chamando o método <xref:System.Windows.Forms.Control.CreateGraphics%2A>.<br />-Definindo a propriedade <xref:System.Windows.Forms.Control.Cursor%2A>.|  
|<xref:System.Windows.Forms.Control.Cursor%2A>|-Definindo a propriedade <xref:System.Windows.Forms.Cursor.Current%2A>.|  
|<xref:System.Windows.Forms.MessageBox>|-Chamando o método <xref:System.Windows.Forms.Form.Show%2A>.|  
  
### <a name="hosting-third-party-controls"></a>Hospedando controles de terceiros  
 Outro tipo de manipulação de janela pode ocorrer se seus formulários hospedarem controles de terceiros. Um controle de terceiros é qualquer <xref:System.Windows.Forms.UserControl> personalizado que você não tenha desenvolvido e compilado por conta própria. Embora o cenário de hospedagem seja difícil de explorar, é teoricamente possível que um controle de terceiros expanda sua superfície de renderização para cobrir toda a área do formulário. Esse controle poderia, então, imitar uma caixa de diálogo crítica e solicitar informações como combinações de nome de usuário/senha ou números de conta bancária de seus usuários.  
  
 Para limitar esse risco potencial, use controles de terceiros apenas de fornecedores nos quais você pode confiar. Se você usar controles de terceiros que você baixou de uma fonte não verificável, recomendamos que você examine o código-fonte em busca de possíveis explorações. Depois de verificar que a origem é não-mal-intencionada, você deve compilar o assembly por conta própria para garantir que a origem corresponda ao assembly.  
  
## <a name="windows-api-calls"></a>Chamadas à API do Windows  
 Se o design do aplicativo exigir a chamada de uma função da API do Windows, você está acessando código não gerenciado. Nesse caso, as ações do código para a janela ou sistema operacional não podem ser determinadas quando você está trabalhando com valores ou chamadas da API do Windows. A classe <xref:System.Security.Permissions.SecurityPermission> e o valor de <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode> da enumeração <xref:System.Security.Permissions.SecurityPermissionFlag> controlam o acesso ao código não gerenciado. Um aplicativo pode acessar código não gerenciado somente quando ele recebe a permissão <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode>. Por padrão, somente os aplicativos que estão sendo executados localmente podem chamar código não gerenciado.  
  
 Alguns membros de Windows Forms fornecem acesso não gerenciado que requer a permissão <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode>. A tabela a seguir lista os membros no namespace <xref:System.Windows.Forms> que exigem a permissão. Para obter mais informações sobre as permissões que são necessárias para um membro, consulte a documentação da biblioteca de classes .NET Framework.  
  
|Componente|{1&gt;Membro&lt;1}|  
|---------------|------------|  
|<xref:System.Windows.Forms.Application>|método de <xref:System.Windows.Forms.Application.AddMessageFilter%2A> de -   <br />-   <xref:System.Windows.Forms.Application.CurrentInputLanguage%2A> Propriedade<br />método de `Exit` de -   <br />método de <xref:System.Windows.Forms.Application.ExitThread%2A> de -   <br />evento de <xref:System.Windows.Forms.Application.ThreadException> de -   |  
|<xref:System.Windows.Forms.CommonDialog>|método de <xref:System.Windows.Forms.CommonDialog.HookProc%2A> de -   <br />-   <xref:System.Windows.Forms.CommonDialog.OwnerWndProc%2A>método<br />método de <xref:System.Windows.Forms.CommonDialog.Reset%2A> de -   <br />método de <xref:System.Windows.Forms.CommonDialog.RunDialog%2A> de -   |  
|<xref:System.Windows.Forms.Control>|método de <xref:System.Windows.Forms.Control.CreateParams%2A> de -   <br />método de <xref:System.Windows.Forms.Control.DefWndProc%2A> de -   <br />método de <xref:System.Windows.Forms.Control.DestroyHandle%2A> de -   <br />método de <xref:System.Windows.Forms.Control.WndProc%2A> de -   |  
|<xref:System.Windows.Forms.Help>|métodos de <xref:System.Windows.Forms.Help.ShowHelp%2A> -   <br />método de <xref:System.Windows.Forms.Help.ShowHelpIndex%2A> de -   |  
|<xref:System.Windows.Forms.NativeWindow>|classe de <xref:System.Windows.Forms.NativeWindow> de -   |  
|<xref:System.Windows.Forms.Screen>|método de <xref:System.Windows.Forms.Screen.FromHandle%2A> de -   |  
|<xref:System.Windows.Forms.SendKeys>|método de <xref:System.Windows.Forms.SendKeys.Send%2A> de -   <br />método de <xref:System.Windows.Forms.SendKeys.SendWait%2A> de -   |  
  
 Se seu aplicativo não tiver permissão para chamar código não gerenciado, seu aplicativo deverá solicitar <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode> permissão ou você deve considerar maneiras alternativas de implementar recursos; em muitos casos, o Windows Forms fornece uma alternativa gerenciada para funções de API do Windows. Se nenhum meio alternativo existir e o aplicativo precisar acessar o código não gerenciado, você precisará elevar as permissões para o aplicativo.  
  
 A permissão para chamar código não gerenciado permite que um aplicativo execute a maioria de qualquer coisa. Portanto, a permissão para chamar código não gerenciado só deve ser concedida para aplicativos provenientes de uma fonte confiável. Como alternativa, dependendo do aplicativo, a parte da funcionalidade do aplicativo que faz a chamada para código não gerenciado poderia ser opcional ou habilitada somente no ambiente de confiança total. Para obter mais informações sobre permissões perigosas, consulte [permissões perigosas e administração de diretivas](../misc/dangerous-permissions-and-policy-administration.md). Para obter mais informações sobre como elevar permissões, consulte [Administração de política de segurança geral](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ed5htz45(v=vs.100)).  
  
## <a name="see-also"></a>Veja também

- [Acesso mais seguro a arquivos e a dados nos Windows Forms](more-secure-file-and-data-access-in-windows-forms.md)
- [Impressão mais segura no Windows Forms](more-secure-printing-in-windows-forms.md)
- [Visão geral da segurança dos Windows Forms](security-in-windows-forms-overview.md)
- [Segurança do Windows Forms](windows-forms-security.md)
- [Protegendo aplicativos ClickOnce](/visualstudio/deployment/securing-clickonce-applications)
