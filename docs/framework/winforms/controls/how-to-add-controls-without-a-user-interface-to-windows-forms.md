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
ms.openlocfilehash: bc1f844e5a2cf4d4f3b64ebf20e935f36ff85e12
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/23/2019
ms.locfileid: "69987087"
---
# <a name="how-to-add-controls-without-a-user-interface-to-windows-forms"></a><span data-ttu-id="12ae6-102">Como: Adicionar controles sem uma interface do usuário ao Windows Forms</span><span class="sxs-lookup"><span data-stu-id="12ae6-102">How to: Add Controls Without a User Interface to Windows Forms</span></span>

<span data-ttu-id="12ae6-103">Um controle (ou componente) não visual fornece funcionalidade ao seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="12ae6-103">A nonvisual control (or component) provides functionality to your application.</span></span> <span data-ttu-id="12ae6-104">Diferente de outros controles, os componentes não fornecem uma interface do usuário ao usuário e, portanto, não precisam ser exibido na superfície do Designer de Formulários do Windows.</span><span class="sxs-lookup"><span data-stu-id="12ae6-104">Unlike other controls, components do not provide a user interface to the user and thus do not need to be displayed on the Windows Forms Designer surface.</span></span> <span data-ttu-id="12ae6-105">Quando um componente é adicionado a um formulário, o Designer de Formulários do Windows exibe uma bandeja redimensionável na parte inferior do formulário em que todos os componentes são exibidos.</span><span class="sxs-lookup"><span data-stu-id="12ae6-105">When a component is added to a form, the Windows Forms Designer displays a resizable tray at the bottom of the form where all components are displayed.</span></span> <span data-ttu-id="12ae6-106">Quando um controle é adicionado à bandeja de componentes, você pode selecionar o componente e definir suas propriedades como faria com qualquer outro controle no formulário.</span><span class="sxs-lookup"><span data-stu-id="12ae6-106">Once a control has been added to the component tray, you can select the component and set its properties as you would any other control on the form.</span></span>

## <a name="add-a-component-to-a-windows-form"></a><span data-ttu-id="12ae6-107">Adicionar um componente a um formulário do Windows</span><span class="sxs-lookup"><span data-stu-id="12ae6-107">Add a component to a Windows Form</span></span>

1. <span data-ttu-id="12ae6-108">Abra o formulário no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="12ae6-108">Open the form in Visual Studio.</span></span> <span data-ttu-id="12ae6-109">Para obter detalhes, confira [Como: Exibir Windows Forms no designer](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w5yd62ts(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="12ae6-109">For details, see [How to: Display Windows Forms in the Designer](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w5yd62ts(v=vs.100)).</span></span>

2. <span data-ttu-id="12ae6-110">Na **Caixa de ferramentas**, clique em um componente e arraste-o para o formulário.</span><span class="sxs-lookup"><span data-stu-id="12ae6-110">In the **Toolbox**, click a component and drag it to your form.</span></span>

     <span data-ttu-id="12ae6-111">O componente aparece na bandeja de componentes.</span><span class="sxs-lookup"><span data-stu-id="12ae6-111">Your component appears in the component tray.</span></span>

<span data-ttu-id="12ae6-112">Além disso, os componentes podem ser adicionados a um formulário no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="12ae6-112">Furthermore, components can be added to a form at run time.</span></span> <span data-ttu-id="12ae6-113">Esse é um cenário comum, especialmente porque os componentes não têm uma expressão visual, diferente de controles que têm uma interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="12ae6-113">This is a common scenario, especially because components do not have a visual expression, unlike controls that have a user interface.</span></span> <span data-ttu-id="12ae6-114">No exemplo a seguir, um <xref:System.Windows.Forms.Timer> componente é adicionado em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="12ae6-114">In the example below, a <xref:System.Windows.Forms.Timer> component is added at run time.</span></span> <span data-ttu-id="12ae6-115">(Observe que o Visual Studio contém vários temporizadores diferentes; nesse caso, use um componente Windows Forms <xref:System.Windows.Forms.Timer> .</span><span class="sxs-lookup"><span data-stu-id="12ae6-115">(Note that Visual Studio contains a number of different timers; in this case, use a Windows Forms <xref:System.Windows.Forms.Timer> component.</span></span> <span data-ttu-id="12ae6-116">Para obter mais informações sobre os diferentes temporizadores no Visual Studio, consulte [introdução a temporizadores baseados em servidor](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/tb9yt5e6(v=vs.90)).)</span><span class="sxs-lookup"><span data-stu-id="12ae6-116">For more information about the different timers in Visual Studio, see [Introduction to Server-Based Timers](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/tb9yt5e6(v=vs.90)).)</span></span>

> [!CAUTION]
> <span data-ttu-id="12ae6-117">Componentes geralmente têm propriedades específicas de controle que devem ser definidas para o componente funcionar com eficiência.</span><span class="sxs-lookup"><span data-stu-id="12ae6-117">Components often have control-specific properties that must be set for the component to function effectively.</span></span> <span data-ttu-id="12ae6-118">No caso do <xref:System.Windows.Forms.Timer> componente abaixo, você define a `Interval` propriedade.</span><span class="sxs-lookup"><span data-stu-id="12ae6-118">In the case of the <xref:System.Windows.Forms.Timer> component below, you set the `Interval` property.</span></span> <span data-ttu-id="12ae6-119">Verifique se as propriedades necessárias para o componente foram definidas ao adicioná-lo ao projeto.</span><span class="sxs-lookup"><span data-stu-id="12ae6-119">Be sure, when adding components to your project, that you set the properties necessary for that component.</span></span>

## <a name="add-a-component-to-a-windows-form-programmatically"></a><span data-ttu-id="12ae6-120">Adicionar um componente a um formulário do Windows programaticamente</span><span class="sxs-lookup"><span data-stu-id="12ae6-120">Add a component to a Windows Form programmatically</span></span>

1. <span data-ttu-id="12ae6-121">Crie uma instância da <xref:System.Windows.Forms.Timer> classe no código.</span><span class="sxs-lookup"><span data-stu-id="12ae6-121">Create an instance of the <xref:System.Windows.Forms.Timer> class in code.</span></span>

2. <span data-ttu-id="12ae6-122">Defina a propriedade `Interval` para determinar o tempo entre os tiques do temporizador.</span><span class="sxs-lookup"><span data-stu-id="12ae6-122">Set the `Interval` property to determine the time between ticks of the timer.</span></span>

3. <span data-ttu-id="12ae6-123">Configure as outras propriedades necessárias para seu componente.</span><span class="sxs-lookup"><span data-stu-id="12ae6-123">Configure any other necessary properties for your component.</span></span>

     <span data-ttu-id="12ae6-124">O código a seguir mostra a criação de <xref:System.Windows.Forms.Timer> um com `Interval` seu conjunto de propriedades.</span><span class="sxs-lookup"><span data-stu-id="12ae6-124">The following code shows the creation of a <xref:System.Windows.Forms.Timer> with its `Interval` property set.</span></span>

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
    > <span data-ttu-id="12ae6-125">Você poderia expor seu computador local a um risco de segurança por meio da rede referenciando um UserControl mal-intencionado.</span><span class="sxs-lookup"><span data-stu-id="12ae6-125">You might expose your local computer to a security risk through the network by referencing a malicious UserControl.</span></span> <span data-ttu-id="12ae6-126">Isso seria um problemas apenas no caso de uma pessoa mal-intencionada criar um controle personalizado prejudicial e você adicioná-lo por engano ao seu projeto.</span><span class="sxs-lookup"><span data-stu-id="12ae6-126">This would only be a concern in the case of a malicious person creating a damaging custom control, followed by you mistakenly adding it to your project.</span></span>

## <a name="see-also"></a><span data-ttu-id="12ae6-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="12ae6-127">See also</span></span>

- [<span data-ttu-id="12ae6-128">Controles dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="12ae6-128">Windows Forms Controls</span></span>](index.md)
- [<span data-ttu-id="12ae6-129">Como: Adicionar controles a Windows Forms</span><span class="sxs-lookup"><span data-stu-id="12ae6-129">How to: Add Controls to Windows Forms</span></span>](how-to-add-controls-to-windows-forms.md)
- [<span data-ttu-id="12ae6-130">Como: Adicionar controles ActiveX a Windows Forms</span><span class="sxs-lookup"><span data-stu-id="12ae6-130">How to: Add ActiveX Controls to Windows Forms</span></span>](how-to-add-activex-controls-to-windows-forms.md)
- [<span data-ttu-id="12ae6-131">Colocando controles nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="12ae6-131">Putting Controls on Windows Forms</span></span>](putting-controls-on-windows-forms.md)
- [<span data-ttu-id="12ae6-132">Rotulando controles individuais dos Windows Forms e fornecendo atalhos para eles</span><span class="sxs-lookup"><span data-stu-id="12ae6-132">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [<span data-ttu-id="12ae6-133">Controles a serem usados nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="12ae6-133">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
- [<span data-ttu-id="12ae6-134">Controles dos Windows Forms por função</span><span class="sxs-lookup"><span data-stu-id="12ae6-134">Windows Forms Controls by Function</span></span>](windows-forms-controls-by-function.md)
