---
title: Propriedades em controles dos Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- custom controls [Windows Forms], properties overview (using code)
- controls [Windows Forms], properties
- properties [Windows Forms]
ms.assetid: 2785279b-fb57-4937-8f6b-2050e475db6f
ms.openlocfilehash: 37db3f16a17acc7f3a6e594bd284ba368801e70a
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/08/2018
ms.locfileid: "48850160"
---
# <a name="properties-in-windows-forms-controls"></a>Propriedades em controles dos Windows Forms
Um controle dos Windows Forms herda muitas propriedades da classe base <xref:System.Windows.Forms.Control?displayProperty=nameWithType>. Estas incluem propriedades como <xref:System.Windows.Forms.Control.Font%2A>, <xref:System.Windows.Forms.Control.ForeColor%2A>, <xref:System.Windows.Forms.Control.BackColor%2A>, <xref:System.Windows.Forms.Control.Bounds%2A>, <xref:System.Windows.Forms.Control.ClientRectangle%2A>, <xref:System.Windows.Forms.Control.DisplayRectangle%2A>, <xref:System.Windows.Forms.Control.Enabled%2A>, <xref:System.Windows.Forms.Control.Focused%2A>, <xref:System.Windows.Forms.Control.Height%2A>, <xref:System.Windows.Forms.Control.Width%2A>, <xref:System.Windows.Forms.Control.Visible%2A>, <xref:System.Windows.Forms.Control.AutoSize%2A>e muitos outros. Para obter detalhes sobre as propriedades herdadas, consulte <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.  
  
 Você pode substituir as propriedades herdadas em seu controle, bem como definir novas propriedades.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Definindo uma propriedade](../../../../docs/framework/winforms/controls/defining-a-property-in-windows-forms-controls.md)  
 Mostra como implementar uma propriedade para um controle personalizado ou componente e mostra como integrar a propriedade ambiente no de design.  
  
 [Definindo valores padrão com os métodos ShouldSerialize e Reset](../../../../docs/framework/winforms/controls/defining-default-values-with-the-shouldserialize-and-reset-methods.md)  
 Mostra como definir valores de propriedade padrão para um controle ou componente personalizado.  
  
 [Eventos alterados por propriedade](../../../../docs/framework/winforms/controls/property-changed-events.md)  
 Descreve como habilitar as notificações de alteração de propriedade quando um valor da propriedade for alterado.  
  
 [Como expor as propriedades de controles constituintes](../../../../docs/framework/winforms/controls/how-to-expose-properties-of-constituent-controls.md)  
 Mostra como expor as propriedades de controles constituintes em um controle de composição o personalizado.  
  
 [Implementação do método em controles personalizados](../../../../docs/framework/winforms/controls/method-implementation-in-custom-controls.md)  
 Descreve como implementar métodos de componentes e controles personalizados.  
  
## <a name="reference"></a>Referência  
 <xref:System.Windows.Forms.UserControl>  
 Documenta a classe base para implementar controles de composição.  
  
 <xref:System.ComponentModel.TypeConverterAttribute>  
 Documenta o atributo que especifica o <xref:System.ComponentModel.TypeConverter> a ser usado para um tipo de propriedade personalizada.  
  
 <xref:System.ComponentModel.EditorAttribute>  
 Documenta o atributo que especifica o <xref:System.Drawing.Design.UITypeEditor> a ser usado para uma propriedade personalizada.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Atributos em controles dos Windows Forms](../../../../docs/framework/winforms/controls/attributes-in-windows-forms-controls.md)  
 Descreve os atributos que você pode aplicar a propriedades ou outros membros de seus componentes e controles personalizados.  
  
 [Atributos de tempo de design para componentes](https://msdn.microsoft.com/library/12050fe3-9327-4509-9e21-4ee2494b95c3)  
 Lista atributos de metadados para aplicar a componentes e controles para que eles sejam exibidos corretamente em tempo de design em designers visuais.  
  
 [Estendendo o suporte ao tempo de design](https://msdn.microsoft.com/library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)  
 Descreve como implementar classes como editores e designers que fornecem suporte ao tempo de design.
