---
title: Funcionalidade padrão no controle DataGridView
ms.date: 03/30/2017
helpviewer_keywords:
- data grids [Windows Forms], default functionality in DataGridView control
- DataGridView control [Windows Forms], default functionality
ms.assetid: 4405f697-cad1-4839-9bcd-8ddb09d9f00e
ms.openlocfilehash: b695883ac7ec3fb0c459adb66214b0eceab3a128
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746127"
---
# <a name="default-functionality-in-the-windows-forms-datagridview-control"></a>Funcionalidade padrão no controle DataGridView dos Windows Forms
O controle de <xref:System.Windows.Forms.DataGridView> de Windows Forms fornece aos usuários uma quantidade significativa de funcionalidade padrão.  
  
## <a name="default-functionality"></a>Funcionalidade padrão  
 Por padrão, um controle de <xref:System.Windows.Forms.DataGridView>:  
  
- Exibe automaticamente os cabeçalhos de coluna e de linha que permanecem visíveis enquanto a tabela rola verticalmente.  
  
- Tem um cabeçalho de linha que contém um indicador de seleção para a linha atual.  
  
- Tem um retângulo de seleção na primeira célula.  
  
- Tem colunas que podem ser redimensionadas automaticamente quando o usuário clicar duas vezes nos divisores de coluna.  
  
- Dá suporte automaticamente a estilos visuais no Windows XP e na família Windows Server 2003 quando o método <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> é chamado a partir do método `Main` do aplicativo.  
  
 Além disso, o conteúdo de um controle de <xref:System.Windows.Forms.DataGridView> pode ser editado por padrão:  
  
- Se o usuário clica duas vezes ou pressiona F2 em uma célula, o controle automaticamente coloca a célula no modo de edição e atualiza o conteúdo da célula à medida que o usuário digita.  
  
- Se o usuário rolar até o final da grade, o usuário verá que existe uma linha para adicionar novos registros. Quando o usuário clica nessa linha, uma nova linha é adicionada ao controle de <xref:System.Windows.Forms.DataGridView>, com valores padrão. Quando o usuário pressiona ESC, essa nova linha desaparece.  
  
- Se o usuário clicar em um cabeçalho de linha, a linha inteira será selecionada.  
  
 Quando você associa um controle de <xref:System.Windows.Forms.DataGridView> a uma fonte de dados definindo sua propriedade <xref:System.Windows.Forms.DataGridView.DataSource%2A>, o controle:  
  
- Usa automaticamente os nomes das colunas da fonte de dados como o texto do cabeçalho de coluna.  
  
- É populado com o conteúdo da fonte de dados. <xref:System.Windows.Forms.DataGridView> colunas são criadas automaticamente para cada coluna na fonte de dados.  
  
- Cria uma linha para cada linha visível na tabela.  
  
- Classifica automaticamente as linhas com base nos dados subjacentes quando o usuário clica em um cabeçalho de coluna.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.DataGridView>
- [Controle DataGridView](datagridview-control-windows-forms.md)
