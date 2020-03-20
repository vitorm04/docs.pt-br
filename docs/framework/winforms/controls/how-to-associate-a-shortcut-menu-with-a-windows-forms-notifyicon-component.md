---
title: Associar um menu de atalho com o componente NotificarÍcone
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- context menus [Windows Forms], for background processes
- NotifyIcon component [Windows Forms], associating shortcut menus
- shortcut menus [Windows Forms], for background processes
ms.assetid: d68f3926-08d3-4f7d-949f-1981b29cf188
ms.openlocfilehash: 15a4a06726de348745e5eef03217d693db496a42
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182258"
---
# <a name="how-to-associate-a-shortcut-menu-with-a-windows-forms-notifyicon-component"></a>Como associar um menu de atalho a um componente NotifyIcon dos Windows Forms
> [!NOTE]
> Embora <xref:System.Windows.Forms.MenuStrip> <xref:System.Windows.Forms.ContextMenuStrip> substitua e adicione <xref:System.Windows.Forms.MainMenu> funcionalidade <xref:System.Windows.Forms.ContextMenu> aos controles e <xref:System.Windows.Forms.MainMenu> <xref:System.Windows.Forms.ContextMenu> controles das versões anteriores, e são retidos tanto para compatibilidade retrógrada quanto para uso futuro, se você escolher.  
  
 O <xref:System.Windows.Forms.NotifyIcon> componente exibe um ícone na área de notificação de status da barra de tarefas. Normalmente, aplicativos permitem clicar com o botão direito do mouse nesse ícone para enviar comandos para o aplicativo que ele representa. Ao associar <xref:System.Windows.Forms.ContextMenu> um componente <xref:System.Windows.Forms.NotifyIcon> ao componente, você pode adicionar essa funcionalidade aos seus aplicativos.  
  
> [!NOTE]
> Se você quiser que seu aplicativo seja minimizado <xref:System.Windows.Forms.NotifyIcon> na inicialização enquanto exibe uma <xref:System.Windows.Forms.Form.WindowState%2A> instância <xref:System.Windows.Forms.FormWindowState.Minimized> do componente <xref:System.Windows.Forms.NotifyIcon> na barra <xref:System.Windows.Forms.NotifyIcon.Visible%2A> de tarefas, defina a propriedade do formulário principal e certifique-se de que a propriedade do componente está definida como `true`.  
  
### <a name="to-associate-a-shortcut-menu-with-the-notifyicon-component-at-design-time"></a>Associar um menu de atalho ao componente NotifyIcon no tempo de design  
  
1. Adicione <xref:System.Windows.Forms.NotifyIcon> um componente ao seu formulário e defina <xref:System.Windows.Forms.NotifyIcon.Icon%2A> <xref:System.Windows.Forms.NotifyIcon.Visible%2A> as propriedades importantes, como as propriedades e.  
  
     Para obter mais informações, consulte [Como adicionar ícones de aplicativo ao TaskBar com o componente NotifyIcon do Windows Forms](app-icons-to-the-taskbar-with-wf-notifyicon.md).  
  
2. Adicione <xref:System.Windows.Forms.ContextMenu> um componente ao formulário do Windows.  
  
     Adicione itens de menu ao menu de atalho que representam os comandos que você deseja disponibilizar no tempo de execução. Esse também é um bom momento para adicionar melhorias de menu a esses itens de menu, como teclas de acesso.  
  
3. Defina <xref:System.Windows.Forms.NotifyIcon.ContextMenu%2A> a <xref:System.Windows.Forms.NotifyIcon> propriedade do componente no menu de atalho que você adicionou.  
  
     Com essa propriedade definida, o menu de atalho será exibido ao clicar no ícone da barra de tarefas.  
  
### <a name="to-associate-a-shortcut-menu-with-the-notifyicon-component-programmatically"></a>Associar um menu de atalho ao componente NotifyIcon com programação  
  
1. Crie uma instância <xref:System.Windows.Forms.NotifyIcon> da <xref:System.Windows.Forms.ContextMenu> classe e uma classe, com quaisquer<xref:System.Windows.Forms.NotifyIcon.Icon%2A> configurações de propriedade necessárias para a aplicação ( e <xref:System.Windows.Forms.NotifyIcon.Visible%2A> propriedades para o <xref:System.Windows.Forms.NotifyIcon> componente, itens de menu para o <xref:System.Windows.Forms.ContextMenu> componente).  
  
2. Defina <xref:System.Windows.Forms.NotifyIcon.ContextMenu%2A> a <xref:System.Windows.Forms.NotifyIcon> propriedade do componente no menu de atalho que você adicionou.  
  
     Com essa propriedade definida, o menu de atalho será exibido ao clicar no ícone da barra de tarefas.  
  
    > [!NOTE]
    > O exemplo de código a seguir cria uma estrutura de menu básica. Você precisará personalizar as opções do menu para que se ajustem ao aplicativo que você está desenvolvendo. Além disso, você vai querer escrever <xref:System.Windows.Forms.MenuItem.Click> código para lidar com os eventos desses itens do menu.  
  
    ```vb  
    Public ContextMenu1 As New ContextMenu  
    Public NotifyIcon1 As New NotifyIcon  
  
    Public Sub CreateIconMenuStructure()  
       ' Add menu items to shortcut menu.  
       ContextMenu1.MenuItems.Add("&Open Application")  
       ContextMenu1.MenuItems.Add("S&uspend Application")  
       ContextMenu1.MenuItems.Add("E&xit")  
  
       ' Set properties of NotifyIcon component.  
       NotifyIcon1.Icon = New System.Drawing.Icon _
          (System.Environment.GetFolderPath _
          (System.Environment.SpecialFolder.Personal)  _
          & "\Icon.ico")  
       NotifyIcon1.Text = "Right-click me!"  
       NotifyIcon1.Visible = True  
       NotifyIcon1.ContextMenu = ContextMenu1  
    End Sub  
    ```  
  
```csharp  
public NotifyIcon notifyIcon1 = new NotifyIcon();  
public ContextMenu contextMenu1 = new ContextMenu();  
  
public void createIconMenuStructure()  
{  
   // Add menu items to shortcut menu.  
   contextMenu1.MenuItems.Add("&Open Application");  
   contextMenu1.MenuItems.Add("S&uspend Application");  
   contextMenu1.MenuItems.Add("E&xit");  
  
   // Set properties of NotifyIcon component.  
   notifyIcon1.Icon = new System.Drawing.Icon  
      (System.Environment.GetFolderPath  
      (System.Environment.SpecialFolder.Personal)  
      + @"\Icon.ico");  
   notifyIcon1.Visible = true;  
   notifyIcon1.Text = "Right-click me!";  
   notifyIcon1.Visible = true;  
   notifyIcon1.ContextMenu = contextMenu1;  
}  
```  
  
```cpp  
public:  
   System::Windows::Forms::NotifyIcon ^ notifyIcon1;  
   System::Windows::Forms::ContextMenu ^ contextMenu1;  
  
   void createIconMenuStructure()  
   {  
      // Add menu items to shortcut menu.  
      contextMenu1->MenuItems->Add("&Open Application");  
      contextMenu1->MenuItems->Add("S&uspend Application");  
      contextMenu1->MenuItems->Add("E&xit");  
  
      // Set properties of NotifyIcon component.  
      notifyIcon1->Icon = gcnew System::Drawing::Icon  
          (String::Concat(System::Environment::GetFolderPath  
          (System::Environment::SpecialFolder::Personal),  
          "\\Icon.ico"));  
      notifyIcon1->Text = "Right-click me!";  
      notifyIcon1->Visible = true;  
      notifyIcon1->ContextMenu = contextMenu1;  
   }  
```  
  
> [!NOTE]
> Você deve inicializar `notifyIcon1` e `contextMenu1,`, o que pode ser feito incluindo a instrução a seguir no construtor do formulário:  
  
```cpp  
notifyIcon1 = gcnew System::Windows::Forms::NotifyIcon();  
contextMenu1 = gcnew System::Windows::Forms::ContextMenu();  
```  
  
## <a name="see-also"></a>Confira também

- <xref:System.Windows.Forms.NotifyIcon>
- <xref:System.Windows.Forms.NotifyIcon.Icon%2A>
- [Como adicionar ícones do aplicativo à TaskBar com o componente NotifyIcon dos Windows Forms](app-icons-to-the-taskbar-with-wf-notifyicon.md)
- [Componente NotifyIcon](notifyicon-component-windows-forms.md)
- [Visão geral do componente NotifyIcon](notifyicon-component-overview-windows-forms.md)
