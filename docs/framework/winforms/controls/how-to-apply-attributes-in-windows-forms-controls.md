---
title: 'Como: Aplicar atributos a controles do Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], applying attributes
- attributes [Windows Forms], applying
- Windows Forms controls, applying attributes
ms.assetid: af0a3f7f-155b-4ba1-83c4-9cf721331a06
ms.openlocfilehash: 273d32927582f4467a92cd3b8f87e699c1f167d7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69922790"
---
# <a name="how-to-apply-attributes-in-windows-forms-controls"></a><span data-ttu-id="da407-102">Como: Aplicar atributos a controles do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="da407-102">How to: Apply Attributes in Windows Forms Controls</span></span>
<span data-ttu-id="da407-103">Para desenvolver componentes e controles que interagem corretamente com o ambiente de design e são executados corretamente no tempo de execução, você precisa aplicar atributos corretamente a classes e membros.</span><span class="sxs-lookup"><span data-stu-id="da407-103">To develop components and controls that interact correctly with the design environment and execute correctly at run time, you need to apply attributes correctly to classes and members.</span></span>  
  
## <a name="example"></a><span data-ttu-id="da407-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="da407-104">Example</span></span>  
 <span data-ttu-id="da407-105">O exemplo de código a seguir demonstra como usar vários atributos em um controle personalizado.</span><span class="sxs-lookup"><span data-stu-id="da407-105">The following code example demonstrates how to use several attributes on a custom control.</span></span> <span data-ttu-id="da407-106">O controle demonstra um recurso de funcionalidade em log simples.</span><span class="sxs-lookup"><span data-stu-id="da407-106">The control demonstrates a simple logging capability.</span></span> <span data-ttu-id="da407-107">Quando o controle está associado a uma fonte de dados, ele exibe os valores enviados pela fonte de dados em <xref:System.Windows.Forms.DataGridView> um controle.</span><span class="sxs-lookup"><span data-stu-id="da407-107">When the control is bound to a data source, it displays the values sent by the data source in a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="da407-108">Se um valor exceder o valor especificado pela propriedade `Threshold`, um evento `ThresholdExceeded` será gerado.</span><span class="sxs-lookup"><span data-stu-id="da407-108">If a value exceeds the value specified by the `Threshold` property, a `ThresholdExceeded` event is raised.</span></span>  
  
 <span data-ttu-id="da407-109">O `AttributesDemoControl` registra valores com uma classe `LogEntry`.</span><span class="sxs-lookup"><span data-stu-id="da407-109">The `AttributesDemoControl` logs values with a `LogEntry` class.</span></span> <span data-ttu-id="da407-110">A classe `LogEntry` é uma classe de modelo, o que significa que ela é parametrizada pelo tipo abordado pelo registro em log.</span><span class="sxs-lookup"><span data-stu-id="da407-110">The `LogEntry` class is a template class, which means it is parameterized on the type that it logs.</span></span> <span data-ttu-id="da407-111">Por exemplo, se o `AttributesDemoControl` registrar em log os valores do tipo `float`, cada instância `LogEntry` será declarada e usada da seguinte maneira.</span><span class="sxs-lookup"><span data-stu-id="da407-111">For example, if the `AttributesDemoControl` is logging values of type `float`, each `LogEntry` instance is declared and used as follows.</span></span>  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#110](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/form1.cs#110)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#110](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/form1.vb#110)]  
  
> [!NOTE]
> <span data-ttu-id="da407-112">Como `LogEntry` é parametrizado por um tipo arbitrário, ele deve usar a reflexão para operar no tipo de parâmetro.</span><span class="sxs-lookup"><span data-stu-id="da407-112">Because `LogEntry` is parameterized by an arbitrary type, it must use reflection to operate on the parameter type.</span></span> <span data-ttu-id="da407-113">Para que o recurso de limite funcione, o tipo `T` de parâmetro deve <xref:System.IComparable> implementar a interface.</span><span class="sxs-lookup"><span data-stu-id="da407-113">For the threshold feature to work, the parameter type `T` must implement the <xref:System.IComparable> interface.</span></span>  
  
 <span data-ttu-id="da407-114">O formulário que hospeda o `AttributesDemoControl` consulta um contador de desempenho periodicamente.</span><span class="sxs-lookup"><span data-stu-id="da407-114">The form that hosts the `AttributesDemoControl` queries a performance counter periodically.</span></span> <span data-ttu-id="da407-115">Cada valor é empacotado em um `LogEntry` do tipo apropriado e adicionado ao. <xref:System.Windows.Forms.BindingSource></span><span class="sxs-lookup"><span data-stu-id="da407-115">Each value is packaged in a `LogEntry` of the appropriate type and added to the form's <xref:System.Windows.Forms.BindingSource>.</span></span> <span data-ttu-id="da407-116">O `AttributesDemoControl` recebe o valor por meio de sua vinculação de dados e exibe o <xref:System.Windows.Forms.DataGridView> valor em um controle.</span><span class="sxs-lookup"><span data-stu-id="da407-116">The `AttributesDemoControl` receives the value through its data binding and displays the value in a <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#1)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#1)]  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#100](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/form1.cs#100)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#100](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/form1.vb#100)]  
  
 <span data-ttu-id="da407-117">O primeiro exemplo de código é a implementação `AttributesDemoControl`.</span><span class="sxs-lookup"><span data-stu-id="da407-117">The first code example is the `AttributesDemoControl` implementation.</span></span> <span data-ttu-id="da407-118">O segundo exemplo de código demonstra um formulário que usa o `AttributesDemoControl`.</span><span class="sxs-lookup"><span data-stu-id="da407-118">The second code example demonstrates a form that uses the `AttributesDemoControl`.</span></span>  
  
## <a name="class-level-attributes"></a><span data-ttu-id="da407-119">Atributos de nível de classe</span><span class="sxs-lookup"><span data-stu-id="da407-119">Class-level Attributes</span></span>  
 <span data-ttu-id="da407-120">Alguns atributos são aplicados no nível de classe.</span><span class="sxs-lookup"><span data-stu-id="da407-120">Some attributes are applied at the class level.</span></span> <span data-ttu-id="da407-121">O exemplo de código a seguir mostra os atributos que normalmente são aplicados a um controle do Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="da407-121">The following code example shows the attributes that are commonly applied to a Windows Forms control.</span></span>  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#20)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#20)]  
  
### <a name="typeconverter-attribute"></a><span data-ttu-id="da407-122">Atributo TypeConverter</span><span class="sxs-lookup"><span data-stu-id="da407-122">TypeConverter Attribute</span></span>  
 <span data-ttu-id="da407-123"><xref:System.ComponentModel.TypeConverterAttribute>é outro atributo de nível de classe usado com frequência.</span><span class="sxs-lookup"><span data-stu-id="da407-123"><xref:System.ComponentModel.TypeConverterAttribute> is another commonly used class-level attribute.</span></span> <span data-ttu-id="da407-124">O exemplo de código a seguir mostra seu uso para a classe `LogEntry`.</span><span class="sxs-lookup"><span data-stu-id="da407-124">The following code example shows its use for the `LogEntry` class.</span></span> <span data-ttu-id="da407-125">Este exemplo também mostra uma implementação de <xref:System.ComponentModel.TypeConverter> para o `LogEntry` tipo, chamado `LogEntryTypeConverter`.</span><span class="sxs-lookup"><span data-stu-id="da407-125">This example also shows an implementation of a <xref:System.ComponentModel.TypeConverter> for the `LogEntry` type, called `LogEntryTypeConverter`.</span></span>  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#5)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#5)]  
  
## <a name="member-level-attributes"></a><span data-ttu-id="da407-126">Atributos de nível de membro</span><span class="sxs-lookup"><span data-stu-id="da407-126">Member-level Attributes</span></span>  
 <span data-ttu-id="da407-127">Alguns atributos são aplicados no nível do membro.</span><span class="sxs-lookup"><span data-stu-id="da407-127">Some attributes are applied at the member level.</span></span> <span data-ttu-id="da407-128">O exemplo de código a seguir mostra alguns atributos que normalmente são aplicados às propriedades de controles do Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="da407-128">The following code examples show some attributes that are commonly applied to properties of Windows Forms controls.</span></span>  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#21)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#21)]  
  
### <a name="ambientvalue-attribute"></a><span data-ttu-id="da407-129">Atributo AmbientValue</span><span class="sxs-lookup"><span data-stu-id="da407-129">AmbientValue Attribute</span></span>  
 <span data-ttu-id="da407-130">O exemplo a seguir demonstra <xref:System.ComponentModel.AmbientValueAttribute> o e mostra o código que dá suporte à sua interação com o ambiente de design.</span><span class="sxs-lookup"><span data-stu-id="da407-130">The following example demonstrates the <xref:System.ComponentModel.AmbientValueAttribute> and shows code that supports its interaction with the design environment.</span></span> <span data-ttu-id="da407-131">Essa interação é chamada *ambiente*.</span><span class="sxs-lookup"><span data-stu-id="da407-131">This interaction is called *ambience*.</span></span>  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#23](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#23)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#23](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#23)]  
  
### <a name="databinding-attributes"></a><span data-ttu-id="da407-132">Atributos de associação de dados</span><span class="sxs-lookup"><span data-stu-id="da407-132">Databinding Attributes</span></span>  
 <span data-ttu-id="da407-133">Os exemplos a seguir demonstram uma implementação da associação de dados complexos.</span><span class="sxs-lookup"><span data-stu-id="da407-133">The following examples demonstrate an implementation of complex data binding.</span></span> <span data-ttu-id="da407-134">O nível <xref:System.ComponentModel.ComplexBindingPropertiesAttribute>de classe, mostrado anteriormente, especifica as `DataSource` propriedades `DataMember` e a serem usadas para a vinculação de dados.</span><span class="sxs-lookup"><span data-stu-id="da407-134">The class-level <xref:System.ComponentModel.ComplexBindingPropertiesAttribute>, shown previously, specifies the `DataSource` and `DataMember` properties to use for data binding.</span></span> <span data-ttu-id="da407-135">Especifica o tipo ao qual a `DataSource` propriedade será associada. <xref:System.ComponentModel.AttributeProviderAttribute></span><span class="sxs-lookup"><span data-stu-id="da407-135">The <xref:System.ComponentModel.AttributeProviderAttribute> specifies the type to which the `DataSource` property will bind.</span></span>  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#25](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#25)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#25](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#25)]  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#26](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#26)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#26](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#26)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="da407-136">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="da407-136">Compiling the Code</span></span>  
  
- <span data-ttu-id="da407-137">O formulário que hospeda o `AttributesDemoControl` requer uma referência ao assembly `AttributesDemoControl` para compilar.</span><span class="sxs-lookup"><span data-stu-id="da407-137">The form that hosts the `AttributesDemoControl` requires a reference to the `AttributesDemoControl` assembly in order to build.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da407-138">Consulte também</span><span class="sxs-lookup"><span data-stu-id="da407-138">See also</span></span>

- <xref:System.IComparable>
- <xref:System.Windows.Forms.DataGridView>
- [<span data-ttu-id="da407-139">Desenvolvendo controles dos Windows Forms personalizados com o .NET Framework</span><span class="sxs-lookup"><span data-stu-id="da407-139">Developing Custom Windows Forms Controls with the .NET Framework</span></span>](developing-custom-windows-forms-controls.md)
- [<span data-ttu-id="da407-140">Atributos em controles dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="da407-140">Attributes in Windows Forms Controls</span></span>](attributes-in-windows-forms-controls.md)
- <span data-ttu-id="da407-141">[Como: Serializar coleções de tipos padrão com o DesignerSerializationVisibilityAttribute](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171833(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="da407-141">[How to: Serialize Collections of Standard Types with the DesignerSerializationVisibilityAttribute](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171833(v=vs.120))</span></span>
