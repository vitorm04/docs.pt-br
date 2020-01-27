---
title: Adicionar ícones de aplicativo à barra de tarefas com o componente NotifyIcon
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
ms.openlocfilehash: 46b50ecaabe75dba08fea922d7b5639031692269
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746253"
---
# <a name="how-to-add-application-icons-to-the-taskbar-with-the-windows-forms-notifyicon-component"></a>Como adicionar ícones de aplicativo ao TaskBar com o componente NotifyIcon dos Windows Forms

O componente Windows Forms <xref:System.Windows.Forms.NotifyIcon> exibe um único ícone na área de notificação de status da barra de tarefas. Para exibir vários ícones na área de status, você deve ter vários componentes <xref:System.Windows.Forms.NotifyIcon> no formulário. Para definir o ícone exibido para um controle, use a propriedade <xref:System.Windows.Forms.NotifyIcon.Icon%2A>. Você também pode escrever código no manipulador de eventos <xref:System.Windows.Forms.NotifyIcon.DoubleClick> para que algo aconteça quando o usuário clicar duas vezes no ícone. Por exemplo, você pode fazer com que uma caixa de diálogo apareça para o usuário configurar o processo em segundo plano representado pelo ícone.

> [!NOTE]
> O componente <xref:System.Windows.Forms.NotifyIcon> é usado apenas para fins de notificação, para alertar os usuários de que uma ação ou evento ocorreu ou houve uma alteração no status de algum tipo. Você deve usar os menus, barras de ferramentas e outros elementos de interface do usuário para interação padrão com aplicativos.

### <a name="to-set-the-icon"></a>Definir o ícone

1. Atribua um valor à propriedade <xref:System.Windows.Forms.NotifyIcon.Icon%2A>. O valor deve ser do tipo `System.Drawing.Icon` e pode ser carregados de um arquivo .ico. Você pode especificar o arquivo de ícone no código ou clicando no botão de reticências (![botão de reticências (...) na janela Propriedades do Visual Studio.](./media/visual-studio-ellipsis-button.png)) ao lado da propriedade <xref:System.Windows.Forms.NotifyIcon.Icon%2A> na janela **Propriedades** e, em seguida, selecionando o arquivo na caixa de diálogo **abrir** que aparece.

2. Defina a propriedade <xref:System.Windows.Forms.NotifyIcon.Visible%2A> como `true`.

3. Defina a propriedade <xref:System.Windows.Forms.NotifyIcon.Text%2A> como uma cadeia de dica de ferramenta apropriada.

     No exemplo de código a seguir, o caminho definido para o local do ícone é a pasta **Meus Documentos**. Esse local é usado porque você pode supor que a maioria dos computadores que executam o sistema operacional Windows inclui essa pasta. Escolher esse local também permite que os usuários com níveis mínimos de acesso ao sistema executem o aplicativo com mais segurança. O exemplo a seguir requer um formulário com um controle <xref:System.Windows.Forms.NotifyIcon> já adicionado. Ele também requer um arquivo de ícone denominado `Icon.ico`.

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

## <a name="see-also"></a>Veja também

- <xref:System.Windows.Forms.NotifyIcon>
- <xref:System.Windows.Forms.NotifyIcon.Icon%2A>
- [Como associar um menu de atalho a um componente NotifyIcon dos Windows Forms](how-to-associate-a-shortcut-menu-with-a-windows-forms-notifyicon-component.md)
- [Componente NotifyIcon](notifyicon-component-windows-forms.md)
- [Visão geral do componente NotifyIcon](notifyicon-component-overview-windows-forms.md)
