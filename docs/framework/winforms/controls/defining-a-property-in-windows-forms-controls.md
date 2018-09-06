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
ms.openlocfilehash: c21aee867fc78c55e62eb183bb1a12ebf1c472e8
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43858660"
---
# <a name="defining-a-property-in-windows-forms-controls"></a>Definindo uma propriedade em controles dos Windows Forms
Para obter uma visão geral das propriedades, consulte [Visão geral das propriedades](https://msdn.microsoft.com/library/8f1a1ff1-0f05-40e0-bfdf-80de8fff7d52). Há algumas considerações importantes ao definir uma propriedade:  
  
-   Você deve aplicar atributos às propriedades que você definir. Atributos especificam como o designer deve exibir uma propriedade. Para obter detalhes, consulte [Atributos de tempo de design para componentes](https://msdn.microsoft.com/library/12050fe3-9327-4509-9e21-4ee2494b95c3).  
  
-   Se alterar a propriedade afeta a exibição visual do controle, chame o <xref:System.Windows.Forms.Control.Invalidate%2A> método (que o controle herda de <xref:System.Windows.Forms.Control>) do `set` acessador. <xref:System.Windows.Forms.Control.Invalidate%2A> por sua vez chama o <xref:System.Windows.Forms.Control.OnPaint%2A> método, que redesenha o controle. Diversas chamadas para <xref:System.Windows.Forms.Control.Invalidate%2A> resultar em uma única chamada para <xref:System.Windows.Forms.Control.OnPaint%2A> para maior eficiência.  
  
-   A biblioteca de classes do .NET Framework fornece conversores de tipo para tipos de dados comuns como inteiros, números decimais, valores boolianos e outros. A finalidade de um conversor de tipo geralmente é fornecer conversão de cadeia de caracteres para valor (de dados de cadeia de caracteres em outros tipos de dados). Tipos de dados comuns são associados a conversores de tipo padrão que convertem valores em cadeias de caracteres e nos tipos de dados apropriados. Se você definir uma propriedade que é um tipo de dados personalizado (isto é, fora do padrão), será necessário aplicar um atributo que especifica o conversor de tipo para associá-lo a essa propriedade. Você também pode usar um atributo para associar um editor de tipos de interface do usuário personalizado a uma propriedade. Um editor de tipos de interface do usuário fornece uma interface do usuário para editar uma propriedade ou tipo de dados. Um seletor de cor é um exemplo de um editor de tipos de interface do usuário. Exemplos de atributos são fornecidos no final deste tópico.  
  
    > [!NOTE]
    >  Se um conversor de tipo ou um editor de tipos de interface do usuário não estiver disponível para a propriedade personalizada, você poderá implementar um conforme descrito em [Estendendo o suporte no tempo de design](https://msdn.microsoft.com/library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2).  
  
 O fragmento de código a seguir define uma propriedade personalizada chamada `EndColor` para o controle personalizado `FlashTrackBar`.  
  
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
  
 O fragmento de código a seguir associa um conversor de tipo e um editor de tipo à interface do usuário com a propriedade `Value`. Nesse caso `Value` é um inteiro e tem um conversor de tipo padrão, mas o <xref:System.ComponentModel.TypeConverterAttribute> atributo se aplica a um conversor de tipo personalizado (`FlashTrackBarValueConverter`) que permite que o designer para exibi-lo como uma porcentagem. O editor de tipo da interface do usuário, `FlashTrackBarValueEditor`, permite que o percentual seja exibido visualmente. Este exemplo também mostra que o conversor de tipo ou o editor especificado pelo <xref:System.ComponentModel.TypeConverterAttribute> ou <xref:System.ComponentModel.EditorAttribute> atributo substitui o conversor padrão.  
  
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
  
## <a name="see-also"></a>Consulte também  
 [Propriedades em controles do Windows Forms](../../../../docs/framework/winforms/controls/properties-in-windows-forms-controls.md)  
 [Definindo valores padrão com os métodos ShouldSerialize e Reset](../../../../docs/framework/winforms/controls/defining-default-values-with-the-shouldserialize-and-reset-methods.md)  
 [Eventos alterados por propriedade](../../../../docs/framework/winforms/controls/property-changed-events.md)  
 [Atributos em controles dos Windows Forms](../../../../docs/framework/winforms/controls/attributes-in-windows-forms-controls.md)
