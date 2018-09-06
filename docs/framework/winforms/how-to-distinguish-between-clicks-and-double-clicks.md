---
title: Como distinguir entre cliques e cliques duplos
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- mouse [Windows Forms], click
- mouse [Windows Forms], double-click
- mouse clicks [Windows Forms], single versus double
ms.assetid: d836ac8c-85bc-4f3a-a761-8aee03dc682c
ms.openlocfilehash: 84d085700091c4e7b8658e8eac4cf86fbd7730d5
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43802480"
---
# <a name="how-to-distinguish-between-clicks-and-double-clicks"></a>Como distinguir entre cliques e cliques duplos
Normalmente, um único *clique* inicia uma interface do usuário e um *clique duplo* estende a ação. Por exemplo, um clique normalmente seleciona um item e um clique duplo edita o item selecionado. No entanto, eventos de clique a formulários do Windows não acomodam facilmente um cenário onde um clique e um clique duplo executam ações incompatíveis, como uma ação associada à <xref:System.Windows.Forms.Control.Click> ou <xref:System.Windows.Forms.Control.MouseClick> eventos é executado antes da ação ligada para o <xref:System.Windows.Forms.Control.DoubleClick>ou <xref:System.Windows.Forms.Control.MouseDoubleClick> eventos. Este tópico demonstra duas soluções para esse problema. Uma solução é manipular o evento de clique duplo e reverter as ações no tratamento de evento de clique. Em raras situações, você talvez seja necessário simular um clique e comportamento de clique duplo manipulando o <xref:System.Windows.Forms.Control.MouseDown> evento e, usando o <xref:System.Windows.Forms.SystemInformation.DoubleClickTime%2A> e <xref:System.Windows.Forms.SystemInformation.DoubleClickSize%2A> propriedades do <xref:System.Windows.Forms.SystemInformation> classe. Você medir o tempo entre cliques e se um segundo clique ocorre antes do valor de <xref:System.Windows.Forms.SystemInformation.DoubleClickTime%2A> for atingido e o clique foi dentro de um retângulo definido por <xref:System.Windows.Forms.SystemInformation.DoubleClickSize%2A>, executar a ação de clique duplo; caso contrário, execute a ação de clique.  
  
### <a name="to-roll-back-a-click-action"></a>Reverter uma ação de clique  
  
-   Verifique se o controle em que você está trabalhando tem um comportamento de clique duplo padrão. Se não estiver, habilite o controle com o <xref:System.Windows.Forms.Control.SetStyle%2A> método. Trate o evento de clique duplo e reverta a ação de clique, bem como a ação de clique duplo. O exemplo de código a seguir demonstra um como criar um botão personalizado com clique duplo habilitado, bem como reverter a ação de clique no código de tratamento de eventos de clique duplo.  
  
     [!code-csharp[System.Windows.Forms.ButtonDoubleClick#1](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ButtonDoubleClick/CS/Form1.cs#1)]
     [!code-vb[System.Windows.Forms.ButtonDoubleClick#1](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ButtonDoubleClick/VB/Form1.vb#1)]  
  
### <a name="to-distinguish-between-clicks-in-the-mousedown-event"></a>Distinguir entre cliques no evento MouseDown  
  
-   Lidar com o <xref:System.Windows.Forms.Control.MouseDown> eventos e determinar o local e o tempo de espaço entre os cliques usando apropriado <xref:System.Windows.Forms.SystemInformation> propriedades e um <xref:System.Windows.Forms.Timer> componente. Execute a ação apropriada dependendo se ocorreu um clique ou um clique duplo. O exemplo de código a seguir demonstra como fazer isso.  
  
     [!code-cpp[System.Windows.Forms.SingleVersusDoubleClick#0](../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.SingleVersusDoubleClick/cpp/form1.cpp#0)]
     [!code-csharp[System.Windows.Forms.SingleVersusDoubleClick#0](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.SingleVersusDoubleClick/CS/form1.cs#0)]
     [!code-vb[System.Windows.Forms.SingleVersusDoubleClick#0](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.SingleVersusDoubleClick/VB/form1.vb#0)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Esses exemplos precisam de:  
  
-   Referências aos assemblies System, System.Drawing e System.Windows.Forms.  
  
 Para obter informações sobre como compilar esses exemplos da linha de comando para o Visual Basic ou Visual c#, consulte [compilando da linha de comando](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [criação de linha de comando com csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Você também pode criar esses exemplos no Visual Studio colando o código em novos projetos.  Consulte também [Como compilar e executar um exemplo completo de código do Windows Forms usando o Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Consulte também  
 [Entrada do mouse em um Aplicativo do Windows Forms](../../../docs/framework/winforms/mouse-input-in-a-windows-forms-application.md)
