---
title: Associar controles a valores de banco de dados DBNull
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- BindingSource component [Windows Forms], binding to DBNull values
- examples [Windows Forms], BindingSource component
- controls [Windows Forms], binding to DBNull values
ms.assetid: 96494e6f-5f40-4f83-af97-bbd7192c2af8
ms.openlocfilehash: 175d7f5aee2540916480e2c55a485af1f9d16653
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746667"
---
# <a name="how-to-bind-windows-forms-controls-to-dbnull-database-values"></a>Como associar controles dos Windows Forms a valores de banco de dados DBNull
Quando você associa Windows Forms controles a uma fonte de dados e a fonte de dados retorna um valor de <xref:System.DBNull>, você pode substituir um valor apropriado sem manipular, formatar ou analisar eventos. A propriedade <xref:System.Windows.Forms.Binding.NullValue%2A> converterá <xref:System.DBNull> em um objeto especificado ao Formatar ou analisar os valores da fonte de dados.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir demonstra como associar um valor de <xref:System.DBNull> em duas situações diferentes. O primeiro demonstra como definir o <xref:System.Windows.Forms.Binding.NullValue%2A> para uma propriedade de cadeia de caracteres; o segundo demonstra como definir o <xref:System.Windows.Forms.Binding.NullValue%2A> para uma propriedade de imagem.  
  
 [!code-csharp[System.Windows.Forms.BindingDBNull#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingDBNull/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.BindingDBNull#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingDBNull/VB/form1.vb#1)]  
  
 Os tipos da propriedade bound e da propriedade <xref:System.Windows.Forms.Binding.NullValue%2A> devem ser iguais, ou um erro será resultado, e nenhum outro valor de <xref:System.Windows.Forms.Binding.NullValue%2A> será processado. Nessa situação, uma exceção não será gerada.  
  
## <a name="compiling-the-code"></a>Compilando o Código  
 Este exemplo requer:  
  
- Referências aos assemblies System, System.Data, System.Drawing e System.Windows.Forms.  
  
## <a name="see-also"></a>Veja também

- [Componente BindingSource](bindingsource-component.md)
- [Como identificar erros e exceções que ocorram na associação de dados](how-to-handle-errors-and-exceptions-that-occur-with-databinding.md)
- [Como associar um controle do Windows Forms a um tipo](how-to-bind-a-windows-forms-control-to-a-type.md)
