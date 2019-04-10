---
title: 'Como: Adicionar ícones do aplicativo à TaskBar com o componente NotifyIcon do Windows Forms'
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
ms.openlocfilehash: 52c18b959361079aac6b95dc5d4584bf464a306a
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59304513"
---
# <a name="how-to-add-application-icons-to-the-taskbar-with-the-windows-forms-notifyicon-component"></a><span data-ttu-id="c52f7-102">Como: Adicionar ícones do aplicativo à TaskBar com o componente NotifyIcon do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c52f7-102">How to: Add Application Icons to the TaskBar with the Windows Forms NotifyIcon Component</span></span>
<span data-ttu-id="c52f7-103">Os formulários do Windows <xref:System.Windows.Forms.NotifyIcon> componente exibe um único ícone na área de notificação de status da barra de tarefas.</span><span class="sxs-lookup"><span data-stu-id="c52f7-103">The Windows Forms <xref:System.Windows.Forms.NotifyIcon> component displays a single icon in the status notification area of the taskbar.</span></span> <span data-ttu-id="c52f7-104">Para exibir vários ícones na área de status, você deve ter vários <xref:System.Windows.Forms.NotifyIcon> componentes em seu formulário.</span><span class="sxs-lookup"><span data-stu-id="c52f7-104">To display multiple icons in the status area, you must have multiple <xref:System.Windows.Forms.NotifyIcon> components on your form.</span></span> <span data-ttu-id="c52f7-105">Para definir o ícone exibido para um controle, use o <xref:System.Windows.Forms.NotifyIcon.Icon%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="c52f7-105">To set the icon displayed for a control, use the <xref:System.Windows.Forms.NotifyIcon.Icon%2A> property.</span></span> <span data-ttu-id="c52f7-106">Você também pode escrever código no <xref:System.Windows.Forms.NotifyIcon.DoubleClick> manipulador de eventos para que algo acontece quando o usuário clica duas vezes no ícone.</span><span class="sxs-lookup"><span data-stu-id="c52f7-106">You can also write code in the <xref:System.Windows.Forms.NotifyIcon.DoubleClick> event handler so that something happens when the user double-clicks the icon.</span></span> <span data-ttu-id="c52f7-107">Por exemplo, você pode fazer com que uma caixa de diálogo apareça para o usuário configurar o processo em segundo plano representado pelo ícone.</span><span class="sxs-lookup"><span data-stu-id="c52f7-107">For example, you could make a dialog box appear for the user to configure the background process represented by the icon.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c52f7-108">O <xref:System.Windows.Forms.NotifyIcon> componente é usado para fins de notificação apenas, para alertar os usuários que ocorreu um evento ou ação ou houve uma alteração no status de algum tipo.</span><span class="sxs-lookup"><span data-stu-id="c52f7-108">The <xref:System.Windows.Forms.NotifyIcon> component is used for notification purposes only, to alert users that an action or event has occurred or there has been a change in status of some sort.</span></span> <span data-ttu-id="c52f7-109">Você deve usar os menus, barras de ferramentas e outros elementos de interface do usuário para interação padrão com aplicativos.</span><span class="sxs-lookup"><span data-stu-id="c52f7-109">You should use menus, toolbars, and other user-interface elements for standard interaction with applications.</span></span>  
  
### <a name="to-set-the-icon"></a><span data-ttu-id="c52f7-110">Definir o ícone</span><span class="sxs-lookup"><span data-stu-id="c52f7-110">To set the icon</span></span>  
  
1. <span data-ttu-id="c52f7-111">Atribuir um valor para o <xref:System.Windows.Forms.NotifyIcon.Icon%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="c52f7-111">Assign a value to the <xref:System.Windows.Forms.NotifyIcon.Icon%2A> property.</span></span> <span data-ttu-id="c52f7-112">O valor deve ser do tipo `System.Drawing.Icon` e pode ser carregados de um arquivo .ico.</span><span class="sxs-lookup"><span data-stu-id="c52f7-112">The value must be of type `System.Drawing.Icon` and can be loaded from an .ico file.</span></span> <span data-ttu-id="c52f7-113">Você pode especificar o arquivo de ícone no código ou clicando no botão de reticências (![captura de tela VisualStudioEllipsesButton](../media/vbellipsesbutton.png "vbEllipsesButton")) ao lado de <xref:System.Windows.Forms.NotifyIcon.Icon%2A> propriedade no  **As propriedades** janela e, em seguida, selecionando o arquivo na **aberto** caixa de diálogo que aparece.</span><span class="sxs-lookup"><span data-stu-id="c52f7-113">You can specify the icon file in code or by clicking the ellipsis button (![VisualStudioEllipsesButton screenshot](../media/vbellipsesbutton.png "vbEllipsesButton")) next to the <xref:System.Windows.Forms.NotifyIcon.Icon%2A> property in the **Properties** window, and then selecting the file in the **Open** dialog box that appears.</span></span>  
  
2. <span data-ttu-id="c52f7-114">Defina a propriedade <xref:System.Windows.Forms.NotifyIcon.Visible%2A> como `true`.</span><span class="sxs-lookup"><span data-stu-id="c52f7-114">Set the <xref:System.Windows.Forms.NotifyIcon.Visible%2A> property to `true`.</span></span>  
  
3. <span data-ttu-id="c52f7-115">Defina o <xref:System.Windows.Forms.NotifyIcon.Text%2A> propriedade como uma cadeia de caracteres de dica de ferramenta apropriada.</span><span class="sxs-lookup"><span data-stu-id="c52f7-115">Set the <xref:System.Windows.Forms.NotifyIcon.Text%2A> property to an appropriate ToolTip string.</span></span>  
  
     <span data-ttu-id="c52f7-116">No exemplo de código a seguir, o caminho definido para o local do ícone é a pasta **Meus Documentos**.</span><span class="sxs-lookup"><span data-stu-id="c52f7-116">In the following code example, the path set for the location of the icon is the **My Documents** folder.</span></span> <span data-ttu-id="c52f7-117">Esse local é usado porque você pode supor que a maioria dos computadores que executam o sistema operacional Windows incluem essa pasta.</span><span class="sxs-lookup"><span data-stu-id="c52f7-117">This location is used because you can assume that most computers running the Windows operating system will include this folder.</span></span> <span data-ttu-id="c52f7-118">Escolher esse local também permite que os usuários com níveis mínimos de acesso ao sistema executem o aplicativo com mais segurança.</span><span class="sxs-lookup"><span data-stu-id="c52f7-118">Choosing this location also enables users with minimal system access levels to safely run the application.</span></span> <span data-ttu-id="c52f7-119">O exemplo a seguir exige um formulário com um <xref:System.Windows.Forms.NotifyIcon> controle já adicionado.</span><span class="sxs-lookup"><span data-stu-id="c52f7-119">The following example requires a form with a <xref:System.Windows.Forms.NotifyIcon> control already added.</span></span> <span data-ttu-id="c52f7-120">Ele também requer um arquivo de ícone denominado `Icon.ico`.</span><span class="sxs-lookup"><span data-stu-id="c52f7-120">It also requires an icon file named `Icon.ico`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c52f7-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c52f7-121">See also</span></span>

- <xref:System.Windows.Forms.NotifyIcon>
- <xref:System.Windows.Forms.NotifyIcon.Icon%2A>
- [<span data-ttu-id="c52f7-122">Como: Associar um menu de atalho a um componente NotifyIcon do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c52f7-122">How to: Associate a Shortcut Menu with a Windows Forms NotifyIcon Component</span></span>](how-to-associate-a-shortcut-menu-with-a-windows-forms-notifyicon-component.md)
- [<span data-ttu-id="c52f7-123">Componente NotifyIcon</span><span class="sxs-lookup"><span data-stu-id="c52f7-123">NotifyIcon Component</span></span>](notifyicon-component-windows-forms.md)
- [<span data-ttu-id="c52f7-124">Visão geral do componente NotifyIcon</span><span class="sxs-lookup"><span data-stu-id="c52f7-124">NotifyIcon Component Overview</span></span>](notifyicon-component-overview-windows-forms.md)
