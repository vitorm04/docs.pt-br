---
title: "Como avançar em um DataSet com o controle BindingNavigator dos Windows Forms"
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
- datasets [Windows Forms], moving through
- BindingNavigator control [Windows Forms], moving through datasets
- examples [Windows Forms], BindingNavigator control
ms.assetid: 146d97be-3d97-400e-accb-860bbf47729d
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 22d71e2cacc7ae9e1341e3f19253dad009d9b617
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-move-through-a-dataset-with-the-windows-forms-bindingnavigator-control"></a>Como avançar em um DataSet com o controle BindingNavigator dos Windows Forms
Como criar aplicativos orientados a dados, geralmente você precisará exibir conjuntos de dados para os usuários. O <xref:System.Windows.Forms.BindingNavigator> controle, em conjunto com o <xref:System.Windows.Forms.BindingSource> componente, fornece uma solução conveniente e extensível para mover uma coleção e exibir itens em sequência.  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir demonstra como usar um <xref:System.Windows.Forms.BindingNavigator> controle para mover dados. O conjunto é contido em um <xref:System.Data.DataView>, que está associada a um <xref:System.Windows.Forms.TextBox> controlar com um <xref:System.Windows.Forms.BindingSource> componente.  
  
> [!NOTE]
>  O armazenamento das informações confidenciais (tal como uma senha) dentro da cadeia de conexão pode afetar a segurança do aplicativo. O uso da Autenticação do Windows (também conhecida como segurança integrada) é uma maneira mais segura de controlar o acesso a um banco de dados. Para obter mais informações, consulte [Protegendo informações de conexão](../../../../docs/framework/data/adonet/protecting-connection-information.md).  
  
 [!code-csharp[System.Windows.Forms.DataNavigator#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataNavigator/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataNavigator#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataNavigator/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer:  
  
-   Referência aos conjuntos System, System.Data, System.Drawing, System.Windows.Forms e System.Xml.  
  
 Para obter informações sobre como compilar este exemplo na linha de comando para [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] ou [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], consulte [Building from the Command Line (Compilando na linha de comando)](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [Compilando pela linha de comando com csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Também é possível compilar este exemplo em [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] colando o código em um novo projeto.  Consulte também [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)) (Como compilar e executar um exemplo completo de código dos Windows Forms usando o Visual Studio).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.BindingSource>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.BindingSource>  
 [Controle BindingNavigator](../../../../docs/framework/winforms/controls/bindingnavigator-control-windows-forms.md)  
 [Componente BindingSource](../../../../docs/framework/winforms/controls/bindingsource-component.md)  
 [Como associar um controle dos Windows Forms a um tipo](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-control-to-a-type.md)
