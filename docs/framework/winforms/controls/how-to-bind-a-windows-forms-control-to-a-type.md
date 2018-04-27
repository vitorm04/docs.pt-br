---
title: Como associar um controle dos Windows Forms a um tipo
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], binding to a type
- BindingSource component [Windows Forms], binding to a type
- types [Windows Forms], binding controls to
ms.assetid: 94faeebb-d2bc-45d6-86d7-96a42661b43d
caps.latest.revision: 19
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a1782d7af7dc7155834926f4b94cf57adf6c4d53
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-bind-a-windows-forms-control-to-a-type"></a>Como associar um controle dos Windows Forms a um tipo
Quando estiver criando controles que interagem com os dados, às vezes, achará necessário associar um controle a um tipo, em vez de um objeto. Essa situação ocorre especialmente em tempo de design, quando os dados podem não estar disponíveis, mas seus controles ligados a dados ainda precisam exibir informações da interface pública de um tipo. Por exemplo, você pode associar um <xref:System.Windows.Forms.DataGridView> controle a um objeto exposto por um serviço Web e deseja que o <xref:System.Windows.Forms.DataGridView> controle para rotular suas colunas em tempo de design com o membro nomes de um tipo personalizado.  
  
 Você pode facilmente associar um controle a um tipo com o <xref:System.Windows.Forms.BindingSource> componente.  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir demonstra como associar um <xref:System.Windows.Forms.DataGridView> controle para um tipo personalizado usando um <xref:System.Windows.Forms.BindingSource> componente. Quando você executa o exemplo, você observará o <xref:System.Windows.Forms.DataGridView> intitulada colunas que refletem as propriedades de um `Customer` do objeto, antes do controle é preenchido com dados. O exemplo tem um botão Add Customer para adicionar dados ao <xref:System.Windows.Forms.DataGridView> controle. Quando você clica no botão, uma nova `Customer` objeto é adicionado para o <xref:System.Windows.Forms.BindingSource>. Em um cenário do mundo real, os dados podem ser obtidos por uma chamada para um serviço Web ou outra fonte de dados.  
  
 [!code-csharp[System.Windows.Forms.DataConnector.BindingToType#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.BindingToType/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnector.BindingToType#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.BindingToType/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer:  
  
-   Referências aos assemblies Sistema e System.Windows.Forms.  
  
 Para obter informações sobre como criar este exemplo da linha de comando para o Visual Basic ou Visual c#, consulte [Compilando a partir da linha de comando](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [criação de linha de comando com csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Também é possível compilar este exemplo em [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] colando o código em um novo projeto.  Consulte também [Como compilar e executar um exemplo completo de código do Windows Forms usando o Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.BindingNavigator>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.BindingSource>  
 [Componente BindingSource](../../../../docs/framework/winforms/controls/bindingsource-component.md)
