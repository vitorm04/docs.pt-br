---
title: 'Como: Desenvolver um controle de formulários do Windows simples'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms]
- custom controls [Windows Forms], creating simple controls using code
- Control class [Windows Forms], Windows Forms
ms.assetid: 86cbe435-45b7-4cb4-9b5a-47418369758d
ms.openlocfilehash: 36891a5acbb2fe06b4ab61573e26612927587c01
ms.sourcegitcommit: 07c4368273b446555cb2c85397ea266b39d5fe50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56583830"
---
# <a name="how-to-develop-a-simple-windows-forms-control"></a><span data-ttu-id="239af-102">Como: Desenvolver um controle de formulários do Windows simples</span><span class="sxs-lookup"><span data-stu-id="239af-102">How to: Develop a Simple Windows Forms Control</span></span>
<span data-ttu-id="239af-103">Esta seção explica as etapas principais para a criação de um controle personalizado dos Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="239af-103">This section walks you through the key steps for authoring a custom Windows Forms control.</span></span> <span data-ttu-id="239af-104">O controle simples desenvolvido neste passo a passo permite que o alinhamento de seu <xref:System.Windows.Forms.Control.Text%2A> propriedade a ser alterada.</span><span class="sxs-lookup"><span data-stu-id="239af-104">The simple control developed in this walkthrough allows the alignment of its <xref:System.Windows.Forms.Control.Text%2A> property to be changed.</span></span> <span data-ttu-id="239af-105">Ele não gera ou manipula eventos.</span><span class="sxs-lookup"><span data-stu-id="239af-105">It does not raise or handle events.</span></span>  
  
### <a name="to-create-a-simple-custom-control"></a><span data-ttu-id="239af-106">Para criar um controle personalizado simples</span><span class="sxs-lookup"><span data-stu-id="239af-106">To create a simple custom control</span></span>  
  
1.  <span data-ttu-id="239af-107">Defina uma classe derivada de <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="239af-107">Define a class that derives from <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.</span></span>  
  
    ```vb  
    Public Class FirstControl  
       Inherits Control  
  
    End Class  
    ```  
  
    ```csharp  
    public class FirstControl:Control {}  
    ```  
  
2.  <span data-ttu-id="239af-108">Defina as propriedades.</span><span class="sxs-lookup"><span data-stu-id="239af-108">Define properties.</span></span> <span data-ttu-id="239af-109">(Não é necessário para definir propriedades, como um controle herda muitas propriedades do <xref:System.Windows.Forms.Control> classe, mas a maioria dos controles personalizados geralmente define propriedades adicionais.) O fragmento de código a seguir define uma propriedade chamada `TextAlignment` que `FirstControl` usa para formatar a exibição da <xref:System.Windows.Forms.Control.Text%2A> propriedade herdada de <xref:System.Windows.Forms.Control>.</span><span class="sxs-lookup"><span data-stu-id="239af-109">(You are not required to define properties, because a control inherits many properties from the <xref:System.Windows.Forms.Control> class, but most custom controls generally do define additional properties.) The following code fragment defines a property named `TextAlignment` that `FirstControl` uses to format the display of the <xref:System.Windows.Forms.Control.Text%2A> property inherited from <xref:System.Windows.Forms.Control>.</span></span> <span data-ttu-id="239af-110">Para obter mais informações sobre como definir as propriedades, consulte [Properties Overview](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/65zdfbdt(v%3dvs.120)) (Visão geral das propriedades).</span><span class="sxs-lookup"><span data-stu-id="239af-110">For more information about defining properties, see [Properties Overview](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/65zdfbdt(v%3dvs.120)).</span></span>  
  
     [!code-csharp[System.Windows.Forms.FirstControl#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/CS/FirstControl.cs#3)]
     [!code-vb[System.Windows.Forms.FirstControl#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/VB/FirstControl.vb#3)]  
  
     <span data-ttu-id="239af-111">Quando você define uma propriedade que altera a exibição visual do controle, você deve chamar o <xref:System.Windows.Forms.Control.Invalidate%2A> método para redesenhar o controle.</span><span class="sxs-lookup"><span data-stu-id="239af-111">When you set a property that changes the visual display of the control, you must invoke the <xref:System.Windows.Forms.Control.Invalidate%2A> method to redraw the control.</span></span> <span data-ttu-id="239af-112"><xref:System.Windows.Forms.Control.Invalidate%2A> é definido na classe base <xref:System.Windows.Forms.Control>.</span><span class="sxs-lookup"><span data-stu-id="239af-112"><xref:System.Windows.Forms.Control.Invalidate%2A> is defined in the base class <xref:System.Windows.Forms.Control>.</span></span>  
  
3.  <span data-ttu-id="239af-113">Substituir o protegido <xref:System.Windows.Forms.Control.OnPaint%2A> método herdado do <xref:System.Windows.Forms.Control> para fornecer a lógica de renderização para o seu controle.</span><span class="sxs-lookup"><span data-stu-id="239af-113">Override the protected <xref:System.Windows.Forms.Control.OnPaint%2A> method inherited from <xref:System.Windows.Forms.Control> to provide rendering logic to your control.</span></span> <span data-ttu-id="239af-114">Se você não substituir <xref:System.Windows.Forms.Control.OnPaint%2A>, seu controle não será possível desenhar a mesmo.</span><span class="sxs-lookup"><span data-stu-id="239af-114">If you do not override <xref:System.Windows.Forms.Control.OnPaint%2A>, your control will not be able to draw itself.</span></span> <span data-ttu-id="239af-115">No fragmento de código a seguir, o <xref:System.Windows.Forms.Control.OnPaint%2A> método exibe a <xref:System.Windows.Forms.Control.Text%2A> propriedade herdada de <xref:System.Windows.Forms.Control> com o alinhamento especificado pelo `alignmentValue` campo.</span><span class="sxs-lookup"><span data-stu-id="239af-115">In the following code fragment, the <xref:System.Windows.Forms.Control.OnPaint%2A> method displays the <xref:System.Windows.Forms.Control.Text%2A> property inherited from <xref:System.Windows.Forms.Control> with the alignment specified by the `alignmentValue` field.</span></span>  
  
     [!code-csharp[System.Windows.Forms.FirstControl#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/CS/FirstControl.cs#4)]
     [!code-vb[System.Windows.Forms.FirstControl#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/VB/FirstControl.vb#4)]  
  
4.  <span data-ttu-id="239af-116">Forneça atributos para o seu controle.</span><span class="sxs-lookup"><span data-stu-id="239af-116">Provide attributes for your control.</span></span> <span data-ttu-id="239af-117">Os atributos permitem que um designer visual exiba adequadamente seu controle, suas propriedades e eventos no tempo de design.</span><span class="sxs-lookup"><span data-stu-id="239af-117">Attributes enable a visual designer to display your control and its properties and events appropriately at design time.</span></span> <span data-ttu-id="239af-118">O fragmento de código a seguir se aplica aos atributos para a propriedade `TextAlignment`.</span><span class="sxs-lookup"><span data-stu-id="239af-118">The following code fragment applies attributes to the `TextAlignment` property.</span></span> <span data-ttu-id="239af-119">Em um designer como o Visual Studio, o <xref:System.ComponentModel.CategoryAttribute.Category%2A> atributo (mostrado no fragmento de código) faz com que a propriedade a ser exibida em uma categoria lógica.</span><span class="sxs-lookup"><span data-stu-id="239af-119">In a designer such as Visual Studio, the <xref:System.ComponentModel.CategoryAttribute.Category%2A> attribute (shown in the code fragment) causes the property to be displayed under a logical category.</span></span> <span data-ttu-id="239af-120">O <xref:System.ComponentModel.DescriptionAttribute.Description%2A> atributo faz com que uma cadeia de caracteres descritiva a ser exibido na parte inferior a **propriedades** janela quando o `TextAlignment` propriedade for selecionada.</span><span class="sxs-lookup"><span data-stu-id="239af-120">The <xref:System.ComponentModel.DescriptionAttribute.Description%2A> attribute causes a descriptive string to be displayed at the bottom of the **Properties** window when the `TextAlignment` property is selected.</span></span> <span data-ttu-id="239af-121">Para obter mais informações sobre atributos, consulte [Design-Time Attributes for Components](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/tk67c2t8(v=vs.120)) (Atributos de tempo de design para componentes).</span><span class="sxs-lookup"><span data-stu-id="239af-121">For more information about attributes, see [Design-Time Attributes for Components](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/tk67c2t8(v=vs.120)).</span></span>  
  
     [!code-csharp[System.Windows.Forms.FirstControl#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/CS/FirstControl.cs#5)]
     [!code-vb[System.Windows.Forms.FirstControl#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/VB/FirstControl.vb#5)]  
  
5.  <span data-ttu-id="239af-122">(opcional) Forneça recursos para o seu controle.</span><span class="sxs-lookup"><span data-stu-id="239af-122">(optional) Provide resources for your control.</span></span> <span data-ttu-id="239af-123">Você pode fornecer um recurso, como um bitmap, para seu controle usando uma opção do compilador (`/res` para C#) para recursos de pacote com seu controle.</span><span class="sxs-lookup"><span data-stu-id="239af-123">You can provide a resource, such as a bitmap, for your control by using a compiler option (`/res` for C#) to package resources with your control.</span></span> <span data-ttu-id="239af-124">Em tempo de execução, o recurso pode ser recuperado usando os métodos do <xref:System.Resources.ResourceManager> classe.</span><span class="sxs-lookup"><span data-stu-id="239af-124">At run time, the resource can be retrieved using the methods of the <xref:System.Resources.ResourceManager> class.</span></span> <span data-ttu-id="239af-125">Para obter mais informações sobre a criação e o uso de recursos, consulte [Resources in Desktop Apps](../../../../docs/framework/resources/index.md) (Recursos em aplicativos da Área de Trabalho).</span><span class="sxs-lookup"><span data-stu-id="239af-125">For more information about creating and using resources, see the [Resources in Desktop Apps](../../../../docs/framework/resources/index.md).</span></span>  
  
6.  <span data-ttu-id="239af-126">Compile e implante seu controle.</span><span class="sxs-lookup"><span data-stu-id="239af-126">Compile and deploy your control.</span></span> <span data-ttu-id="239af-127">Para compilar e implantar `FirstControl,`, execute as seguintes etapas:</span><span class="sxs-lookup"><span data-stu-id="239af-127">To compile and deploy `FirstControl,` execute the following steps:</span></span>  
  
    1.  <span data-ttu-id="239af-128">Salve o código no exemplo a seguir em um arquivo de origem (como FirstControl.cs ou FirstControl.vb).</span><span class="sxs-lookup"><span data-stu-id="239af-128">Save the code in the following sample to a source file (such as FirstControl.cs or FirstControl.vb).</span></span>  
  
    2.  <span data-ttu-id="239af-129">Compile o código-fonte em um assembly e salve-o no diretório do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="239af-129">Compile the source code into an assembly and save it in your application's directory.</span></span> <span data-ttu-id="239af-130">Para fazer isso, execute o seguinte comando do diretório que contém o arquivo de origem.</span><span class="sxs-lookup"><span data-stu-id="239af-130">To accomplish this, execute the following command from the directory that contains the source file.</span></span>  
  
        ```console  
        vbc -t:library -out:[path to your application's directory]/CustomWinControls.dll -r:System.dll -r:System.Windows.Forms.dll -r:System.Drawing.dll FirstControl.vb  
        ```  
  
        ```console 
        csc -t:library -out:[path to your application's directory]/CustomWinControls.dll -r:System.dll -r:System.Windows.Forms.dll -r:System.Drawing.dll FirstControl.cs  
        ```  
  
         <span data-ttu-id="239af-131">A opção do compilador `/t:library` informa o compilador que o assembly que você está criando é uma biblioteca (e não um executável).</span><span class="sxs-lookup"><span data-stu-id="239af-131">The `/t:library` compiler option tells the compiler that the assembly you are creating is a library (and not an executable).</span></span> <span data-ttu-id="239af-132">A opção `/out` especifica o caminho e o nome do assembly.</span><span class="sxs-lookup"><span data-stu-id="239af-132">The `/out` option specifies the path and name of the assembly.</span></span> <span data-ttu-id="239af-133">A opção `/r` fornece o nome dos assemblies referenciados pelo seu código.</span><span class="sxs-lookup"><span data-stu-id="239af-133">The`/r` option provides the name of the assemblies that are referenced by your code.</span></span> <span data-ttu-id="239af-134">Neste exemplo, você cria um assembly particular que somente os seus aplicativos podem usar.</span><span class="sxs-lookup"><span data-stu-id="239af-134">In this example, you create a private assembly that only your applications can use.</span></span> <span data-ttu-id="239af-135">Portanto, você precisa salvá-lo no diretório do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="239af-135">Hence, you have to save it in your application's directory.</span></span> <span data-ttu-id="239af-136">Para obter mais informações sobre o empacotamento e a implantação de um controle para distribuição, consulte [Implantação](../../../../docs/framework/deployment/index.md).</span><span class="sxs-lookup"><span data-stu-id="239af-136">For more information about packaging and deploying a control for distribution, see [Deployment](../../../../docs/framework/deployment/index.md).</span></span>  
  
 <span data-ttu-id="239af-137">O exemplo a seguir mostra o código para `FirstControl`.</span><span class="sxs-lookup"><span data-stu-id="239af-137">The following sample shows the code for `FirstControl`.</span></span> <span data-ttu-id="239af-138">O controle é colocado no namespace `CustomWinControls`.</span><span class="sxs-lookup"><span data-stu-id="239af-138">The control is enclosed in the namespace `CustomWinControls`.</span></span> <span data-ttu-id="239af-139">Um namespace fornece um agrupamento lógico de tipos relacionados.</span><span class="sxs-lookup"><span data-stu-id="239af-139">A namespace provides a logical grouping of related types.</span></span> <span data-ttu-id="239af-140">Você pode criar seu controle em um namespace novo ou existente.</span><span class="sxs-lookup"><span data-stu-id="239af-140">You can create your control in a new or existing namespace.</span></span> <span data-ttu-id="239af-141">Em C#, a declaração `using` (no Visual Basic, `Imports`) permite que os tipos sejam acessados de um namespace sem usar o nome totalmente qualificado do tipo.</span><span class="sxs-lookup"><span data-stu-id="239af-141">In C#, the `using` declaration (in Visual Basic, `Imports`) allows types to be accessed from a namespace without using the fully qualified name of the type.</span></span> <span data-ttu-id="239af-142">No exemplo a seguir, o `using` declaração permite que o código acessar a classe <xref:System.Windows.Forms.Control> partir <xref:System.Windows.Forms?displayProperty=nameWithType> simplesmente <xref:System.Windows.Forms.Control> em vez de ter que usar o nome totalmente qualificado <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="239af-142">In the following example, the `using` declaration allows code to access the class <xref:System.Windows.Forms.Control> from <xref:System.Windows.Forms?displayProperty=nameWithType> as simply <xref:System.Windows.Forms.Control> instead of having to use the fully qualified name <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.</span></span>  
  
 [!code-csharp[System.Windows.Forms.FirstControl#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/CS/FirstControl.cs#1)]
 [!code-vb[System.Windows.Forms.FirstControl#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/VB/FirstControl.vb#1)]  
  
## <a name="using-the-custom-control-on-a-form"></a><span data-ttu-id="239af-143">Usando o controle personalizado em um formulário</span><span class="sxs-lookup"><span data-stu-id="239af-143">Using the Custom Control on a Form</span></span>  
 <span data-ttu-id="239af-144">O exemplo a seguir mostra um formulário simples que usa `FirstControl`.</span><span class="sxs-lookup"><span data-stu-id="239af-144">The following example shows a simple form that uses `FirstControl`.</span></span> <span data-ttu-id="239af-145">Ele cria três instâncias de `FirstControl`, cada uma com um valor diferente para a propriedade `TextAlignment`.</span><span class="sxs-lookup"><span data-stu-id="239af-145">It creates three instances of `FirstControl`, each with a different value for the `TextAlignment` property.</span></span>  
  
#### <a name="to-compile-and-run-this-sample"></a><span data-ttu-id="239af-146">Para compilar e executar esse exemplo</span><span class="sxs-lookup"><span data-stu-id="239af-146">To compile and run this sample</span></span>  
  
1.  <span data-ttu-id="239af-147">Salve o código no exemplo a seguir em um arquivo de origem (SimpleForm.cs ou SimpleForms.vb).</span><span class="sxs-lookup"><span data-stu-id="239af-147">Save the code in the following example to a source file (SimpleForm.cs or SimpleForms.vb).</span></span>  
  
2.  <span data-ttu-id="239af-148">Compile o código-fonte em um assembly executável, executando o seguinte comando do diretório que contém o arquivo de origem.</span><span class="sxs-lookup"><span data-stu-id="239af-148">Compile the source code into an executable assembly by executing the following command from the directory that contains the source file.</span></span>  
  
    ```console  
    vbc -r:CustomWinControls.dll -r:System.dll -r:System.Windows.Forms.dll -r:System.Drawing.dll SimpleForm.vb  
    ```  
  
    ```console 
    csc -r:CustomWinControls.dll -r:System.dll -r:System.Windows.Forms.dll -r:System.Drawing.dll SimpleForm.cs  
    ```  
  
     <span data-ttu-id="239af-149">Customwincontrols é o assembly que contém a classe `FirstControl`.</span><span class="sxs-lookup"><span data-stu-id="239af-149">CustomWinControls.dll is the assembly that contains the class `FirstControl`.</span></span> <span data-ttu-id="239af-150">Esse assembly deve estar no mesmo diretório que o arquivo de origem para o formulário que o acessa (SimpleForm.cs ou SimpleForms.vb).</span><span class="sxs-lookup"><span data-stu-id="239af-150">This assembly must be in the same directory as the source file for the form that accesses it (SimpleForm.cs or SimpleForms.vb).</span></span>  
  
3.  <span data-ttu-id="239af-151">Execute SimpleForm.exe usando o seguinte comando.</span><span class="sxs-lookup"><span data-stu-id="239af-151">Execute SimpleForm.exe using the following command.</span></span>  
  
    ```console
    SimpleForm  
    ```  
  
 [!code-csharp[System.Windows.Forms.FirstControl#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/CS/SimpleForm.cs#10)]
 [!code-vb[System.Windows.Forms.FirstControl#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/VB/SimpleForm.vb#10)]  
  
## <a name="see-also"></a><span data-ttu-id="239af-152">Consulte também</span><span class="sxs-lookup"><span data-stu-id="239af-152">See also</span></span>
- [<span data-ttu-id="239af-153">Propriedades em controles do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="239af-153">Properties in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/properties-in-windows-forms-controls.md)
- [<span data-ttu-id="239af-154">Eventos em controles do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="239af-154">Events in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/events-in-windows-forms-controls.md)
