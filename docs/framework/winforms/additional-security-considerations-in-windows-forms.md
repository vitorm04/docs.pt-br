---
title: "Considerações adicionais sobre Segurança do Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Forms, secure calls to Windows API
- security [Windows Forms]
- security [Windows Forms], calling APIs
- Clipboard [Windows Forms], securing access
ms.assetid: 15abda8b-0527-47c7-aedb-77ab595f2bf1
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 874bd286ec7dbafb95df1726fdc902b0ab7716e5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="additional-security-considerations-in-windows-forms"></a>Considerações adicionais sobre Segurança do Windows Forms
[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]configurações de segurança podem fazer com que seu aplicativo para execução de maneira diferente em um ambiente de confiança parcial que no computador local. O [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] restringe o acesso a esses recursos locais críticos como o sistema de arquivos, rede e APIs não gerenciadas, entre outras coisas. As configurações de segurança afetam a capacidade de chamar a API do Microsoft Win32 ou outras APIs que não pode ser verificado pelo sistema de segurança. A segurança também afeta outros aspectos do seu aplicativo, incluindo acesso a dados e de arquivo e impressão. Para obter mais informações sobre o acesso a arquivos e dados em um ambiente de confiança parcial, consulte [arquivo mais seguro e acesso a dados em formulários do Windows](../../../docs/framework/winforms/more-secure-file-and-data-access-in-windows-forms.md). Para obter mais informações sobre a impressão em um ambiente de confiança parcial, consulte [mais seguro impressão no Windows Forms](../../../docs/framework/winforms/more-secure-printing-in-windows-forms.md).  
  
 As seções a seguir discutem como trabalhar com a área de transferência, executar a manipulação de janela e chamar a API do Win32 de aplicativos que são executados em um ambiente de confiança parcial.  
  
## <a name="clipboard-access"></a>Acesso de área de transferência  
 O <xref:System.Security.Permissions.UIPermission> classe controla o acesso à área de transferência e associado <xref:System.Security.Permissions.UIPermissionClipboard> valor de enumeração indica o nível de acesso. A tabela a seguir mostra os níveis de permissão possíveis.  
  
|Valor de UIPermissionClipboard|Descrição|  
|---------------------------------|-----------------|  
|<xref:System.Security.Permissions.UIPermissionClipboard.AllClipboard>|A área de transferência pode ser usada sem restrição.|  
|<xref:System.Security.Permissions.UIPermissionClipboard.OwnClipboard>|A área de transferência pode ser usada com algumas restrições. A capacidade de colocar dados na área de transferência (operações de comando Recortar ou copiar) é irrestrita. Controles intrínsecos que aceitam colar, como uma caixa de texto, podem aceitar dados de área de transferência, mas controles de usuário por meio de programação não é possível ler da área de transferência.|  
|<xref:System.Security.Permissions.UIPermissionClipboard.NoClipboard>|A área de transferência não pode ser usada.|  
  
 Por padrão, a zona de Intranet Local recebe <xref:System.Security.Permissions.UIPermissionClipboard.AllClipboard> acesso e a zona da Internet recebe <xref:System.Security.Permissions.UIPermissionClipboard.OwnClipboard> acesso. Isso significa que o aplicativo pode copiar dados para a área de transferência, mas o aplicativo por meio de programação não é possível colar ou ler da área de transferência. Essas restrições impedem que programas sem confiança leiam conteúdo copiados para a área de transferência por outro aplicativo. Se seu aplicativo requer acesso total à área de transferência, mas você não tem as permissões, você terá que elevar as permissões para seu aplicativo. Para obter mais informações sobre como elevar permissões, consulte [administração geral de política de segurança](http://msdn.microsoft.com/en-us/5121fe35-f0e3-402c-94ab-4f35b0a87b4b).  
  
## <a name="window-manipulation"></a>Manipulação de janelas  
 O <xref:System.Security.Permissions.UIPermission> classe também controla a permissão para executar a manipulação de janelas e outras ações relacionadas à interface do usuário e associado <xref:System.Security.Permissions.UIPermissionWindow> valor de enumeração indica o nível de acesso. A tabela a seguir mostra os níveis de permissão possíveis.  
  
 Por padrão, a zona de Intranet Local recebe <xref:System.Security.Permissions.UIPermissionWindow.AllWindows> acesso e a zona da Internet recebe <xref:System.Security.Permissions.UIPermissionWindow.SafeTopLevelWindows> acesso. Isso significa que na zona da Internet, o aplicativo pode executar a maioria das janelas e ações de interface do usuário, mas a aparência da janela será modificada. A janela modificada exibe uma notificação de balão quando executado pela primeira vez, contém o texto da barra de título modificado e requer um botão Fechar na barra de título. A notificação de balão e a barra de título identificam para o usuário do aplicativo que o aplicativo está executando em confiança parcial.  
  
|Valor de UIPermissionWindow|Descrição|  
|------------------------------|-----------------|  
|<xref:System.Security.Permissions.UIPermissionWindow.AllWindows>|Os usuários podem usar todas as janelas e os eventos de entrada do usuário sem restrição.|  
|<xref:System.Security.Permissions.UIPermissionWindow.SafeTopLevelWindows>|Os usuários podem usar apenas mais segura de nível superior e subjanelas seguras para desenho e podem usar somente os eventos entrada do usuário para a interface do usuário dentro dessas janelas de nível superior e subjanelas. Essas janelas seguras são rotuladas claramente e têm restrições de tamanho mínimo e máximo. As restrições impedem ataques de falsificação potencialmente prejudiciais, como imitar telas de logon do sistema ou a área de trabalho do sistema e restringe o acesso programático ao pai do windows, APIs relacionadas a foco e uso do <xref:System.Windows.Forms.ToolTip> controle|  
|<xref:System.Security.Permissions.UIPermissionWindow.SafeSubWindows>|Os usuários podem somente usar subjanelas seguras para desenho e podem usar somente os eventos entrada do usuário para a interface do usuário dentro desta subjanela. Um controle exibido dentro de um navegador é um exemplo de uma subjanela segura.|  
|<xref:System.Security.Permissions.UIPermissionWindow.NoWindows>|Os usuários não podem usar as janelas ou os eventos da interface do usuário. Nenhuma interface do usuário pode ser usada.|  
  
 Cada nível de permissão identificado pelo <xref:System.Security.Permissions.UIPermissionWindow> enumeração permite menos ações do que o nível acima dele. As tabelas a seguir indicam as ações que são restritos pelo <xref:System.Security.Permissions.UIPermissionWindow.SafeTopLevelWindows> e <xref:System.Security.Permissions.UIPermissionWindow.SafeSubWindows> valores. Para obter as permissões exatas que são necessárias para cada membro, consulte a referência para esse membro na documentação da biblioteca de classe do .NET Framework.  
  
 <xref:System.Security.Permissions.UIPermissionWindow.SafeTopLevelWindows>a permissão restringe as ações listadas na tabela a seguir.  
  
|Componente|Ações restritas|  
|---------------|------------------------|  
|<xref:System.Windows.Forms.Application>|-Definir o <xref:System.Windows.Forms.Application.SafeTopLevelCaptionFormat%2A> propriedade.|  
|<xref:System.Windows.Forms.Control>|-Obtendo o <xref:System.Windows.Forms.Control.Parent%2A> propriedade.<br />-Definir o `Region` propriedade.<br />-Chamando o <xref:System.Windows.Forms.Control.FindForm%2A> , <xref:System.Windows.Forms.Control.Focus%2A>, <xref:System.Windows.Forms.Control.FromChildHandle%2A> e <xref:System.Windows.Forms.Control.FromHandle%2A>, <xref:System.Windows.Forms.Control.PreProcessMessage%2A>, <xref:System.Windows.Forms.Control.ReflectMessage%2A>, ou <xref:System.Windows.Forms.Control.SetTopLevel%2A> método.<br />-Ao chamar o <xref:System.Windows.Forms.Control.GetChildAtPoint%2A> método se o controle retornado não é um filho do controle de chamada.<br />-Modificar o foco do controle dentro de um controle de contêiner.|  
|<xref:System.Windows.Forms.Cursor>|-Definir o <xref:System.Windows.Forms.Cursor.Clip%2A> propriedade.<br />-Ao chamar o <xref:System.Windows.Forms.Control.Hide%2A> método.|  
|<xref:System.Windows.Forms.DataGrid>|-Ao chamar o <xref:System.Windows.Forms.ContainerControl.ProcessTabKey%2A> método.|  
|<xref:System.Windows.Forms.Form>|-Obtendo o <xref:System.Windows.Forms.Form.ActiveForm%2A> ou <xref:System.Windows.Forms.Form.MdiParent%2A> propriedade.<br />-Definir o <xref:System.Windows.Forms.Form.ControlBox%2A>, <xref:System.Windows.Forms.Form.ShowInTaskbar%2A>, ou <xref:System.Windows.Forms.Form.TopMost%2A> propriedade.<br />-Definir o <xref:System.Windows.Forms.Form.Opacity%2A> propriedade abaixo de 50%.<br />-Definir o <xref:System.Windows.Forms.Form.WindowState%2A> propriedade <xref:System.Windows.Forms.FormWindowState.Minimized> programaticamente.<br />-Ao chamar o <xref:System.Windows.Forms.Form.Activate%2A> método.<br />-O usando o <xref:System.Windows.Forms.FormBorderStyle.None>, <xref:System.Windows.Forms.FormBorderStyle.FixedToolWindow>, e <xref:System.Windows.Forms.FormBorderStyle.SizableToolWindow> <xref:System.Windows.Forms.FormBorderStyle> valores de enumeração.|  
|<xref:System.Windows.Forms.NotifyIcon>|-O usando o <xref:System.Windows.Forms.NotifyIcon> componente é totalmente restrito.|  
  
 O <xref:System.Security.Permissions.UIPermissionWindow.SafeSubWindows> valor restringe as ações listadas na tabela a seguir, além disso, as restrições colocadas pelo <xref:System.Security.Permissions.UIPermissionWindow.SafeTopLevelWindows> valor.  
  
|Componente|Ações restritas|  
|---------------|------------------------|  
|<xref:System.Windows.Forms.CommonDialog>|-Mostrar uma caixa de diálogo derivado de <xref:System.Windows.Forms.CommonDialog> classe.|  
|<xref:System.Windows.Forms.Control>|-Ao chamar o <xref:System.Windows.Forms.Control.CreateGraphics%2A> método.<br />-Definir o <xref:System.Windows.Forms.Control.Cursor%2A> propriedade.|  
|<xref:System.Windows.Forms.Control.Cursor%2A>|-Definir o <xref:System.Windows.Forms.Cursor.Current%2A> propriedade.|  
|<xref:System.Windows.Forms.MessageBox>|-Ao chamar o <xref:System.Windows.Forms.Form.Show%2A> método.|  
  
### <a name="hosting-third-party-controls"></a>Hospedando controles de terceiros  
 Outro tipo de manipulação de janela pode ocorrer se os formulários hospedarem controles de terceiros. Um controle de terceiros é qualquer custom <xref:System.Windows.Forms.UserControl> que você não tenha desenvolvido e compilado você mesmo. Embora o cenário de hospedagem é difícil de explorar, é teoricamente possível para um controle de terceiros expandir sua superfície de renderização para cobrir toda a área do formulário. Este controle pode simular uma caixa de diálogo crítica e solicitar informações como números de conta bancária ou combinações de nome de usuário/senha dos usuários.  
  
 Para limitar esse risco em potencial, use os controles de terceiros apenas de fornecedores que você pode confiar. Se você usar controles de terceiros que você baixou a partir de uma fonte não verificável, recomendamos que você examine o código-fonte para possíveis explorações. Depois de verificar que a origem é não mal-intencionado, você deve compilar o assembly para garantir que a fonte corresponda ao assembly.  
  
## <a name="win32-api-calls"></a>Chamadas de API do Win32  
 Se o projeto de aplicativo requer chamando uma função de API do Win32, você está acessando código não gerenciado. Nesse caso as ações do código para o sistema operacional ou a janela não podem ser determinadas quando você estiver trabalhando com valores ou chamadas de API do Win32. O <xref:System.Security.Permissions.SecurityPermission> classe e o <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode> valor o <xref:System.Security.Permissions.SecurityPermissionFlag> acesso de controle de enumeração para código não gerenciado. Um aplicativo pode acessar código não gerenciado apenas quando ele recebe o <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode> permissão. Por padrão, somente aplicativos que estão sendo executados localmente podem chamar código não gerenciado.  
  
 Alguns membros de formulários do Windows fornecem um acesso não gerenciado que requer o <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode> permissão. A tabela a seguir lista os membros de <xref:System.Windows.Forms> namespace que exigem a permissão. Para obter mais informações sobre as permissões que são necessárias para um membro, consulte a documentação da biblioteca de classe do .NET Framework.  
  
|Componente|Membro|  
|---------------|------------|  
|<xref:System.Windows.Forms.Application>|-   <xref:System.Windows.Forms.Application.AddMessageFilter%2A>método<br />-   <xref:System.Windows.Forms.Application.CurrentInputLanguage%2A>propriedade<br />-   `Exit`método<br />-   <xref:System.Windows.Forms.Application.ExitThread%2A>método<br />-   <xref:System.Windows.Forms.Application.ThreadException>evento|  
|<xref:System.Windows.Forms.CommonDialog>|-   <xref:System.Windows.Forms.CommonDialog.HookProc%2A>método<br />-   <xref:System.Windows.Forms.CommonDialog.OwnerWndProc%2A>\ método<br />-   <xref:System.Windows.Forms.CommonDialog.Reset%2A>método<br />-   <xref:System.Windows.Forms.CommonDialog.RunDialog%2A>método|  
|<xref:System.Windows.Forms.Control>|-   <xref:System.Windows.Forms.Control.CreateParams%2A>método<br />-   <xref:System.Windows.Forms.Control.DefWndProc%2A>método<br />-   <xref:System.Windows.Forms.Control.DestroyHandle%2A>método<br />-   <xref:System.Windows.Forms.Control.WndProc%2A>método|  
|<xref:System.Windows.Forms.Help>|-   <xref:System.Windows.Forms.Help.ShowHelp%2A>métodos<br />-   <xref:System.Windows.Forms.Help.ShowHelpIndex%2A>método|  
|<xref:System.Windows.Forms.NativeWindow>|-   <xref:System.Windows.Forms.NativeWindow>classe|  
|<xref:System.Windows.Forms.Screen>|-   <xref:System.Windows.Forms.Screen.FromHandle%2A>método|  
|<xref:System.Windows.Forms.SendKeys>|-   <xref:System.Windows.Forms.SendKeys.Send%2A>método<br />-   <xref:System.Windows.Forms.SendKeys.SendWait%2A>método|  
  
 Se seu aplicativo não tem permissão para chamar código não gerenciado, seu aplicativo deve solicitar <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode> permissão, ou você deve considerar maneiras alternativas de implementar recursos; em muitos casos, o Windows Forms fornece uma alternativa gerenciada para API do Win32 funções. Se existe nenhum meio alternativo e o aplicativo deve acessar código não gerenciado, você terá que elevar as permissões para o aplicativo.  
  
 Permissão para chamar código não gerenciado permite que um aplicativo execute quase qualquer coisa. Portanto, permissão para chamar código não gerenciado deve ser concedida somente para aplicativos que vêm de uma fonte confiável. Como alternativa, dependendo do aplicativo, a parte da funcionalidade do aplicativo que faz a chamada para código não gerenciado poderia ser opcional, ou ativada no ambiente de confiança total somente. Para obter mais informações sobre permissões perigosas, consulte [permissões perigosas e administração de políticas](../../../docs/framework/misc/dangerous-permissions-and-policy-administration.md). Para obter mais informações sobre como elevar permissões, consulte [NIB: administração geral de política de segurança](http://msdn.microsoft.com/en-us/5121fe35-f0e3-402c-94ab-4f35b0a87b4b).  
  
## <a name="see-also"></a>Consulte também  
 [Acesso mais seguro a arquivos e a dados nos Windows Forms](../../../docs/framework/winforms/more-secure-file-and-data-access-in-windows-forms.md)  
 [Impressão mais segura no Windows Forms](../../../docs/framework/winforms/more-secure-printing-in-windows-forms.md)  
 [Visão geral da segurança dos Windows Forms](../../../docs/framework/winforms/security-in-windows-forms-overview.md)  
 [Segurança do Windows Forms](../../../docs/framework/winforms/windows-forms-security.md)  
 [Protegendo aplicativos ClickOnce](/visualstudio/deployment/securing-clickonce-applications)
