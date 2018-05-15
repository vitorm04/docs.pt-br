---
title: Como adicionar ícones de aplicativo ao TaskBar com o componente NotifyIcon dos Windows Forms
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
ms.openlocfilehash: c7658a3a1c72c3fed4033e644d0dd776b06ee1a6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-add-application-icons-to-the-taskbar-with-the-windows-forms-notifyicon-component"></a><span data-ttu-id="271d9-102">Como adicionar ícones de aplicativo ao TaskBar com o componente NotifyIcon dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="271d9-102">How to: Add Application Icons to the TaskBar with the Windows Forms NotifyIcon Component</span></span>
<span data-ttu-id="271d9-103">Windows Forms <xref:System.Windows.Forms.NotifyIcon> componente exibe um único ícone na área de notificação de status da barra de tarefas.</span><span class="sxs-lookup"><span data-stu-id="271d9-103">The Windows Forms <xref:System.Windows.Forms.NotifyIcon> component displays a single icon in the status notification area of the taskbar.</span></span> <span data-ttu-id="271d9-104">Para exibir vários ícones na área de status, você deve ter vários <xref:System.Windows.Forms.NotifyIcon> componentes no formulário.</span><span class="sxs-lookup"><span data-stu-id="271d9-104">To display multiple icons in the status area, you must have multiple <xref:System.Windows.Forms.NotifyIcon> components on your form.</span></span> <span data-ttu-id="271d9-105">Para definir o ícone exibido para um controle, use o <xref:System.Windows.Forms.NotifyIcon.Icon%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="271d9-105">To set the icon displayed for a control, use the <xref:System.Windows.Forms.NotifyIcon.Icon%2A> property.</span></span> <span data-ttu-id="271d9-106">Você também pode escrever código no <xref:System.Windows.Forms.NotifyIcon.DoubleClick> manipulador de eventos para que algo acontece quando o usuário clica duas vezes no ícone.</span><span class="sxs-lookup"><span data-stu-id="271d9-106">You can also write code in the <xref:System.Windows.Forms.NotifyIcon.DoubleClick> event handler so that something happens when the user double-clicks the icon.</span></span> <span data-ttu-id="271d9-107">Por exemplo, você pode fazer com que uma caixa de diálogo apareça para o usuário configurar o processo em segundo plano representado pelo ícone.</span><span class="sxs-lookup"><span data-stu-id="271d9-107">For example, you could make a dialog box appear for the user to configure the background process represented by the icon.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="271d9-108">O <xref:System.Windows.Forms.NotifyIcon> componente é usado para fins de notificação apenas, para alertar os usuários que ocorreu um evento ou ação ou houve uma alteração no status de algum tipo.</span><span class="sxs-lookup"><span data-stu-id="271d9-108">The <xref:System.Windows.Forms.NotifyIcon> component is used for notification purposes only, to alert users that an action or event has occurred or there has been a change in status of some sort.</span></span> <span data-ttu-id="271d9-109">Você deve usar os menus, barras de ferramentas e outros elementos de interface do usuário para interação padrão com aplicativos.</span><span class="sxs-lookup"><span data-stu-id="271d9-109">You should use menus, toolbars, and other user-interface elements for standard interaction with applications.</span></span>  
  
### <a name="to-set-the-icon"></a><span data-ttu-id="271d9-110">Definir o ícone</span><span class="sxs-lookup"><span data-stu-id="271d9-110">To set the icon</span></span>  
  
1.  <span data-ttu-id="271d9-111">Atribuir um valor para o <xref:System.Windows.Forms.NotifyIcon.Icon%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="271d9-111">Assign a value to the <xref:System.Windows.Forms.NotifyIcon.Icon%2A> property.</span></span> <span data-ttu-id="271d9-112">O valor deve ser do tipo `System.Drawing.Icon` e pode ser carregados de um arquivo .ico.</span><span class="sxs-lookup"><span data-stu-id="271d9-112">The value must be of type `System.Drawing.Icon` and can be loaded from an .ico file.</span></span> <span data-ttu-id="271d9-113">Você pode especificar o arquivo de ícone no código ou clicando no botão de reticências (![de tela de VisualStudioEllipsesButton](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) ao lado de <xref:System.Windows.Forms.NotifyIcon.Icon%2A> propriedade no  **Propriedades** janela e, em seguida, selecionando o arquivo no **abrir** caixa de diálogo que aparece.</span><span class="sxs-lookup"><span data-stu-id="271d9-113">You can specify the icon file in code or by clicking the ellipsis button (![VisualStudioEllipsesButton screenshot](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) next to the <xref:System.Windows.Forms.NotifyIcon.Icon%2A> property in the **Properties** window, and then selecting the file in the **Open** dialog box that appears.</span></span>  
  
2.  <span data-ttu-id="271d9-114">Defina a propriedade <xref:System.Windows.Forms.NotifyIcon.Visible%2A> como `true`.</span><span class="sxs-lookup"><span data-stu-id="271d9-114">Set the <xref:System.Windows.Forms.NotifyIcon.Visible%2A> property to `true`.</span></span>  
  
3.  <span data-ttu-id="271d9-115">Definir o <xref:System.Windows.Forms.NotifyIcon.Text%2A> propriedade como uma cadeia de caracteres de dica de ferramenta apropriada.</span><span class="sxs-lookup"><span data-stu-id="271d9-115">Set the <xref:System.Windows.Forms.NotifyIcon.Text%2A> property to an appropriate ToolTip string.</span></span>  
  
     <span data-ttu-id="271d9-116">No exemplo de código a seguir, o caminho definido para o local do ícone é a pasta **Meus Documentos**.</span><span class="sxs-lookup"><span data-stu-id="271d9-116">In the following code example, the path set for the location of the icon is the **My Documents** folder.</span></span> <span data-ttu-id="271d9-117">Esse local é usado porque você pode supor que a maioria dos computadores que executam o sistema operacional Windows incluem essa pasta.</span><span class="sxs-lookup"><span data-stu-id="271d9-117">This location is used because you can assume that most computers running the Windows operating system will include this folder.</span></span> <span data-ttu-id="271d9-118">Escolher esse local também permite que os usuários com níveis mínimos de acesso ao sistema executem o aplicativo com mais segurança.</span><span class="sxs-lookup"><span data-stu-id="271d9-118">Choosing this location also enables users with minimal system access levels to safely run the application.</span></span> <span data-ttu-id="271d9-119">O exemplo a seguir exige um formulário com um <xref:System.Windows.Forms.NotifyIcon> controle já foi adicionado.</span><span class="sxs-lookup"><span data-stu-id="271d9-119">The following example requires a form with a <xref:System.Windows.Forms.NotifyIcon> control already added.</span></span> <span data-ttu-id="271d9-120">Ele também requer um arquivo de ícone denominado `Icon.ico`.</span><span class="sxs-lookup"><span data-stu-id="271d9-120">It also requires an icon file named `Icon.ico`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="271d9-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="271d9-121">See Also</span></span>  
 <xref:System.Windows.Forms.NotifyIcon>  
 <xref:System.Windows.Forms.NotifyIcon.Icon%2A>  
 [<span data-ttu-id="271d9-122">Como associar um menu de atalho a um componente NotifyIcon dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="271d9-122">How to: Associate a Shortcut Menu with a Windows Forms NotifyIcon Component</span></span>](../../../../docs/framework/winforms/controls/how-to-associate-a-shortcut-menu-with-a-windows-forms-notifyicon-component.md)  
 [<span data-ttu-id="271d9-123">Componente NotifyIcon</span><span class="sxs-lookup"><span data-stu-id="271d9-123">NotifyIcon Component</span></span>](../../../../docs/framework/winforms/controls/notifyicon-component-windows-forms.md)  
 [<span data-ttu-id="271d9-124">Visão geral do componente NotifyIcon</span><span class="sxs-lookup"><span data-stu-id="271d9-124">NotifyIcon Component Overview</span></span>](../../../../docs/framework/winforms/controls/notifyicon-component-overview-windows-forms.md)
