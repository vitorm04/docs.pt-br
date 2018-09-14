---
title: Como aplicar atributos em controles dos Windows Forms
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], applying attributes
- attributes [Windows Forms], applying
- Windows Forms controls, applying attributes
ms.assetid: af0a3f7f-155b-4ba1-83c4-9cf721331a06
ms.openlocfilehash: 1ab54b0c6828a0648fecfc293b6a7143b012ad6a
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/14/2018
ms.locfileid: "45592952"
---
# <a name="how-to-apply-attributes-in-windows-forms-controls"></a><span data-ttu-id="e7552-102">Como aplicar atributos em controles dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e7552-102">How to: Apply Attributes in Windows Forms Controls</span></span>
<span data-ttu-id="e7552-103">Para desenvolver componentes e controles que interagem corretamente com o ambiente de design e são executados corretamente no tempo de execução, você precisa aplicar atributos corretamente a classes e membros.</span><span class="sxs-lookup"><span data-stu-id="e7552-103">To develop components and controls that interact correctly with the design environment and execute correctly at run time, you need to apply attributes correctly to classes and members.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e7552-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e7552-104">Example</span></span>  
 <span data-ttu-id="e7552-105">O exemplo de código a seguir demonstra como usar vários atributos em um controle personalizado.</span><span class="sxs-lookup"><span data-stu-id="e7552-105">The following code example demonstrates how to use several attributes on a custom control.</span></span> <span data-ttu-id="e7552-106">O controle demonstra um recurso de funcionalidade em log simples.</span><span class="sxs-lookup"><span data-stu-id="e7552-106">The control demonstrates a simple logging capability.</span></span> <span data-ttu-id="e7552-107">Quando o controle está vinculado a uma fonte de dados, ele exibe os valores enviados pela fonte de dados em um <xref:System.Windows.Forms.DataGridView> controle.</span><span class="sxs-lookup"><span data-stu-id="e7552-107">When the control is bound to a data source, it displays the values sent by the data source in a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="e7552-108">Se um valor exceder o valor especificado pela propriedade `Threshold`, um evento `ThresholdExceeded` será gerado.</span><span class="sxs-lookup"><span data-stu-id="e7552-108">If a value exceeds the value specified by the `Threshold` property, a `ThresholdExceeded` event is raised.</span></span>  
  
 <span data-ttu-id="e7552-109">O `AttributesDemoControl` registra valores com uma classe `LogEntry`.</span><span class="sxs-lookup"><span data-stu-id="e7552-109">The `AttributesDemoControl` logs values with a `LogEntry` class.</span></span> <span data-ttu-id="e7552-110">A classe `LogEntry` é uma classe de modelo, o que significa que ela é parametrizada pelo tipo abordado pelo registro em log.</span><span class="sxs-lookup"><span data-stu-id="e7552-110">The `LogEntry` class is a template class, which means it is parameterized on the type that it logs.</span></span> <span data-ttu-id="e7552-111">Por exemplo, se o `AttributesDemoControl` registrar em log os valores do tipo `float`, cada instância `LogEntry` será declarada e usada da seguinte maneira.</span><span class="sxs-lookup"><span data-stu-id="e7552-111">For example, if the `AttributesDemoControl` is logging values of type `float`, each `LogEntry` instance is declared and used as follows.</span></span>  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#110](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/form1.cs#110)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#110](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/form1.vb#110)]  
  
> [!NOTE]
>  <span data-ttu-id="e7552-112">Como `LogEntry` é parametrizado por um tipo arbitrário, ele deve usar a reflexão para operar no tipo de parâmetro.</span><span class="sxs-lookup"><span data-stu-id="e7552-112">Because `LogEntry` is parameterized by an arbitrary type, it must use reflection to operate on the parameter type.</span></span> <span data-ttu-id="e7552-113">Para o recurso de limite funcione, o tipo de parâmetro `T` deve implementar o <xref:System.IComparable> interface.</span><span class="sxs-lookup"><span data-stu-id="e7552-113">For the threshold feature to work, the parameter type `T` must implement the <xref:System.IComparable> interface.</span></span>  
  
 <span data-ttu-id="e7552-114">O formulário que hospeda o `AttributesDemoControl` consulta um contador de desempenho periodicamente.</span><span class="sxs-lookup"><span data-stu-id="e7552-114">The form that hosts the `AttributesDemoControl` queries a performance counter periodically.</span></span> <span data-ttu-id="e7552-115">Cada valor é empacotado em uma `LogEntry` do tipo apropriado e adicionado ao formulário <xref:System.Windows.Forms.BindingSource>.</span><span class="sxs-lookup"><span data-stu-id="e7552-115">Each value is packaged in a `LogEntry` of the appropriate type and added to the form's <xref:System.Windows.Forms.BindingSource>.</span></span> <span data-ttu-id="e7552-116">O `AttributesDemoControl` recebe o valor por meio de sua associação de dados e exibe o valor em uma <xref:System.Windows.Forms.DataGridView> controle.</span><span class="sxs-lookup"><span data-stu-id="e7552-116">The `AttributesDemoControl` receives the value through its data binding and displays the value in a <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#1)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#1)]  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#100](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/form1.cs#100)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#100](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/form1.vb#100)]  
  
 <span data-ttu-id="e7552-117">O primeiro exemplo de código é a implementação `AttributesDemoControl`.</span><span class="sxs-lookup"><span data-stu-id="e7552-117">The first code example is the `AttributesDemoControl` implementation.</span></span> <span data-ttu-id="e7552-118">O segundo exemplo de código demonstra um formulário que usa o `AttributesDemoControl`.</span><span class="sxs-lookup"><span data-stu-id="e7552-118">The second code example demonstrates a form that uses the `AttributesDemoControl`.</span></span>  
  
## <a name="class-level-attributes"></a><span data-ttu-id="e7552-119">Atributos de nível de classe</span><span class="sxs-lookup"><span data-stu-id="e7552-119">Class-level Attributes</span></span>  
 <span data-ttu-id="e7552-120">Alguns atributos são aplicados no nível de classe.</span><span class="sxs-lookup"><span data-stu-id="e7552-120">Some attributes are applied at the class level.</span></span> <span data-ttu-id="e7552-121">O exemplo de código a seguir mostra os atributos que normalmente são aplicados a um controle do Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="e7552-121">The following code example shows the attributes that are commonly applied to a Windows Forms control.</span></span>  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#20)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#20)]  
  
### <a name="typeconverter-attribute"></a><span data-ttu-id="e7552-122">Atributo TypeConverter</span><span class="sxs-lookup"><span data-stu-id="e7552-122">TypeConverter Attribute</span></span>  
 <span data-ttu-id="e7552-123"><xref:System.ComponentModel.TypeConverterAttribute> é outro atributo de nível de classe comumente usado.</span><span class="sxs-lookup"><span data-stu-id="e7552-123"><xref:System.ComponentModel.TypeConverterAttribute> is another commonly used class-level attribute.</span></span> <span data-ttu-id="e7552-124">O exemplo de código a seguir mostra seu uso para a classe `LogEntry`.</span><span class="sxs-lookup"><span data-stu-id="e7552-124">The following code example shows its use for the `LogEntry` class.</span></span> <span data-ttu-id="e7552-125">Este exemplo também mostra uma implementação de um <xref:System.ComponentModel.TypeConverter> para o `LogEntry` tipo, chamado `LogEntryTypeConverter`.</span><span class="sxs-lookup"><span data-stu-id="e7552-125">This example also shows an implementation of a <xref:System.ComponentModel.TypeConverter> for the `LogEntry` type, called `LogEntryTypeConverter`.</span></span>  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#5)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#5)]  
  
## <a name="member-level-attributes"></a><span data-ttu-id="e7552-126">Atributos de nível de membro</span><span class="sxs-lookup"><span data-stu-id="e7552-126">Member-level Attributes</span></span>  
 <span data-ttu-id="e7552-127">Alguns atributos são aplicados no nível do membro.</span><span class="sxs-lookup"><span data-stu-id="e7552-127">Some attributes are applied at the member level.</span></span> <span data-ttu-id="e7552-128">O exemplo de código a seguir mostra alguns atributos que normalmente são aplicados às propriedades de controles do Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="e7552-128">The following code examples show some attributes that are commonly applied to properties of Windows Forms controls.</span></span>  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#21)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#21)]  
  
### <a name="ambientvalue-attribute"></a><span data-ttu-id="e7552-129">Atributo AmbientValue</span><span class="sxs-lookup"><span data-stu-id="e7552-129">AmbientValue Attribute</span></span>  
 <span data-ttu-id="e7552-130">O exemplo a seguir demonstra o <xref:System.ComponentModel.AmbientValueAttribute> e mostra o código que dá suporte à sua interação com o ambiente de design.</span><span class="sxs-lookup"><span data-stu-id="e7552-130">The following example demonstrates the <xref:System.ComponentModel.AmbientValueAttribute> and shows code that supports its interaction with the design environment.</span></span> <span data-ttu-id="e7552-131">Essa interação é chamada *ambiente*.</span><span class="sxs-lookup"><span data-stu-id="e7552-131">This interaction is called *ambience*.</span></span>  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#23](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#23)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#23](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#23)]  
  
### <a name="databinding-attributes"></a><span data-ttu-id="e7552-132">Atributos de associação de dados</span><span class="sxs-lookup"><span data-stu-id="e7552-132">Databinding Attributes</span></span>  
 <span data-ttu-id="e7552-133">Os exemplos a seguir demonstram uma implementação da associação de dados complexos.</span><span class="sxs-lookup"><span data-stu-id="e7552-133">The following examples demonstrate an implementation of complex data binding.</span></span> <span data-ttu-id="e7552-134">O nível de classe <xref:System.ComponentModel.ComplexBindingPropertiesAttribute>, conforme mostrado anteriormente, especifica o `DataSource` e `DataMember` propriedades a serem usadas para associação de dados.</span><span class="sxs-lookup"><span data-stu-id="e7552-134">The class-level <xref:System.ComponentModel.ComplexBindingPropertiesAttribute>, shown previously, specifies the `DataSource` and `DataMember` properties to use for data binding.</span></span> <span data-ttu-id="e7552-135">O <xref:System.ComponentModel.AttributeProviderAttribute> Especifica o tipo ao qual o `DataSource` associará a propriedade.</span><span class="sxs-lookup"><span data-stu-id="e7552-135">The <xref:System.ComponentModel.AttributeProviderAttribute> specifies the type to which the `DataSource` property will bind.</span></span>  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#25](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#25)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#25](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#25)]  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#26](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#26)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#26](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#26)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e7552-136">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="e7552-136">Compiling the Code</span></span>  
  
-   <span data-ttu-id="e7552-137">O formulário que hospeda o `AttributesDemoControl` requer uma referência ao assembly `AttributesDemoControl` para compilar.</span><span class="sxs-lookup"><span data-stu-id="e7552-137">The form that hosts the `AttributesDemoControl` requires a reference to the `AttributesDemoControl` assembly in order to build.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7552-138">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e7552-138">See Also</span></span>  
 <xref:System.IComparable>  
 <xref:System.Windows.Forms.DataGridView>  
 [<span data-ttu-id="e7552-139">Desenvolvendo controles dos Windows Forms personalizados com o .NET Framework</span><span class="sxs-lookup"><span data-stu-id="e7552-139">Developing Custom Windows Forms Controls with the .NET Framework</span></span>](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)  
 [<span data-ttu-id="e7552-140">Atributos em controles dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e7552-140">Attributes in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/attributes-in-windows-forms-controls.md)  
 [<span data-ttu-id="e7552-141">Como serializar coleções de tipos padrão com o DesignerSerializationVisibilityAttribute</span><span class="sxs-lookup"><span data-stu-id="e7552-141">How to: Serialize Collections of Standard Types with the DesignerSerializationVisibilityAttribute</span></span>](https://msdn.microsoft.com/library/7829fcdd-8205-405f-8231-a1282a9835c9)
