---
title: 'Como: Criar Controles para o Windows Forms'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], creating
- UserControl class [Windows Forms], Windows Forms
- custom controls [Windows Forms], creating
ms.assetid: 7570e982-545b-4c3a-a7c7-55581d313400
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 45a6ae68102204ad8506027065c2676e02fdd7a3
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/24/2019
ms.locfileid: "70015911"
---
# <a name="how-to-author-controls-for-windows-forms"></a><span data-ttu-id="f4a6a-102">Como: Controles de autor para Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f4a6a-102">How to: Author controls for Windows Forms</span></span>

<span data-ttu-id="f4a6a-103">Um controle representa um link gráfico entre o usuário e o programa.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-103">A control represents a graphical link between the user and the program.</span></span> <span data-ttu-id="f4a6a-104">Um controle pode fornecer ou processar dados, aceitar a entrada do usuário, responder a eventos ou executar quaisquer outras funções que conectam o usuário ao aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-104">A control can provide or process data, accept user input, respond to events, or perform any number of other functions that connect the user and the application.</span></span> <span data-ttu-id="f4a6a-105">Como um controle é essencialmente um componente com uma interface gráfica, ele pode cumprir qualquer função realizada por um componente, além de oferecer interação ao usuário.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-105">Because a control is essentially a component with a graphical interface, it can serve any function that a component does, as well as provide user interaction.</span></span> <span data-ttu-id="f4a6a-106">Os controles são criados para atender a objetivos específicos e a criação de controles é apenas outra tarefa de programação.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-106">Controls are created to serve specific purposes, and authoring controls is just another programming task.</span></span> <span data-ttu-id="f4a6a-107">Com isso em mente, as etapas a seguir representam uma visão geral do processo de criação de controles.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-107">With that in mind, the following steps represent an overview of the control authoring process.</span></span> <span data-ttu-id="f4a6a-108">Os links fornecem informações adicionais sobre as etapas individuais.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-108">Links provide additional information on the individual steps.</span></span>

## <a name="to-author-a-control"></a><span data-ttu-id="f4a6a-109">Criar um controle</span><span class="sxs-lookup"><span data-stu-id="f4a6a-109">To author a control</span></span>

1. <span data-ttu-id="f4a6a-110">Determine o que o controle deverá realizar ou qual será o papel executado por ele no aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-110">Determine what you want your control to accomplish, or what part it will play in your application.</span></span> <span data-ttu-id="f4a6a-111">Os fatores a serem considerados incluem:</span><span class="sxs-lookup"><span data-stu-id="f4a6a-111">Factors to consider are:</span></span>

    - <span data-ttu-id="f4a6a-112">Que tipo de interface gráfica será necessária?</span><span class="sxs-lookup"><span data-stu-id="f4a6a-112">What kind of graphical interface do you need?</span></span>

    - <span data-ttu-id="f4a6a-113">Quais as interações específicas do usuário esse controle manipulará?</span><span class="sxs-lookup"><span data-stu-id="f4a6a-113">What specific user interactions will this control handle?</span></span>

    - <span data-ttu-id="f4a6a-114">A funcionalidade necessária é fornecida por algum dos controles existentes?</span><span class="sxs-lookup"><span data-stu-id="f4a6a-114">Is the functionality you need provided by any existing controls?</span></span>

    - <span data-ttu-id="f4a6a-115">É possível obter a funcionalidade necessária combinando vários controles do Windows Forms?</span><span class="sxs-lookup"><span data-stu-id="f4a6a-115">Can you get the functionality you need by combining several Windows Forms controls?</span></span>

2. <span data-ttu-id="f4a6a-116">Caso seja necessário um modelo de objeto para o controle, determine como a funcionalidade será distribuída ao longo do modelo de objeto e divida-a entre o controle e os subobjetos.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-116">If you need an object model for your control, determine how functionality will be distributed throughout the object model, and divide up functionality between the control and any subobjects.</span></span> <span data-ttu-id="f4a6a-117">Um modelo de objeto poderá ser útil se você estiver planejando um controle complexo ou desejar incorporar várias funcionalidades.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-117">An object model may be useful if you are planning a complex control, or want to incorporate several functionalities.</span></span>

3. <span data-ttu-id="f4a6a-118">Determine o tipo de controle (por exemplo, controle de usuário, controle personalizado, controle herdado do Windows Forms) necessário.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-118">Determine the type of control (for example, user control, custom control, inherited Windows Forms control) you need.</span></span> <span data-ttu-id="f4a6a-119">Para obter detalhes, consulte [Recomendações do Tipo de Controle](control-type-recommendations.md) e [Variedades de Controles Personalizados](varieties-of-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="f4a6a-119">For details, see [Control Type Recommendations](control-type-recommendations.md) and [Varieties of Custom Controls](varieties-of-custom-controls.md).</span></span>

4. <span data-ttu-id="f4a6a-120">Expresse funcionalidades como propriedades, métodos e eventos do controle e seus subobjetos ou estruturas subsidiárias e atribua níveis de acesso apropriados (por exemplo, público, protegido e assim por diante).</span><span class="sxs-lookup"><span data-stu-id="f4a6a-120">Express functionality as properties, methods, and events of the control and its subobjects or subsidiary structures, and assign appropriate access levels (for example, public, protected, and so on).</span></span>

5. <span data-ttu-id="f4a6a-121">Se uma pintura personalizada for necessária para o controle, adicione código a ele.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-121">If you need custom painting for your control, add code for it.</span></span> <span data-ttu-id="f4a6a-122">Para obter detalhes, consulte [Pintura e renderização de controle personalizado](custom-control-painting-and-rendering.md).</span><span class="sxs-lookup"><span data-stu-id="f4a6a-122">For details, see [Custom Control Painting and Rendering](custom-control-painting-and-rendering.md).</span></span>

6. <span data-ttu-id="f4a6a-123">Se o controle for herdado de <xref:System.Windows.Forms.UserControl>, você poderá testar seu comportamento de tempo de execução criando o projeto de controle e executando-o no contêiner de teste de **UserControl**.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-123">If your control inherits from <xref:System.Windows.Forms.UserControl>, you can test its runtime behavior by building the control project and running it in the **UserControl Test Container**.</span></span> <span data-ttu-id="f4a6a-124">Para obter mais informações, confira [Como: Testar o comportamento de tempo de execução de um](how-to-test-the-run-time-behavior-of-a-usercontrol.md)UserControl.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-124">For more information, see [How to: Test the Run-Time Behavior of a UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span></span>

7. <span data-ttu-id="f4a6a-125">Também é possível testar e depurar o controle criando um novo projeto, como um Aplicativo do Windows, e colocá-lo em um contêiner.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-125">You can also test and debug your control by creating a new project, such as a Windows Application, and placing it into a container.</span></span> <span data-ttu-id="f4a6a-126">Esse processo é demonstrado como parte [do passo a passos: Criação de um controle](walkthrough-authoring-a-composite-control-with-visual-csharp.md)composto.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-126">This process is demonstrated as part of [Walkthrough: Authoring a Composite Control](walkthrough-authoring-a-composite-control-with-visual-csharp.md).</span></span>

8. <span data-ttu-id="f4a6a-127">Ao adicionar cada recurso, adicione recursos ao projeto de teste para praticar a nova funcionalidade.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-127">As you add each feature, add features to your test project to exercise the new functionality.</span></span>

9. <span data-ttu-id="f4a6a-128">Repita, refinando o design.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-128">Repeat, refining the design.</span></span>

10. <span data-ttu-id="f4a6a-129">Empacote e implante o controle.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-129">Package and deploy your control.</span></span> <span data-ttu-id="f4a6a-130">Para obter detalhes, consulte [primeira olhada na implantação no Visual Studio](/visualstudio/deployment/deploying-applications-services-and-components).</span><span class="sxs-lookup"><span data-stu-id="f4a6a-130">For details, see [First look at deployment in Visual Studio](/visualstudio/deployment/deploying-applications-services-and-components).</span></span>

## <a name="see-also"></a><span data-ttu-id="f4a6a-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f4a6a-131">See also</span></span>

- [<span data-ttu-id="f4a6a-132">Como: Herdar da classe UserControl</span><span class="sxs-lookup"><span data-stu-id="f4a6a-132">How to: Inherit from the UserControl Class</span></span>](how-to-inherit-from-the-usercontrol-class.md)
- [<span data-ttu-id="f4a6a-133">Como: Herdar da classe de controle</span><span class="sxs-lookup"><span data-stu-id="f4a6a-133">How to: Inherit from the Control Class</span></span>](how-to-inherit-from-the-control-class.md)
- [<span data-ttu-id="f4a6a-134">Como: Herdar de controles de Windows Forms existentes</span><span class="sxs-lookup"><span data-stu-id="f4a6a-134">How to: Inherit from Existing Windows Forms Controls</span></span>](how-to-inherit-from-existing-windows-forms-controls.md)
- [<span data-ttu-id="f4a6a-135">Como: Testar o comportamento de tempo de execução de um UserControl</span><span class="sxs-lookup"><span data-stu-id="f4a6a-135">How to: Test the Run-Time Behavior of a UserControl</span></span>](how-to-test-the-run-time-behavior-of-a-usercontrol.md)
- [<span data-ttu-id="f4a6a-136">Variedades de controles personalizados</span><span class="sxs-lookup"><span data-stu-id="f4a6a-136">Varieties of Custom Controls</span></span>](varieties-of-custom-controls.md)
