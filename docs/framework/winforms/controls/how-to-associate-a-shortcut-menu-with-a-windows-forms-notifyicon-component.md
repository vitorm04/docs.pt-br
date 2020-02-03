---
title: Associar um menu de atalho com o componente NotifyIcon
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
ms.openlocfilehash: 392c04f73feaec201033ad76f9419a0e070bec70
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742052"
---
# <a name="how-to-associate-a-shortcut-menu-with-a-windows-forms-notifyicon-component"></a>Como associar um menu de atalho a um componente NotifyIcon dos Windows Forms
> [!NOTE]
> Embora <xref:System.Windows.Forms.MenuStrip> e <xref:System.Windows.Forms.ContextMenuStrip> substituam e adicionem funcionalidade aos controles <xref:System.Windows.Forms.MainMenu> e <xref:System.Windows.Forms.ContextMenu> de versões anteriores, <xref:System.Windows.Forms.MainMenu> e <xref:System.Windows.Forms.ContextMenu> são mantidos para a compatibilidade com versões anteriores e o uso futuro, se você escolher.  
  
 O componente <xref:System.Windows.Forms.NotifyIcon> exibe um ícone na área de notificação de status da barra de tarefas. Normalmente, aplicativos permitem clicar com o botão direito do mouse nesse ícone para enviar comandos para o aplicativo que ele representa. Ao associar um componente de <xref:System.Windows.Forms.ContextMenu> ao componente <xref:System.Windows.Forms.NotifyIcon>, você pode adicionar essa funcionalidade aos seus aplicativos.  
  
> [!NOTE]
> Se você quiser que seu aplicativo seja minimizado na inicialização durante a exibição de uma instância do componente <xref:System.Windows.Forms.NotifyIcon> na barra de tarefas, defina a propriedade <xref:System.Windows.Forms.Form.WindowState%2A> do formulário principal como <xref:System.Windows.Forms.FormWindowState.Minimized> e verifique se a propriedade <xref:System.Windows.Forms.NotifyIcon.Visible%2A> do componente <xref:System.Windows.Forms.NotifyIcon> está definida como `true`.  
  
### <a name="to-associate-a-shortcut-menu-with-the-notifyicon-component-at-design-time"></a>Associar um menu de atalho ao componente NotifyIcon no tempo de design  
  
1. Adicione um componente <xref:System.Windows.Forms.NotifyIcon> ao formulário e defina as propriedades importantes, como as propriedades <xref:System.Windows.Forms.NotifyIcon.Icon%2A> e <xref:System.Windows.Forms.NotifyIcon.Visible%2A>.  
  
     Para obter mais informações, consulte [Como adicionar ícones de aplicativo ao TaskBar com o componente NotifyIcon do Windows Forms](app-icons-to-the-taskbar-with-wf-notifyicon.md).  
  
2. Adicione um componente <xref:System.Windows.Forms.ContextMenu> ao seu formulário do Windows.  
  
     Adicione itens de menu ao menu de atalho que representam os comandos que você deseja disponibilizar no tempo de execução. Esse também é um bom momento para adicionar melhorias de menu a esses itens de menu, como teclas de acesso.  
  
3. Defina a propriedade <xref:System.Windows.Forms.NotifyIcon.ContextMenu%2A> do componente <xref:System.Windows.Forms.NotifyIcon> para o menu de atalho que você adicionou.  
  
     Com essa propriedade definida, o menu de atalho será exibido ao clicar no ícone da barra de tarefas.  
  
### <a name="to-associate-a-shortcut-menu-with-the-notifyicon-component-programmatically"></a>Associar um menu de atalho ao componente NotifyIcon com programação  
  
1. Crie uma instância da classe <xref:System.Windows.Forms.NotifyIcon> e uma classe <xref:System.Windows.Forms.ContextMenu>, com quaisquer configurações de propriedade necessárias para o aplicativo (<xref:System.Windows.Forms.NotifyIcon.Icon%2A> e propriedades <xref:System.Windows.Forms.NotifyIcon.Visible%2A> para o componente <xref:System.Windows.Forms.NotifyIcon>, itens de menu para o componente <xref:System.Windows.Forms.ContextMenu>).  
  
2. Defina a propriedade <xref:System.Windows.Forms.NotifyIcon.ContextMenu%2A> do componente <xref:System.Windows.Forms.NotifyIcon> para o menu de atalho que você adicionou.  
  
     Com essa propriedade definida, o menu de atalho será exibido ao clicar no ícone da barra de tarefas.  
  
    > [!NOTE]
    > O exemplo de código a seguir cria uma estrutura de menu básica. Você precisará personalizar as opções do menu para que se ajustem ao aplicativo que você está desenvolvendo. Além disso, você desejará escrever código para manipular os eventos de <xref:System.Windows.Forms.MenuItem.Click> para esses itens de menu.  
  
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
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.NotifyIcon>
- <xref:System.Windows.Forms.NotifyIcon.Icon%2A>
- [Como adicionar ícones do aplicativo à TaskBar com o componente NotifyIcon dos Windows Forms](app-icons-to-the-taskbar-with-wf-notifyicon.md)
- [Componente NotifyIcon](notifyicon-component-windows-forms.md)
- [Visão geral do componente NotifyIcon](notifyicon-component-overview-windows-forms.md)
