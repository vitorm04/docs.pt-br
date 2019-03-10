---
title: 'Como: Adicionar ícones de aplicativo ao TaskBar com o componente NotifyIcon dos Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
f1_keywords:
- TrayIcon
helpviewer_keywords:
- status area icons
- icons [Windows Forms], adding to taskbar
- NotifyIcon component
- taskbar [Windows Forms], adding icons
ms.assetid: d28c0fe6-aaf2-4df7-ad74-928d861a8510
ms.openlocfilehash: 04f6b98a2206371a2838b3a6952feeafcd788309
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57714249"
---
# <a name="how-to-add-application-icons-to-the-taskbar-with-the-windows-forms-notifyicon-component"></a>Como: Adicionar ícones de aplicativo ao TaskBar com o componente NotifyIcon dos Windows Forms
Os formulários do Windows <xref:System.Windows.Forms.NotifyIcon> componente exibe um único ícone na área de notificação de status da barra de tarefas. Para exibir vários ícones na área de status, você deve ter vários <xref:System.Windows.Forms.NotifyIcon> componentes em seu formulário. Para definir o ícone exibido para um controle, use o <xref:System.Windows.Forms.NotifyIcon.Icon%2A> propriedade. Você também pode escrever código no <xref:System.Windows.Forms.NotifyIcon.DoubleClick> manipulador de eventos para que algo acontece quando o usuário clica duas vezes no ícone. Por exemplo, você pode fazer com que uma caixa de diálogo apareça para o usuário configurar o processo em segundo plano representado pelo ícone.  
  
> [!NOTE]
>  O <xref:System.Windows.Forms.NotifyIcon> componente é usado para fins de notificação apenas, para alertar os usuários que ocorreu um evento ou ação ou houve uma alteração no status de algum tipo. Você deve usar os menus, barras de ferramentas e outros elementos de interface do usuário para interação padrão com aplicativos.  
  
### <a name="to-set-the-icon"></a>Definir o ícone  
  
1.  Atribuir um valor para o <xref:System.Windows.Forms.NotifyIcon.Icon%2A> propriedade. O valor deve ser do tipo `System.Drawing.Icon` e pode ser carregados de um arquivo .ico. Você pode especificar o arquivo de ícone no código ou clicando no botão de reticências (![captura de tela VisualStudioEllipsesButton](../media/vbellipsesbutton.png "vbEllipsesButton")) ao lado de <xref:System.Windows.Forms.NotifyIcon.Icon%2A> propriedade no  **As propriedades** janela e, em seguida, selecionando o arquivo na **aberto** caixa de diálogo que aparece.  
  
2.  Defina a propriedade <xref:System.Windows.Forms.NotifyIcon.Visible%2A> como `true`.  
  
3.  Defina o <xref:System.Windows.Forms.NotifyIcon.Text%2A> propriedade como uma cadeia de caracteres de dica de ferramenta apropriada.  
  
     No exemplo de código a seguir, o caminho definido para o local do ícone é a pasta **Meus Documentos**. Esse local é usado porque você pode supor que a maioria dos computadores que executam o sistema operacional Windows incluem essa pasta. Escolher esse local também permite que os usuários com níveis mínimos de acesso ao sistema executem o aplicativo com mais segurança. O exemplo a seguir exige um formulário com um <xref:System.Windows.Forms.NotifyIcon> controle já adicionado. Ele também requer um arquivo de ícone denominado `Icon.ico`.  
  
    ```vb  
    ' You should replace the bold icon in the sample below  
    ' with an icon of your own choosing.  
    NotifyIcon1.Icon = New _   
       System.Drawing.Icon(System.Environment.GetFolderPath _  
       (System.Environment.SpecialFolder.Personal) _  
       & "\Icon.ico")  
    NotifyIcon1.Visible = True  
    NotifyIcon1.Text = "Antivirus program"  
    ```  
  
    ```csharp  
    // You should replace the bold icon in the sample below  
    // with an icon of your own choosing.  
    // Note the escape character used (@) when specifying the path.  
    notifyIcon1.Icon =   
       new System.Drawing.Icon (System.Environment.GetFolderPath  
       (System.Environment.SpecialFolder.Personal)  
       + @"\Icon.ico");  
    notifyIcon1.Visible = true;  
    notifyIcon1.Text = "Antivirus program";  
    ```  
  
    ```cpp  
    // You should replace the bold icon in the sample below  
    // with an icon of your own choosing.  
    notifyIcon1->Icon = gcnew   
       System::Drawing::Icon(String::Concat  
       (System::Environment::GetFolderPath  
       (System::Environment::SpecialFolder::Personal),  
       "\\Icon.ico"));  
    notifyIcon1->Visible = true;  
    notifyIcon1->Text = "Antivirus program";  
    ```  
  
## <a name="see-also"></a>Consulte também
- <xref:System.Windows.Forms.NotifyIcon>
- <xref:System.Windows.Forms.NotifyIcon.Icon%2A>
- [Como: Associar um Menu de atalho um componente NotifyIcon dos Windows Forms](how-to-associate-a-shortcut-menu-with-a-windows-forms-notifyicon-component.md)
- [Componente NotifyIcon](notifyicon-component-windows-forms.md)
- [Visão geral do componente NotifyIcon](notifyicon-component-overview-windows-forms.md)
