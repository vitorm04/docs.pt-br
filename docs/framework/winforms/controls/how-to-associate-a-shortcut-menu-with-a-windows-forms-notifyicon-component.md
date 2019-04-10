---
title: 'Como: Associar um menu de atalho a um componente NotifyIcon do Windows Forms'
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
ms.openlocfilehash: f2a086cc25eb6996b2643742a887bccf481916d6
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59337052"
---
# <a name="how-to-associate-a-shortcut-menu-with-a-windows-forms-notifyicon-component"></a>Como: Associar um menu de atalho a um componente NotifyIcon do Windows Forms
> [!NOTE]
>  Embora <xref:System.Windows.Forms.MenuStrip> e <xref:System.Windows.Forms.ContextMenuStrip> substituam e adicionem funcionalidade para o <xref:System.Windows.Forms.MainMenu> e <xref:System.Windows.Forms.ContextMenu> de versões anteriores, os controles <xref:System.Windows.Forms.MainMenu> e <xref:System.Windows.Forms.ContextMenu> são mantidos para compatibilidade com versões anteriores e uso futuro, se você escolher.  
  
 O <xref:System.Windows.Forms.NotifyIcon> componente exibe um ícone na área de notificação de status da barra de tarefas. Normalmente, aplicativos permitem clicar com o botão direito do mouse nesse ícone para enviar comandos para o aplicativo que ele representa. Associando um <xref:System.Windows.Forms.ContextMenu> componente com o <xref:System.Windows.Forms.NotifyIcon> componente, você pode adicionar essa funcionalidade aos seus aplicativos.  
  
> [!NOTE]
>  Se você quiser que seu aplicativo seja minimizado na inicialização ao exibir uma instância das <xref:System.Windows.Forms.NotifyIcon> componente na barra de tarefas, defina o formulário principal <xref:System.Windows.Forms.Form.WindowState%2A> propriedade a ser <xref:System.Windows.Forms.FormWindowState.Minimized> e certifique-se a <xref:System.Windows.Forms.NotifyIcon> do componente <xref:System.Windows.Forms.NotifyIcon.Visible%2A> propriedade é definido como `true`.  
  
### <a name="to-associate-a-shortcut-menu-with-the-notifyicon-component-at-design-time"></a>Associar um menu de atalho ao componente NotifyIcon no tempo de design  
  
1. Adicionar um <xref:System.Windows.Forms.NotifyIcon> ao seu formulário e defina as propriedades importantes, como o <xref:System.Windows.Forms.NotifyIcon.Icon%2A> e <xref:System.Windows.Forms.NotifyIcon.Visible%2A> propriedades.  
  
     Para obter mais informações, confira [Como: Adicionar ícones de aplicativo ao TaskBar com o Windows Forms ao componente NotifyIcon](app-icons-to-the-taskbar-with-wf-notifyicon.md).  
  
2. Adicionar um <xref:System.Windows.Forms.ContextMenu> ao seu formulário do Windows.  
  
     Adicione itens de menu ao menu de atalho que representam os comandos que você deseja disponibilizar no tempo de execução. Esse também é um bom momento para adicionar melhorias de menu a esses itens de menu, como teclas de acesso.  
  
3. Defina a <xref:System.Windows.Forms.NotifyIcon.ContextMenu%2A> propriedade do <xref:System.Windows.Forms.NotifyIcon> componente para o menu de atalho que você adicionou.  
  
     Com essa propriedade definida, o menu de atalho será exibido ao clicar no ícone da barra de tarefas.  
  
### <a name="to-associate-a-shortcut-menu-with-the-notifyicon-component-programmatically"></a>Associar um menu de atalho ao componente NotifyIcon com programação  
  
1. Criar uma instância do <xref:System.Windows.Forms.NotifyIcon> classe e uma <xref:System.Windows.Forms.ContextMenu> classe, com todas as configurações de propriedade são necessárias para o aplicativo (<xref:System.Windows.Forms.NotifyIcon.Icon%2A> e <xref:System.Windows.Forms.NotifyIcon.Visible%2A> as propriedades para o <xref:System.Windows.Forms.NotifyIcon> componente, itens de menu para o <xref:System.Windows.Forms.ContextMenu> componente).  
  
2. Defina a <xref:System.Windows.Forms.NotifyIcon.ContextMenu%2A> propriedade do <xref:System.Windows.Forms.NotifyIcon> componente para o menu de atalho que você adicionou.  
  
     Com essa propriedade definida, o menu de atalho será exibido ao clicar no ícone da barra de tarefas.  
  
    > [!NOTE]
    >  O exemplo de código a seguir cria uma estrutura de menu básica. Você precisará personalizar as opções do menu para que se ajustem ao aplicativo que você está desenvolvendo. Além disso, você vai querer escrever código para manipular o <xref:System.Windows.Forms.MenuItem.Click> eventos para esses itens de menu.  
  
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
>  Você deve inicializar `notifyIcon1` e `contextMenu1,`, o que pode ser feito incluindo a instrução a seguir no construtor do formulário:  
  
```cpp  
notifyIcon1 = gcnew System::Windows::Forms::NotifyIcon();  
contextMenu1 = gcnew System::Windows::Forms::ContextMenu();  
```  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.NotifyIcon>
- <xref:System.Windows.Forms.NotifyIcon.Icon%2A>
- [Como: Adicionar ícones do aplicativo à TaskBar com o componente NotifyIcon do Windows Forms](app-icons-to-the-taskbar-with-wf-notifyicon.md)
- [Componente NotifyIcon](notifyicon-component-windows-forms.md)
- [Visão geral do componente NotifyIcon](notifyicon-component-overview-windows-forms.md)
