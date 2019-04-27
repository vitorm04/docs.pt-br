---
title: 'Como: Adicionar controles sem uma interface do usuário ao Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
f1_keywords:
- NonVisualSelection
helpviewer_keywords:
- invisible controls [Windows Forms]
- Windows Forms controls, adding to form
- controls [Windows Forms], nonvisual
- Windows Forms controls, nonvisual
- nonvisual controls [Windows Forms]
ms.assetid: 52134d9c-cff6-4eed-8e2b-3d5eb3bd494e
ms.openlocfilehash: 0768f811653543b3370310ccc0b59890273baf52
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62011080"
---
# <a name="how-to-add-controls-without-a-user-interface-to-windows-forms"></a><span data-ttu-id="a7a70-102">Como: Adicionar controles sem uma interface do usuário ao Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a7a70-102">How to: Add Controls Without a User Interface to Windows Forms</span></span>
<span data-ttu-id="a7a70-103">Um controle (ou componente) não visual fornece funcionalidade ao seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a7a70-103">A nonvisual control (or component) provides functionality to your application.</span></span> <span data-ttu-id="a7a70-104">Diferente de outros controles, os componentes não fornecem uma interface do usuário ao usuário e, portanto, não precisam ser exibido na superfície do Designer de Formulários do Windows.</span><span class="sxs-lookup"><span data-stu-id="a7a70-104">Unlike other controls, components do not provide a user interface to the user and thus do not need to be displayed on the Windows Forms Designer surface.</span></span> <span data-ttu-id="a7a70-105">Quando um componente é adicionado a um formulário, o Designer de Formulários do Windows exibe uma bandeja redimensionável na parte inferior do formulário em que todos os componentes são exibidos.</span><span class="sxs-lookup"><span data-stu-id="a7a70-105">When a component is added to a form, the Windows Forms Designer displays a resizable tray at the bottom of the form where all components are displayed.</span></span> <span data-ttu-id="a7a70-106">Quando um controle é adicionado à bandeja de componentes, você pode selecionar o componente e definir suas propriedades como faria com qualquer outro controle no formulário.</span><span class="sxs-lookup"><span data-stu-id="a7a70-106">Once a control has been added to the component tray, you can select the component and set its properties as you would any other control on the form.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a7a70-107">As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas.</span><span class="sxs-lookup"><span data-stu-id="a7a70-107">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="a7a70-108">Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="a7a70-108">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="a7a70-109">Para obter mais informações, confira [Personalizar o IDE do Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="a7a70-109">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-add-a-component-to-a-windows-form"></a><span data-ttu-id="a7a70-110">Adicionar um componente a um Windows Form</span><span class="sxs-lookup"><span data-stu-id="a7a70-110">To add a component to a Windows Form</span></span>  
  
1. <span data-ttu-id="a7a70-111">Abra o formulário.</span><span class="sxs-lookup"><span data-stu-id="a7a70-111">Open the form.</span></span> <span data-ttu-id="a7a70-112">Para obter detalhes, confira [Como: Exibir Windows Forms no Designer](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w5yd62ts(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="a7a70-112">For details, see [How to: Display Windows Forms in the Designer](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w5yd62ts(v=vs.100)).</span></span>  
  
2. <span data-ttu-id="a7a70-113">Na **Caixa de ferramentas**, clique em um componente e arraste-o para o formulário.</span><span class="sxs-lookup"><span data-stu-id="a7a70-113">In the **Toolbox**, click a component and drag it to your form.</span></span>  
  
     <span data-ttu-id="a7a70-114">O componente aparece na bandeja de componentes.</span><span class="sxs-lookup"><span data-stu-id="a7a70-114">Your component appears in the component tray.</span></span>  
  
 <span data-ttu-id="a7a70-115">Além disso, os componentes podem ser adicionados a um formulário no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="a7a70-115">Furthermore, components can be added to a form at run time.</span></span> <span data-ttu-id="a7a70-116">Esse é um cenário comum, especialmente porque os componentes não têm uma expressão visual, diferente de controles que têm uma interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="a7a70-116">This is a common scenario, especially because components do not have a visual expression, unlike controls that have a user interface.</span></span> <span data-ttu-id="a7a70-117">No exemplo a seguir, um <xref:System.Windows.Forms.Timer> componente é adicionado em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="a7a70-117">In the example below, a <xref:System.Windows.Forms.Timer> component is added at run time.</span></span> <span data-ttu-id="a7a70-118">(Observe que o Visual Studio contém um número de temporizadores diferentes; nesse caso, use um Windows Forms <xref:System.Windows.Forms.Timer> componente.</span><span class="sxs-lookup"><span data-stu-id="a7a70-118">(Note that Visual Studio contains a number of different timers; in this case, use a Windows Forms <xref:System.Windows.Forms.Timer> component.</span></span> <span data-ttu-id="a7a70-119">Para obter mais informações sobre os diferentes temporizadores no Visual Studio, consulte [Introdução a temporizadores baseados em servidor](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/tb9yt5e6(v=vs.90)).)</span><span class="sxs-lookup"><span data-stu-id="a7a70-119">For more information about the different timers in Visual Studio, see [Introduction to Server-Based Timers](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/tb9yt5e6(v=vs.90)).)</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="a7a70-120">Componentes geralmente têm propriedades específicas de controle que devem ser definidas para o componente funcionar com eficiência.</span><span class="sxs-lookup"><span data-stu-id="a7a70-120">Components often have control-specific properties that must be set for the component to function effectively.</span></span> <span data-ttu-id="a7a70-121">No caso do <xref:System.Windows.Forms.Timer> componente abaixo, defina o `Interval` propriedade.</span><span class="sxs-lookup"><span data-stu-id="a7a70-121">In the case of the <xref:System.Windows.Forms.Timer> component below, you set the `Interval` property.</span></span> <span data-ttu-id="a7a70-122">Verifique se as propriedades necessárias para o componente foram definidas ao adicioná-lo ao projeto.</span><span class="sxs-lookup"><span data-stu-id="a7a70-122">Be sure, when adding components to your project, that you set the properties necessary for that component.</span></span>  
  
#### <a name="to-add-a-component-to-a-windows-form-programmatically"></a><span data-ttu-id="a7a70-123">Adicionar um componente a um Windows Form com programação</span><span class="sxs-lookup"><span data-stu-id="a7a70-123">To add a component to a Windows Form programmatically</span></span>  
  
1. <span data-ttu-id="a7a70-124">Criar uma instância da <xref:System.Windows.Forms.Timer> classe no código.</span><span class="sxs-lookup"><span data-stu-id="a7a70-124">Create an instance of the <xref:System.Windows.Forms.Timer> class in code.</span></span>  
  
2. <span data-ttu-id="a7a70-125">Defina a propriedade `Interval` para determinar o tempo entre os tiques do temporizador.</span><span class="sxs-lookup"><span data-stu-id="a7a70-125">Set the `Interval` property to determine the time between ticks of the timer.</span></span>  
  
3. <span data-ttu-id="a7a70-126">Configure as outras propriedades necessárias para seu componente.</span><span class="sxs-lookup"><span data-stu-id="a7a70-126">Configure any other necessary properties for your component.</span></span>  
  
     <span data-ttu-id="a7a70-127">O código a seguir mostra a criação de um <xref:System.Windows.Forms.Timer> com seu `Interval` conjunto de propriedades.</span><span class="sxs-lookup"><span data-stu-id="a7a70-127">The following code shows the creation of a <xref:System.Windows.Forms.Timer> with its `Interval` property set.</span></span>  
  
    ```vb  
    Public Sub CreateTimer()  
       Dim timerKeepTrack As New System.Windows.Forms.Timer  
       timerKeepTrack.Interval = 1000  
    End Sub  
    ```  
  
    ```csharp  
    public void createTimer()  
    {  
       System.Windows.Forms.Timer timerKeepTrack = new  
           System.Windows.Forms.Timer();  
       timerKeepTrack.Interval = 1000;  
    }  
    ```  
  
    ```cpp  
    public:  
       void createTimer()  
       {  
          System::Windows::Forms::Timer^ timerKeepTrack = gcnew  
             System::Windows::Forms::Timer();  
          timerKeepTrack->Interval = 1000;  
       }  
    ```  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="a7a70-128">Você poderia expor seu computador local a um risco de segurança por meio da rede referenciando um UserControl mal-intencionado.</span><span class="sxs-lookup"><span data-stu-id="a7a70-128">You might expose your local computer to a security risk through the network by referencing a malicious UserControl.</span></span> <span data-ttu-id="a7a70-129">Isso seria um problemas apenas no caso de uma pessoa mal-intencionada criar um controle personalizado prejudicial e você adicioná-lo por engano ao seu projeto.</span><span class="sxs-lookup"><span data-stu-id="a7a70-129">This would only be a concern in the case of a malicious person creating a damaging custom control, followed by you mistakenly adding it to your project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7a70-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a7a70-130">See also</span></span>

- [<span data-ttu-id="a7a70-131">Controles dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a7a70-131">Windows Forms Controls</span></span>](index.md)
- [<span data-ttu-id="a7a70-132">Como: Adicionar controles ao Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a7a70-132">How to: Add Controls to Windows Forms</span></span>](how-to-add-controls-to-windows-forms.md)
- [<span data-ttu-id="a7a70-133">Como: Adicionar controles ActiveX ao Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a7a70-133">How to: Add ActiveX Controls to Windows Forms</span></span>](how-to-add-activex-controls-to-windows-forms.md)
- [<span data-ttu-id="a7a70-134">Como: Copiar controles entre Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a7a70-134">How to: Copy Controls Between Windows Forms</span></span>](how-to-copy-controls-between-windows-forms.md)
- [<span data-ttu-id="a7a70-135">Colocando controles nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a7a70-135">Putting Controls on Windows Forms</span></span>](putting-controls-on-windows-forms.md)
- [<span data-ttu-id="a7a70-136">Rotulando controles individuais dos Windows Forms e fornecendo atalhos para eles</span><span class="sxs-lookup"><span data-stu-id="a7a70-136">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [<span data-ttu-id="a7a70-137">Controles a serem usados nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a7a70-137">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
- [<span data-ttu-id="a7a70-138">Controles dos Windows Forms por função</span><span class="sxs-lookup"><span data-stu-id="a7a70-138">Windows Forms Controls by Function</span></span>](windows-forms-controls-by-function.md)
