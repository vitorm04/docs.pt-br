---
title: Definindo uma propriedade em controles dos Windows Forms
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- properties [Windows Forms], defining in code
- custom controls [Windows Forms], defining properties in code
ms.assetid: c2eb8277-a842-4d99-89a9-647b901a0434
ms.openlocfilehash: 84273d2fab36df287eaca70f5f32fd8024a9204d
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57712195"
---
# <a name="defining-a-property-in-windows-forms-controls"></a><span data-ttu-id="4f914-102">Definindo uma propriedade em controles dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="4f914-102">Defining a Property in Windows Forms Controls</span></span>
<span data-ttu-id="4f914-103">Para obter uma visão geral das propriedades, consulte [Visão geral das propriedades](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/65zdfbdt(v=vs.120)).</span><span class="sxs-lookup"><span data-stu-id="4f914-103">For an overview of properties, see [Properties Overview](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/65zdfbdt(v=vs.120)).</span></span> <span data-ttu-id="4f914-104">Há algumas considerações importantes ao definir uma propriedade:</span><span class="sxs-lookup"><span data-stu-id="4f914-104">There are a few important considerations when defining a property:</span></span>  
  
-   <span data-ttu-id="4f914-105">Você deve aplicar atributos às propriedades que você definir.</span><span class="sxs-lookup"><span data-stu-id="4f914-105">You must apply attributes to the properties you define.</span></span> <span data-ttu-id="4f914-106">Atributos especificam como o designer deve exibir uma propriedade.</span><span class="sxs-lookup"><span data-stu-id="4f914-106">Attributes specify how the designer should display a property.</span></span> <span data-ttu-id="4f914-107">Para obter detalhes, consulte [Atributos de tempo de design para componentes](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/tk67c2t8(v=vs.120)).</span><span class="sxs-lookup"><span data-stu-id="4f914-107">For details, see [Design-Time Attributes for Components](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/tk67c2t8(v=vs.120)).</span></span>  
  
-   <span data-ttu-id="4f914-108">Se alterar a propriedade afeta a exibição visual do controle, chame o <xref:System.Windows.Forms.Control.Invalidate%2A> método (que o controle herda de <xref:System.Windows.Forms.Control>) do `set` acessador.</span><span class="sxs-lookup"><span data-stu-id="4f914-108">If changing the property affects the visual display of the control, call the <xref:System.Windows.Forms.Control.Invalidate%2A> method (that your control inherits from <xref:System.Windows.Forms.Control>) from the `set` accessor.</span></span> <span data-ttu-id="4f914-109"><xref:System.Windows.Forms.Control.Invalidate%2A> por sua vez chama o <xref:System.Windows.Forms.Control.OnPaint%2A> método, que redesenha o controle.</span><span class="sxs-lookup"><span data-stu-id="4f914-109"><xref:System.Windows.Forms.Control.Invalidate%2A> in turn calls the <xref:System.Windows.Forms.Control.OnPaint%2A> method, which redraws the control.</span></span> <span data-ttu-id="4f914-110">Diversas chamadas para <xref:System.Windows.Forms.Control.Invalidate%2A> resultar em uma única chamada para <xref:System.Windows.Forms.Control.OnPaint%2A> para maior eficiência.</span><span class="sxs-lookup"><span data-stu-id="4f914-110">Multiple calls to <xref:System.Windows.Forms.Control.Invalidate%2A> result in a single call to <xref:System.Windows.Forms.Control.OnPaint%2A> for efficiency.</span></span>  
  
-   <span data-ttu-id="4f914-111">A biblioteca de classes do .NET Framework fornece conversores de tipo para tipos de dados comuns como inteiros, números decimais, valores boolianos e outros.</span><span class="sxs-lookup"><span data-stu-id="4f914-111">The .NET Framework class library provides type converters for common data types such as integers, decimal numbers, Boolean values, and others.</span></span> <span data-ttu-id="4f914-112">A finalidade de um conversor de tipo geralmente é fornecer conversão de cadeia de caracteres para valor (de dados de cadeia de caracteres em outros tipos de dados).</span><span class="sxs-lookup"><span data-stu-id="4f914-112">The purpose of a type converter is generally to provide string-to-value conversion (from string data to other data types).</span></span> <span data-ttu-id="4f914-113">Tipos de dados comuns são associados a conversores de tipo padrão que convertem valores em cadeias de caracteres e nos tipos de dados apropriados.</span><span class="sxs-lookup"><span data-stu-id="4f914-113">Common data types are associated with default type converters that convert values into strings and strings into the appropriate data types.</span></span> <span data-ttu-id="4f914-114">Se você definir uma propriedade que é um tipo de dados personalizado (isto é, fora do padrão), será necessário aplicar um atributo que especifica o conversor de tipo para associá-lo a essa propriedade.</span><span class="sxs-lookup"><span data-stu-id="4f914-114">If you define a property that is a custom (that is, nonstandard) data type, you will have to apply an attribute that specifies the type converter to associate with that property.</span></span> <span data-ttu-id="4f914-115">Você também pode usar um atributo para associar um editor de tipos de interface do usuário personalizado a uma propriedade.</span><span class="sxs-lookup"><span data-stu-id="4f914-115">You can also use an attribute to associate a custom UI type editor with a property.</span></span> <span data-ttu-id="4f914-116">Um editor de tipos de interface do usuário fornece uma interface do usuário para editar uma propriedade ou tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="4f914-116">A UI type editor provides a user interface for editing a property or data type.</span></span> <span data-ttu-id="4f914-117">Um seletor de cor é um exemplo de um editor de tipos de interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="4f914-117">A color picker is an example of a UI type editor.</span></span> <span data-ttu-id="4f914-118">Exemplos de atributos são fornecidos no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="4f914-118">Examples of attributes are given at the end of this topic.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="4f914-119">Se um conversor de tipo ou um editor de tipos de interface do usuário não estiver disponível para a propriedade personalizada, você poderá implementar um conforme descrito em [Estendendo o suporte no tempo de design](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/37899azc(v=vs.120)).</span><span class="sxs-lookup"><span data-stu-id="4f914-119">If a type converter or a UI type editor is not available for your custom property, you can implement one as described in [Extending Design-Time Support](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/37899azc(v=vs.120)).</span></span>  
  
 <span data-ttu-id="4f914-120">O fragmento de código a seguir define uma propriedade personalizada chamada `EndColor` para o controle personalizado `FlashTrackBar`.</span><span class="sxs-lookup"><span data-stu-id="4f914-120">The following code fragment defines a custom property named `EndColor` for the custom control `FlashTrackBar`.</span></span>  
  
```vb  
Public Class FlashTrackBar  
   Inherits Control  
   ...  
   ' Private data member that backs the EndColor property.  
   Private _endColor As Color = Color.LimeGreen  
  
   ' The Category attribute tells the designer to display  
   ' it in the Flash grouping.   
   ' The Description attribute provides a description of  
   ' the property.   
   <Category("Flash"), _  
   Description("The ending color of the bar.")>  _  
   Public Property EndColor() As Color  
      ' The public property EndColor accesses _endColor.  
      Get  
         Return _endColor  
      End Get  
      Set  
         _endColor = value  
         If Not (baseBackground Is Nothing) And showGradient Then  
            baseBackground.Dispose()  
            baseBackground = Nothing  
         End If  
         ' The Invalidate method calls the OnPaint method, which redraws    
         ' the control.  
         Invalidate()  
      End Set  
   End Property  
   ...  
End Class  
```  
  
```csharp  
public class FlashTrackBar : Control {  
   ...  
   // Private data member that backs the EndColor property.  
   private Color endColor = Color.LimeGreen;  
   // The Category attribute tells the designer to display  
   // it in the Flash grouping.   
   // The Description attribute provides a description of  
   // the property.   
   [  
   Category("Flash"),  
   Description("The ending color of the bar.")  
   ]  
   // The public property EndColor accesses endColor.  
   public Color EndColor {  
      get {  
         return endColor;  
      }  
      set {  
         endColor = value;  
         if (baseBackground != null && showGradient) {  
            baseBackground.Dispose();  
            baseBackground = null;  
         }  
         // The Invalidate method calls the OnPaint method, which redraws   
         // the control.  
         Invalidate();  
      }  
   }  
   ...  
}  
```  
  
 <span data-ttu-id="4f914-121">O fragmento de código a seguir associa um conversor de tipo e um editor de tipo à interface do usuário com a propriedade `Value`.</span><span class="sxs-lookup"><span data-stu-id="4f914-121">The following code fragment associates a type converter and a UI type editor with the property `Value`.</span></span> <span data-ttu-id="4f914-122">Nesse caso `Value` é um inteiro e tem um conversor de tipo padrão, mas o <xref:System.ComponentModel.TypeConverterAttribute> atributo se aplica a um conversor de tipo personalizado (`FlashTrackBarValueConverter`) que permite que o designer para exibi-lo como uma porcentagem.</span><span class="sxs-lookup"><span data-stu-id="4f914-122">In this case `Value` is an integer and has a default type converter, but the <xref:System.ComponentModel.TypeConverterAttribute> attribute applies a custom type converter (`FlashTrackBarValueConverter`) that enables the designer to display it as a percentage.</span></span> <span data-ttu-id="4f914-123">O editor de tipo da interface do usuário, `FlashTrackBarValueEditor`, permite que o percentual seja exibido visualmente.</span><span class="sxs-lookup"><span data-stu-id="4f914-123">The UI type editor, `FlashTrackBarValueEditor`, allows the percentage to be displayed visually.</span></span> <span data-ttu-id="4f914-124">Este exemplo também mostra que o conversor de tipo ou o editor especificado pelo <xref:System.ComponentModel.TypeConverterAttribute> ou <xref:System.ComponentModel.EditorAttribute> atributo substitui o conversor padrão.</span><span class="sxs-lookup"><span data-stu-id="4f914-124">This example also shows that the type converter or editor specified by the <xref:System.ComponentModel.TypeConverterAttribute> or <xref:System.ComponentModel.EditorAttribute> attribute overrides the default converter.</span></span>  
  
```vb  
<Category("Flash"), _  
TypeConverter(GetType(FlashTrackBarValueConverter)), _  
Editor(GetType(FlashTrackBarValueEditor), _  
GetType(UITypeEditor)), _  
Description("The current value of the track bar.  You can enter an actual value or a percentage.")>  _  
Public ReadOnly Property Value() As Integer  
...  
End Property  
```  
  
```csharp  
[  
Category("Flash"),   
TypeConverter(typeof(FlashTrackBarValueConverter)),  
Editor(typeof(FlashTrackBarValueEditor), typeof(UITypeEditor)),  
Description("The current value of the track bar.  You can enter an actual value or a percentage.")  
]  
public int Value {  
...  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="4f914-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4f914-125">See also</span></span>
- [<span data-ttu-id="4f914-126">Propriedades em controles do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="4f914-126">Properties in Windows Forms Controls</span></span>](properties-in-windows-forms-controls.md)
- [<span data-ttu-id="4f914-127">Definindo valores padrão com os métodos ShouldSerialize e Reset</span><span class="sxs-lookup"><span data-stu-id="4f914-127">Defining Default Values with the ShouldSerialize and Reset Methods</span></span>](defining-default-values-with-the-shouldserialize-and-reset-methods.md)
- [<span data-ttu-id="4f914-128">Eventos alterados por propriedade</span><span class="sxs-lookup"><span data-stu-id="4f914-128">Property-Changed Events</span></span>](property-changed-events.md)
- [<span data-ttu-id="4f914-129">Atributos em controles dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="4f914-129">Attributes in Windows Forms Controls</span></span>](attributes-in-windows-forms-controls.md)
