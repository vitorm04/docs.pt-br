---
title: Como aplicar atributos em controles dos Windows Forms
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], applying attributes
- attributes [Windows Forms], applying
- Windows Forms controls, applying attributes
ms.assetid: af0a3f7f-155b-4ba1-83c4-9cf721331a06
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4697ef7a74916bcc7b922f265262a83b8f0316d5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-apply-attributes-in-windows-forms-controls"></a>Como aplicar atributos em controles dos Windows Forms
Para desenvolver componentes e controles que interagem corretamente com o ambiente de design e são executados corretamente no tempo de execução, você precisa aplicar atributos corretamente a classes e membros.  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir demonstra como usar vários atributos em um controle personalizado. O controle demonstra um recurso de funcionalidade em log simples. Quando o controle é vinculado a uma fonte de dados, ele exibe os valores enviados pela fonte de dados em um <xref:System.Windows.Forms.DataGridView> controle. Se um valor exceder o valor especificado pela propriedade `Threshold`, um evento `ThresholdExceeded` será gerado.  
  
 O `AttributesDemoControl` registra valores com uma classe `LogEntry`. A classe `LogEntry` é uma classe de modelo, o que significa que ela é parametrizada pelo tipo abordado pelo registro em log. Por exemplo, se o `AttributesDemoControl` registrar em log os valores do tipo `float`, cada instância `LogEntry` será declarada e usada da seguinte maneira.  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#110](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/form1.cs#110)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#110](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/form1.vb#110)]  
  
> [!NOTE]
>  Como `LogEntry` é parametrizado por um tipo arbitrário, ele deve usar a reflexão para operar no tipo de parâmetro. Para o recurso de limite de trabalho, o tipo de parâmetro `T` deve implementar o <xref:System.IComparable> interface.  
  
 O formulário que hospeda o `AttributesDemoControl` consulta um contador de desempenho periodicamente. Cada valor é empacotado em um `LogEntry` do tipo apropriado e adicionado ao formulário <xref:System.Windows.Forms.BindingSource>. O `AttributesDemoControl` recebe o valor por meio de sua associação de dados e exibe o valor em uma <xref:System.Windows.Forms.DataGridView> controle.  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#1)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#1)]  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#100](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/form1.cs#100)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#100](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/form1.vb#100)]  
  
 O primeiro exemplo de código é a implementação `AttributesDemoControl`. O segundo exemplo de código demonstra um formulário que usa o `AttributesDemoControl`.  
  
## <a name="class-level-attributes"></a>Atributos de nível de classe  
 Alguns atributos são aplicados no nível de classe. O exemplo de código a seguir mostra os atributos que normalmente são aplicados a um controle do Windows Forms.  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#20)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#20)]  
  
### <a name="typeconverter-attribute"></a>Atributo TypeConverter  
 <xref:System.ComponentModel.TypeConverterAttribute>é outro atributo de nível de classe usado com frequência. O exemplo de código a seguir mostra seu uso para a classe `LogEntry`. Este exemplo também mostra uma implementação de um <xref:System.ComponentModel.TypeConverter> para o `LogEntry` tipo, chamado `LogEntryTypeConverter`.  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#5)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#5)]  
  
## <a name="member-level-attributes"></a>Atributos de nível de membro  
 Alguns atributos são aplicados no nível do membro. O exemplo de código a seguir mostra alguns atributos que normalmente são aplicados às propriedades de controles do Windows Forms.  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#21)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#21)]  
  
### <a name="ambientvalue-attribute"></a>Atributo AmbientValue  
 O exemplo a seguir demonstra o <xref:System.ComponentModel.AmbientValueAttribute> e mostra o código que dá suporte à sua interação com o ambiente de design. Essa interação é chamada *ambiente*.  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#23](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#23)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#23](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#23)]  
  
### <a name="databinding-attributes"></a>Atributos de associação de dados  
 Os exemplos a seguir demonstram uma implementação da associação de dados complexos. O nível de classe <xref:System.ComponentModel.ComplexBindingPropertiesAttribute>, conforme mostrado anteriormente, especifica o `DataSource` e `DataMember` propriedades a serem usadas para associação de dados. O <xref:System.ComponentModel.AttributeProviderAttribute> Especifica o tipo para o qual o `DataSource` propriedade associada.  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#25](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#25)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#25](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#25)]  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#26](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#26)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#26](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#26)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
  
-   O formulário que hospeda o `AttributesDemoControl` requer uma referência ao assembly `AttributesDemoControl` para compilar.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.IComparable>  
 <xref:System.Windows.Forms.DataGridView>  
 [Desenvolvendo controles dos Windows Forms personalizados com o .NET Framework](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)  
 [Atributos em controles dos Windows Forms](../../../../docs/framework/winforms/controls/attributes-in-windows-forms-controls.md)  
 [Como serializar coleções de tipos padrão com o DesignerSerializationVisibilityAttribute](http://msdn.microsoft.com/library/7829fcdd-8205-405f-8231-a1282a9835c9)
