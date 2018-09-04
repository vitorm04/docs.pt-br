---
title: Como associar controles dos Windows Forms a valores de banco de dados DBNull
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- BindingSource component [Windows Forms], binding to DBNull values
- examples [Windows Forms], BindingSource component
- controls [Windows Forms], binding to DBNull values
ms.assetid: 96494e6f-5f40-4f83-af97-bbd7192c2af8
ms.openlocfilehash: 278fd4ed0622673a49bfaa2567501b832bd535d3
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43506046"
---
# <a name="how-to-bind-windows-forms-controls-to-dbnull-database-values"></a>Como associar controles dos Windows Forms a valores de banco de dados DBNull
Quando você associa os controles dos Windows Forms a uma fonte de dados e a fonte de dados retorna um <xref:System.DBNull> valor, você pode substituir um valor apropriado sem tratamento, formatação ou análise de eventos. O <xref:System.Windows.Forms.Binding.NullValue%2A> propriedade converterá <xref:System.DBNull> a um objeto especificado ao formatar ou analisar os valores de fonte de dados.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir demonstra como associar um <xref:System.DBNull> valor em duas situações diferentes. O primeiro demonstra como definir a <xref:System.Windows.Forms.Binding.NullValue%2A> para uma propriedade de cadeia de caracteres; o segundo demonstra como definir o <xref:System.Windows.Forms.Binding.NullValue%2A> para uma propriedade de imagem.  
  
 [!code-csharp[System.Windows.Forms.BindingDBNull#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingDBNull/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.BindingDBNull#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingDBNull/VB/form1.vb#1)]  
  
 Os tipos de propriedade associada e o <xref:System.Windows.Forms.Binding.NullValue%2A> propriedade deve ser iguais ou ocorrerá um erro e nenhuma outra <xref:System.Windows.Forms.Binding.NullValue%2A> valores serão processados. Nessa situação, uma exceção não será gerada.  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer:  
  
-   Referências aos assemblies System, System.Data, System.Drawing e System.Windows.Forms.  
  
 Para obter informações sobre como compilar este exemplo da linha de comando para o Visual Basic ou Visual c#, consulte [compilando da linha de comando](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [criação de linha de comando com csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Você também pode criar este exemplo no Visual Studio colando o código em um novo projeto.  Consulte também [Como compilar e executar um exemplo completo de código do Windows Forms usando o Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Consulte também  
 [Componente BindingSource](../../../../docs/framework/winforms/controls/bindingsource-component.md)  
 [Como identificar erros e exceções que ocorram na associação de dados](../../../../docs/framework/winforms/controls/how-to-handle-errors-and-exceptions-that-occur-with-databinding.md)  
 [Como associar um controle do Windows Forms a um tipo](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-control-to-a-type.md)
