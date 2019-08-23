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
# <a name="how-to-apply-attributes-in-windows-forms-controls"></a>Como: Aplicar atributos a controles do Windows Forms
Para desenvolver componentes e controles que interagem corretamente com o ambiente de design e são executados corretamente no tempo de execução, você precisa aplicar atributos corretamente a classes e membros.  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir demonstra como usar vários atributos em um controle personalizado. O controle demonstra um recurso de funcionalidade em log simples. Quando o controle está associado a uma fonte de dados, ele exibe os valores enviados pela fonte de dados em <xref:System.Windows.Forms.DataGridView> um controle. Se um valor exceder o valor especificado pela propriedade `Threshold`, um evento `ThresholdExceeded` será gerado.  
  
 O `AttributesDemoControl` registra valores com uma classe `LogEntry`. A classe `LogEntry` é uma classe de modelo, o que significa que ela é parametrizada pelo tipo abordado pelo registro em log. Por exemplo, se o `AttributesDemoControl` registrar em log os valores do tipo `float`, cada instância `LogEntry` será declarada e usada da seguinte maneira.  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#110](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/form1.cs#110)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#110](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/form1.vb#110)]  
  
> [!NOTE]
> Como `LogEntry` é parametrizado por um tipo arbitrário, ele deve usar a reflexão para operar no tipo de parâmetro. Para que o recurso de limite funcione, o tipo `T` de parâmetro deve <xref:System.IComparable> implementar a interface.  
  
 O formulário que hospeda o `AttributesDemoControl` consulta um contador de desempenho periodicamente. Cada valor é empacotado em um `LogEntry` do tipo apropriado e adicionado ao. <xref:System.Windows.Forms.BindingSource> O `AttributesDemoControl` recebe o valor por meio de sua vinculação de dados e exibe o <xref:System.Windows.Forms.DataGridView> valor em um controle.  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#1)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#1)]  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#100](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/form1.cs#100)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#100](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/form1.vb#100)]  
  
 O primeiro exemplo de código é a implementação `AttributesDemoControl`. O segundo exemplo de código demonstra um formulário que usa o `AttributesDemoControl`.  
  
## <a name="class-level-attributes"></a>Atributos de nível de classe  
 Alguns atributos são aplicados no nível de classe. O exemplo de código a seguir mostra os atributos que normalmente são aplicados a um controle do Windows Forms.  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#20)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#20)]  
  
### <a name="typeconverter-attribute"></a>Atributo TypeConverter  
 <xref:System.ComponentModel.TypeConverterAttribute>é outro atributo de nível de classe usado com frequência. O exemplo de código a seguir mostra seu uso para a classe `LogEntry`. Este exemplo também mostra uma implementação de <xref:System.ComponentModel.TypeConverter> para o `LogEntry` tipo, chamado `LogEntryTypeConverter`.  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#5)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#5)]  
  
## <a name="member-level-attributes"></a>Atributos de nível de membro  
 Alguns atributos são aplicados no nível do membro. O exemplo de código a seguir mostra alguns atributos que normalmente são aplicados às propriedades de controles do Windows Forms.  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#21)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#21)]  
  
### <a name="ambientvalue-attribute"></a>Atributo AmbientValue  
 O exemplo a seguir demonstra <xref:System.ComponentModel.AmbientValueAttribute> o e mostra o código que dá suporte à sua interação com o ambiente de design. Essa interação é chamada *ambiente*.  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#23](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#23)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#23](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#23)]  
  
### <a name="databinding-attributes"></a>Atributos de associação de dados  
 Os exemplos a seguir demonstram uma implementação da associação de dados complexos. O nível <xref:System.ComponentModel.ComplexBindingPropertiesAttribute>de classe, mostrado anteriormente, especifica as `DataSource` propriedades `DataMember` e a serem usadas para a vinculação de dados. Especifica o tipo ao qual a `DataSource` propriedade será associada. <xref:System.ComponentModel.AttributeProviderAttribute>  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#25](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#25)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#25](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#25)]  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#26](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#26)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#26](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#26)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
  
- O formulário que hospeda o `AttributesDemoControl` requer uma referência ao assembly `AttributesDemoControl` para compilar.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.IComparable>
- <xref:System.Windows.Forms.DataGridView>
- [Desenvolvendo controles dos Windows Forms personalizados com o .NET Framework](developing-custom-windows-forms-controls.md)
- [Atributos em controles dos Windows Forms](attributes-in-windows-forms-controls.md)
- [Como: Serializar coleções de tipos padrão com o DesignerSerializationVisibilityAttribute](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171833(v=vs.120))
