---
title: Atalhos de teclado para o controle DataGrid dos Windows Forms
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- keyboard shortcuts [Windows Forms], DataGrid control
- DataGrid control [Windows Forms], navigation keys
ms.assetid: a01780f9-20d5-4f5f-808f-c790c9a007a5
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3e80281f3a89737f060804aa5237705386232763
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="keyboard-shortcuts-for-the-windows-forms-datagrid-control"></a>Atalhos de teclado para o controle DataGrid dos Windows Forms
> [!NOTE]
>  O controle <xref:System.Windows.Forms.DataGridView> substitui e adiciona funcionalidade ao controle <xref:System.Windows.Forms.DataGrid>, no entanto, o controle <xref:System.Windows.Forms.DataGrid> é mantido para compatibilidade com versões anteriores e para uso futuro, se desejado. Para obter mais informações, consulte [Diferenças Entre o Windows Forms DataGridView e os Controles do DataGrid](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 A tabela a seguir lista os atalhos de teclado que podem ser usados para a navegação em Windows Forms <xref:System.Windows.Forms.DataGrid> controle:  
  
|Ação|Atalho|  
|------------|--------------|  
|Concluir uma entrada de célula e avance para a próxima célula abaixo.<br /><br /> Se o foco estiver em um link da tabela filho, navegue para essa tabela.|ENTER|  
|Cancelar a edição de célula se estiver no modo de edição de célula.<br /><br /> Se estiver na seleção de letreiro, cancele a edição na linha.|ESC|  
|Excluir o caractere antes do ponto de inserção ao editar uma célula.|BACKSPACE|  
|Excluir o caractere após o ponto de inserção ao editar uma célula.|DELETE|  
|Ir para a primeira célula na linha atual.|HOME|  
|Ir para a última célula na linha atual.|END|  
|Realçar caracteres na célula atual e posicionar o ponto de inserção no final da linha. Mesmo comportamento que clicar duas vezes em uma célula.|F2|  
|Se o foco estiver em uma célula, vá para a próxima célula na linha.<br /><br /> Se o foco estiver na última célula em uma linha, vá para o primeiro link da tabela filho da linha e expanda-o.<br /><br /> Se o foco estiver em um link filho, vá para o próximo link filho.<br /><br /> Se o foco estiver no último link filho, vá para a primeira célula da linha seguinte.|TAB|  
|Se o foco estiver em uma célula, vá para a célula anterior na linha.<br /><br /> Se o foco estiver na primeira célula em uma linha, vá para o último link da tabela filho expandida da linha anterior ou vá para a última célula da linha anterior.<br /><br /> Se o foco estiver em um link filho, vá para o link filho anterior.<br /><br /> Se o foco estiver no primeiro link filho, vá para a última célula da linha anterior.|SHIFT+TAB|  
|Ir para o próximo controle na ordem de tabulação.|CTRL+TAB|  
|Ir para o controle anterior na ordem de tabulação.|CTRL+SHIFT+TAB|  
|Subir para a tabela pai se estiver em uma tabela filho. Mesmo comportamento que clicar no botão Voltar.|ALT+SETA PARA A ESQUERDA|  
|Expandir links da tabela filho. ALT+SETA PARA BAIXO expande todos os links, não apenas os selecionados.|ALT+SETA PARA BAIXO ou CTRL+SINAL DE ADIÇÃO|  
|Recolher links da tabela filho. ALT+SETA PARA CIMA recolhe todos os links, não apenas aqueles selecionados.|ALT+SETA PARA CIMA ou CTRL+SINAL DE SUBTRAÇÃO|  
|Ir para a célula não vazia mais distante na direção da seta.|CTRL+SETA|  
|Estender a seleção uma linha na direção da seta (exceto links da tabela filho).|SHIFT+SETA PARA CIMA/SETA PARA BAIXO|  
|Estender a seleção para a linha mais não vazia mais distante na direção da seta (exceto links da tabela filho).|CTRL+SHIFT+ SETA PARA CIMA/PARA BAIXO|  
|Mover para a célula superior esquerda.|CTRL+HOME|  
|Mover para a célula inferior direita.|CTRL+END|  
|Estender a seleção para a linha superior.|CTRL+SHIFT+HOME|  
|Estender a seleção para a linha inferior.|CTRL+SHIFT+END|  
|Selecionar a linha atual (exceto por links da tabela filho).|SHIFT+BARRA DE ESPAÇOS|  
|Selecionar toda a grade (exceto por links da tabela filho).|CTRL+A|  
|Exibir a linha pai quando estiver em uma tabela filho.|CTRL+PAGE DOWN|  
|Ocultar a linha pai quando estiver em uma tabela filho.|CTRL+PAGE UP|  
|Estender a seleção para baixo uma tela (exceto por links da tabela filho).|SHIFT + PAGE DOWN|  
|Estender a seleção para cima uma tela (exceto por links da tabela filho).|SHIFT+PAGE UP|  
|Chamar o <xref:System.Windows.Forms.DataGrid.EndEdit%2A> método para a linha atual.|CTRL+ENTER|  
|Insira um <xref:System.DBNull.Value?displayProperty=nameWithType> valor em uma célula em modo de edição.|CTRL+0|  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral do controle DataGrid](../../../../docs/framework/winforms/controls/datagrid-control-overview-windows-forms.md)  
 [Controle DataGrid](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)
