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
# <a name="how-to-add-application-icons-to-the-taskbar-with-the-windows-forms-notifyicon-component"></a><span data-ttu-id="8dc07-102">Como adicionar ícones de aplicativo ao TaskBar com o componente NotifyIcon dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8dc07-102">How to: Add Application Icons to the TaskBar with the Windows Forms NotifyIcon Component</span></span>

<span data-ttu-id="8dc07-103">O componente Windows Forms <xref:System.Windows.Forms.NotifyIcon> exibe um único ícone na área de notificação de status da barra de tarefas.</span><span class="sxs-lookup"><span data-stu-id="8dc07-103">The Windows Forms <xref:System.Windows.Forms.NotifyIcon> component displays a single icon in the status notification area of the taskbar.</span></span> <span data-ttu-id="8dc07-104">Para exibir vários ícones na área de status, você deve ter vários componentes <xref:System.Windows.Forms.NotifyIcon> no formulário.</span><span class="sxs-lookup"><span data-stu-id="8dc07-104">To display multiple icons in the status area, you must have multiple <xref:System.Windows.Forms.NotifyIcon> components on your form.</span></span> <span data-ttu-id="8dc07-105">Para definir o ícone exibido para um controle, use a propriedade <xref:System.Windows.Forms.NotifyIcon.Icon%2A>.</span><span class="sxs-lookup"><span data-stu-id="8dc07-105">To set the icon displayed for a control, use the <xref:System.Windows.Forms.NotifyIcon.Icon%2A> property.</span></span> <span data-ttu-id="8dc07-106">Você também pode escrever código no manipulador de eventos <xref:System.Windows.Forms.NotifyIcon.DoubleClick> para que algo aconteça quando o usuário clicar duas vezes no ícone.</span><span class="sxs-lookup"><span data-stu-id="8dc07-106">You can also write code in the <xref:System.Windows.Forms.NotifyIcon.DoubleClick> event handler so that something happens when the user double-clicks the icon.</span></span> <span data-ttu-id="8dc07-107">Por exemplo, você pode fazer com que uma caixa de diálogo apareça para o usuário configurar o processo em segundo plano representado pelo ícone.</span><span class="sxs-lookup"><span data-stu-id="8dc07-107">For example, you could make a dialog box appear for the user to configure the background process represented by the icon.</span></span>

> [!NOTE]
> <span data-ttu-id="8dc07-108">O componente <xref:System.Windows.Forms.NotifyIcon> é usado apenas para fins de notificação, para alertar os usuários de que uma ação ou evento ocorreu ou houve uma alteração no status de algum tipo.</span><span class="sxs-lookup"><span data-stu-id="8dc07-108">The <xref:System.Windows.Forms.NotifyIcon> component is used for notification purposes only, to alert users that an action or event has occurred or there has been a change in status of some sort.</span></span> <span data-ttu-id="8dc07-109">Você deve usar os menus, barras de ferramentas e outros elementos de interface do usuário para interação padrão com aplicativos.</span><span class="sxs-lookup"><span data-stu-id="8dc07-109">You should use menus, toolbars, and other user-interface elements for standard interaction with applications.</span></span>

### <a name="to-set-the-icon"></a><span data-ttu-id="8dc07-110">Definir o ícone</span><span class="sxs-lookup"><span data-stu-id="8dc07-110">To set the icon</span></span>

1. <span data-ttu-id="8dc07-111">Atribua um valor à propriedade <xref:System.Windows.Forms.NotifyIcon.Icon%2A>.</span><span class="sxs-lookup"><span data-stu-id="8dc07-111">Assign a value to the <xref:System.Windows.Forms.NotifyIcon.Icon%2A> property.</span></span> <span data-ttu-id="8dc07-112">O valor deve ser do tipo `System.Drawing.Icon` e pode ser carregados de um arquivo .ico.</span><span class="sxs-lookup"><span data-stu-id="8dc07-112">The value must be of type `System.Drawing.Icon` and can be loaded from an .ico file.</span></span> <span data-ttu-id="8dc07-113">Você pode especificar o arquivo de ícone no código ou clicando no botão de reticências (![botão de reticências (...) na janela Propriedades do Visual Studio.](./media/visual-studio-ellipsis-button.png)) ao lado da propriedade <xref:System.Windows.Forms.NotifyIcon.Icon%2A> na janela **Propriedades** e, em seguida, selecionando o arquivo na caixa de diálogo **abrir** que aparece.</span><span class="sxs-lookup"><span data-stu-id="8dc07-113">You can specify the icon file in code or by clicking the ellipsis button (![The Ellipsis button (...) in the Properties window of Visual Studio.](./media/visual-studio-ellipsis-button.png)) next to the <xref:System.Windows.Forms.NotifyIcon.Icon%2A> property in the **Properties** window, and then selecting the file in the **Open** dialog box that appears.</span></span>

2. <span data-ttu-id="8dc07-114">Defina a propriedade <xref:System.Windows.Forms.NotifyIcon.Visible%2A> como `true`.</span><span class="sxs-lookup"><span data-stu-id="8dc07-114">Set the <xref:System.Windows.Forms.NotifyIcon.Visible%2A> property to `true`.</span></span>

3. <span data-ttu-id="8dc07-115">Defina a propriedade <xref:System.Windows.Forms.NotifyIcon.Text%2A> como uma cadeia de dica de ferramenta apropriada.</span><span class="sxs-lookup"><span data-stu-id="8dc07-115">Set the <xref:System.Windows.Forms.NotifyIcon.Text%2A> property to an appropriate ToolTip string.</span></span>

     <span data-ttu-id="8dc07-116">No exemplo de código a seguir, o caminho definido para o local do ícone é a pasta **Meus Documentos**.</span><span class="sxs-lookup"><span data-stu-id="8dc07-116">In the following code example, the path set for the location of the icon is the **My Documents** folder.</span></span> <span data-ttu-id="8dc07-117">Esse local é usado porque você pode supor que a maioria dos computadores que executam o sistema operacional Windows incluem essa pasta.</span><span class="sxs-lookup"><span data-stu-id="8dc07-117">This location is used because you can assume that most computers running the Windows operating system will include this folder.</span></span> <span data-ttu-id="8dc07-118">Escolher esse local também permite que os usuários com níveis mínimos de acesso ao sistema executem o aplicativo com mais segurança.</span><span class="sxs-lookup"><span data-stu-id="8dc07-118">Choosing this location also enables users with minimal system access levels to safely run the application.</span></span> <span data-ttu-id="8dc07-119">O exemplo a seguir requer um formulário com um controle <xref:System.Windows.Forms.NotifyIcon> já adicionado.</span><span class="sxs-lookup"><span data-stu-id="8dc07-119">The following example requires a form with a <xref:System.Windows.Forms.NotifyIcon> control already added.</span></span> <span data-ttu-id="8dc07-120">Ele também requer um arquivo de ícone denominado `Icon.ico`.</span><span class="sxs-lookup"><span data-stu-id="8dc07-120">It also requires an icon file named `Icon.ico`.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="8dc07-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8dc07-121">See also</span></span>

- <xref:System.Windows.Forms.NotifyIcon>
- <xref:System.Windows.Forms.NotifyIcon.Icon%2A>
- [<span data-ttu-id="8dc07-122">Como associar um menu de atalho a um componente NotifyIcon dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8dc07-122">How to: Associate a Shortcut Menu with a Windows Forms NotifyIcon Component</span></span>](how-to-associate-a-shortcut-menu-with-a-windows-forms-notifyicon-component.md)
- [<span data-ttu-id="8dc07-123">Componente NotifyIcon</span><span class="sxs-lookup"><span data-stu-id="8dc07-123">NotifyIcon Component</span></span>](notifyicon-component-windows-forms.md)
- [<span data-ttu-id="8dc07-124">Visão geral do componente NotifyIcon</span><span class="sxs-lookup"><span data-stu-id="8dc07-124">NotifyIcon Component Overview</span></span>](notifyicon-component-overview-windows-forms.md)
