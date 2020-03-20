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
# <a name="how-to-associate-a-shortcut-menu-with-a-windows-forms-notifyicon-component"></a><span data-ttu-id="94a22-102">Como associar um menu de atalho a um componente NotifyIcon dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="94a22-102">How to: Associate a Shortcut Menu with a Windows Forms NotifyIcon Component</span></span>
> [!NOTE]
> <span data-ttu-id="94a22-103">Embora <xref:System.Windows.Forms.MenuStrip> <xref:System.Windows.Forms.ContextMenuStrip> substitua e adicione <xref:System.Windows.Forms.MainMenu> funcionalidade <xref:System.Windows.Forms.ContextMenu> aos controles e <xref:System.Windows.Forms.MainMenu> <xref:System.Windows.Forms.ContextMenu> controles das versões anteriores, e são retidos tanto para compatibilidade retrógrada quanto para uso futuro, se você escolher.</span><span class="sxs-lookup"><span data-stu-id="94a22-103">Although <xref:System.Windows.Forms.MenuStrip> and <xref:System.Windows.Forms.ContextMenuStrip> replace and add functionality to the <xref:System.Windows.Forms.MainMenu> and <xref:System.Windows.Forms.ContextMenu> controls of previous versions, <xref:System.Windows.Forms.MainMenu> and <xref:System.Windows.Forms.ContextMenu> are retained for both backward compatibility and future use if you choose.</span></span>  
  
 <span data-ttu-id="94a22-104">O <xref:System.Windows.Forms.NotifyIcon> componente exibe um ícone na área de notificação de status da barra de tarefas.</span><span class="sxs-lookup"><span data-stu-id="94a22-104">The <xref:System.Windows.Forms.NotifyIcon> component displays an icon in the status notification area of the taskbar.</span></span> <span data-ttu-id="94a22-105">Normalmente, aplicativos permitem clicar com o botão direito do mouse nesse ícone para enviar comandos para o aplicativo que ele representa.</span><span class="sxs-lookup"><span data-stu-id="94a22-105">Commonly, applications enable you to right-click this icon to send commands to the application it represents.</span></span> <span data-ttu-id="94a22-106">Ao associar <xref:System.Windows.Forms.ContextMenu> um componente <xref:System.Windows.Forms.NotifyIcon> ao componente, você pode adicionar essa funcionalidade aos seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="94a22-106">By associating a <xref:System.Windows.Forms.ContextMenu> component with the <xref:System.Windows.Forms.NotifyIcon> component, you can add this functionality to your applications.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="94a22-107">Se você quiser que seu aplicativo seja minimizado <xref:System.Windows.Forms.NotifyIcon> na inicialização enquanto exibe uma <xref:System.Windows.Forms.Form.WindowState%2A> instância <xref:System.Windows.Forms.FormWindowState.Minimized> do componente <xref:System.Windows.Forms.NotifyIcon> na barra <xref:System.Windows.Forms.NotifyIcon.Visible%2A> de tarefas, defina a propriedade do formulário principal e certifique-se de que a propriedade do componente está definida como `true`.</span><span class="sxs-lookup"><span data-stu-id="94a22-107">If you want your application to be minimized at startup while displaying an instance of the <xref:System.Windows.Forms.NotifyIcon> component in the taskbar, set the main form's <xref:System.Windows.Forms.Form.WindowState%2A> property to <xref:System.Windows.Forms.FormWindowState.Minimized> and be sure the <xref:System.Windows.Forms.NotifyIcon> component's <xref:System.Windows.Forms.NotifyIcon.Visible%2A> property is set to `true`.</span></span>  
  
### <a name="to-associate-a-shortcut-menu-with-the-notifyicon-component-at-design-time"></a><span data-ttu-id="94a22-108">Associar um menu de atalho ao componente NotifyIcon no tempo de design</span><span class="sxs-lookup"><span data-stu-id="94a22-108">To associate a shortcut menu with the NotifyIcon component at design time</span></span>  
  
1. <span data-ttu-id="94a22-109">Adicione <xref:System.Windows.Forms.NotifyIcon> um componente ao seu formulário e defina <xref:System.Windows.Forms.NotifyIcon.Icon%2A> <xref:System.Windows.Forms.NotifyIcon.Visible%2A> as propriedades importantes, como as propriedades e.</span><span class="sxs-lookup"><span data-stu-id="94a22-109">Add a <xref:System.Windows.Forms.NotifyIcon> component to your form, and set the important properties, such as the <xref:System.Windows.Forms.NotifyIcon.Icon%2A> and <xref:System.Windows.Forms.NotifyIcon.Visible%2A> properties.</span></span>  
  
     <span data-ttu-id="94a22-110">Para obter mais informações, consulte [Como adicionar ícones de aplicativo ao TaskBar com o componente NotifyIcon do Windows Forms](app-icons-to-the-taskbar-with-wf-notifyicon.md).</span><span class="sxs-lookup"><span data-stu-id="94a22-110">For more information, see [How to: Add Application Icons to the TaskBar with the Windows Forms NotifyIcon Component](app-icons-to-the-taskbar-with-wf-notifyicon.md).</span></span>  
  
2. <span data-ttu-id="94a22-111">Adicione <xref:System.Windows.Forms.ContextMenu> um componente ao formulário do Windows.</span><span class="sxs-lookup"><span data-stu-id="94a22-111">Add a <xref:System.Windows.Forms.ContextMenu> component to your Windows Form.</span></span>  
  
     <span data-ttu-id="94a22-112">Adicione itens de menu ao menu de atalho que representam os comandos que você deseja disponibilizar no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="94a22-112">Add menu items to the shortcut menu representing the commands you want to make available at run time.</span></span> <span data-ttu-id="94a22-113">Esse também é um bom momento para adicionar melhorias de menu a esses itens de menu, como teclas de acesso.</span><span class="sxs-lookup"><span data-stu-id="94a22-113">This is also a good time to add menu enhancements to these menu items, such as access keys.</span></span>  
  
3. <span data-ttu-id="94a22-114">Defina <xref:System.Windows.Forms.NotifyIcon.ContextMenu%2A> a <xref:System.Windows.Forms.NotifyIcon> propriedade do componente no menu de atalho que você adicionou.</span><span class="sxs-lookup"><span data-stu-id="94a22-114">Set the <xref:System.Windows.Forms.NotifyIcon.ContextMenu%2A> property of the <xref:System.Windows.Forms.NotifyIcon> component to the shortcut menu that you added.</span></span>  
  
     <span data-ttu-id="94a22-115">Com essa propriedade definida, o menu de atalho será exibido ao clicar no ícone da barra de tarefas.</span><span class="sxs-lookup"><span data-stu-id="94a22-115">With this property set, the shortcut menu will be displayed when the icon on the taskbar is clicked.</span></span>  
  
### <a name="to-associate-a-shortcut-menu-with-the-notifyicon-component-programmatically"></a><span data-ttu-id="94a22-116">Associar um menu de atalho ao componente NotifyIcon com programação</span><span class="sxs-lookup"><span data-stu-id="94a22-116">To associate a shortcut menu with the NotifyIcon component programmatically</span></span>  
  
1. <span data-ttu-id="94a22-117">Crie uma instância <xref:System.Windows.Forms.NotifyIcon> da <xref:System.Windows.Forms.ContextMenu> classe e uma classe, com quaisquer<xref:System.Windows.Forms.NotifyIcon.Icon%2A> configurações de propriedade necessárias para a aplicação ( e <xref:System.Windows.Forms.NotifyIcon.Visible%2A> propriedades para o <xref:System.Windows.Forms.NotifyIcon> componente, itens de menu para o <xref:System.Windows.Forms.ContextMenu> componente).</span><span class="sxs-lookup"><span data-stu-id="94a22-117">Create an instance of the <xref:System.Windows.Forms.NotifyIcon> class and a <xref:System.Windows.Forms.ContextMenu> class, with whatever property settings are necessary for the application (<xref:System.Windows.Forms.NotifyIcon.Icon%2A> and <xref:System.Windows.Forms.NotifyIcon.Visible%2A> properties for the <xref:System.Windows.Forms.NotifyIcon> component, menu items for the <xref:System.Windows.Forms.ContextMenu> component).</span></span>  
  
2. <span data-ttu-id="94a22-118">Defina <xref:System.Windows.Forms.NotifyIcon.ContextMenu%2A> a <xref:System.Windows.Forms.NotifyIcon> propriedade do componente no menu de atalho que você adicionou.</span><span class="sxs-lookup"><span data-stu-id="94a22-118">Set the <xref:System.Windows.Forms.NotifyIcon.ContextMenu%2A> property of the <xref:System.Windows.Forms.NotifyIcon> component to the shortcut menu that you added.</span></span>  
  
     <span data-ttu-id="94a22-119">Com essa propriedade definida, o menu de atalho será exibido ao clicar no ícone da barra de tarefas.</span><span class="sxs-lookup"><span data-stu-id="94a22-119">With this property set, the shortcut menu will be displayed when the icon on the taskbar is clicked.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="94a22-120">O exemplo de código a seguir cria uma estrutura de menu básica.</span><span class="sxs-lookup"><span data-stu-id="94a22-120">The following code example creates a basic menu structure.</span></span> <span data-ttu-id="94a22-121">Você precisará personalizar as opções do menu para que se ajustem ao aplicativo que você está desenvolvendo.</span><span class="sxs-lookup"><span data-stu-id="94a22-121">You will need to customize the menu choices to those that fit the application you are developing.</span></span> <span data-ttu-id="94a22-122">Além disso, você vai querer escrever <xref:System.Windows.Forms.MenuItem.Click> código para lidar com os eventos desses itens do menu.</span><span class="sxs-lookup"><span data-stu-id="94a22-122">Additionally, you will want to write code to handle the <xref:System.Windows.Forms.MenuItem.Click> events for these menu items.</span></span>  
  
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
> <span data-ttu-id="94a22-123">Você deve inicializar `notifyIcon1` e `contextMenu1,`, o que pode ser feito incluindo a instrução a seguir no construtor do formulário:</span><span class="sxs-lookup"><span data-stu-id="94a22-123">You must initialize `notifyIcon1` and `contextMenu1,` which you can do by including the following statements in the constructor of your form:</span></span>  
  
```cpp  
notifyIcon1 = gcnew System::Windows::Forms::NotifyIcon();  
contextMenu1 = gcnew System::Windows::Forms::ContextMenu();  
```  
  
## <a name="see-also"></a><span data-ttu-id="94a22-124">Confira também</span><span class="sxs-lookup"><span data-stu-id="94a22-124">See also</span></span>

- <xref:System.Windows.Forms.NotifyIcon>
- <xref:System.Windows.Forms.NotifyIcon.Icon%2A>
- [<span data-ttu-id="94a22-125">Como adicionar ícones do aplicativo à TaskBar com o componente NotifyIcon dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="94a22-125">How to: Add Application Icons to the TaskBar with the Windows Forms NotifyIcon Component</span></span>](app-icons-to-the-taskbar-with-wf-notifyicon.md)
- [<span data-ttu-id="94a22-126">Componente NotifyIcon</span><span class="sxs-lookup"><span data-stu-id="94a22-126">NotifyIcon Component</span></span>](notifyicon-component-windows-forms.md)
- [<span data-ttu-id="94a22-127">Visão geral do componente NotifyIcon</span><span class="sxs-lookup"><span data-stu-id="94a22-127">NotifyIcon Component Overview</span></span>](notifyicon-component-overview-windows-forms.md)
