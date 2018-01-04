---
title: "Instruções passo a passo: implementando o modo virtual no controle DataGridView dos Windows Forms"
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
- cpp
helpviewer_keywords:
- data [Windows Forms], managing large data sets
- DataGridView control [Windows Forms], virtual mode
- virtual mode [Windows Forms], walkthroughs
- DataGridView control [Windows Forms], large data sets
- walkthroughs [Windows Forms], DataGridView control
ms.assetid: 74eb5276-5ab8-4ce0-8005-dae751d85f7c
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3b9a70aaf2643811354cc9d7f6b51ed0805ca916
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-implementing-virtual-mode-in-the-windows-forms-datagridview-control"></a>Instruções passo a passo: implementando o modo virtual no controle DataGridView dos Windows Forms
Quando você deseja exibir grandes quantidades de dados tabulares em uma <xref:System.Windows.Forms.DataGridView> controle, você pode definir o <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> propriedade `true` e gerenciar explicitamente a interação do controle com seu repositório de dados. Isso permite ajustar o desempenho do controle nessa situação.  
  
 O <xref:System.Windows.Forms.DataGridView> controle fornece vários eventos que você pode manipular para interagir com um armazenamento de dados personalizado. Este passo a passo orienta você ao longo do processo de implementar esses manipuladores de eventos. O exemplo de código neste tópico usa uma fonte de dados muito simples para fins de ilustração. Em um ambiente de produção, você normalmente carrega apenas as linhas que você precisa exibir em um cache e manipular <xref:System.Windows.Forms.DataGridView> eventos para interagir com e atualizar o cache. Para obter mais informações, consulte [Implementando o modo virtual com carregamento de dados Just-In-Time no controle DataGridView dos Windows Forms](../../../../docs/framework/winforms/controls/implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)  
  
 Para copiar o código deste tópico como uma única lista, consulte [Como implementar o modo virtual no controle DataGridView dos Windows Forms](../../../../docs/framework/winforms/controls/how-to-implement-virtual-mode-in-the-windows-forms-datagridview-control.md).  
  
## <a name="creating-the-form"></a>Criando o formulário  
  
#### <a name="to-implement-virtual-mode"></a>Para implementar o modo virtual  
  
1.  Criar uma classe que deriva de <xref:System.Windows.Forms.Form> e contém um <xref:System.Windows.Forms.DataGridView> controle.  
  
     O código a seguir contém uma inicialização básica. Ele declara algumas variáveis que serão usadas em etapas posteriores, fornece um método `Main` e fornece um layout de formulário simples no construtor da classe.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#001](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#001)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#001](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#001)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#001](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#001)]  
    [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#002](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#002)]
    [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#002](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#002)]
    [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#002](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#002)]  
  
2.  Implementar um manipulador para o seu formulário <xref:System.Windows.Forms.Form.Load> evento que inicializa o <xref:System.Windows.Forms.DataGridView> controlar e preenche o armazenamento de dados com valores de exemplo.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#110](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#110)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#110](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#110)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#110](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#110)]  
  
3.  Implementar um manipulador para o <xref:System.Windows.Forms.DataGridView.CellValueNeeded> evento que recupera o valor da célula solicitada do armazenamento de dados ou o `Customer` objeto atualmente na edição.  
  
     Esse evento ocorre sempre que o <xref:System.Windows.Forms.DataGridView> controle precisa pintar uma célula.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#120](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#120)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#120](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#120)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#120](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#120)]  
  
4.  Implementar um manipulador para o <xref:System.Windows.Forms.DataGridView.CellValuePushed> eventos que armazena um valor de célula editado no `Customer` objeto que representa a linha editada. Esse evento ocorre sempre que o usuário confirma uma alteração de valor da célula.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#130](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#130)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#130](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#130)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#130](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#130)]  
  
5.  Implementar um manipulador para o <xref:System.Windows.Forms.DataGridView.NewRowNeeded> que cria um novo evento `Customer` objeto que representa uma linha criada recentemente.  
  
     Esse evento ocorre sempre que o usuário insere a linha de novos registros.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#140](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#140)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#140](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#140)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#140](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#140)]  
  
6.  Implementar um manipulador para o <xref:System.Windows.Forms.DataGridView.RowValidated> evento que salva linhas novas ou modificadas para o repositório de dados.  
  
     Esse evento ocorre sempre que o usuário altera a linha atual.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#150](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#150)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#150](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#150)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#150](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#150)]  
  
7.  Implementar um manipulador para o <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded> evento que indica se o <xref:System.Windows.Forms.DataGridView.CancelRowEdit> evento ocorrerá quando o usuário sinaliza reverter linha pressionando ESC duas vezes no modo de edição ou uma vez fora do modo de edição.  
  
     Por padrão, <xref:System.Windows.Forms.DataGridView.CancelRowEdit> ocorre após a reversão de linha quando as células na linha atual foram modificadas, a menos que o <xref:System.Windows.Forms.QuestionEventArgs.Response%2A?displayProperty=nameWithType> está definida como `true` no <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded> manipulador de eventos. Esse evento é útil quando o escopo da confirmação é determinado em tempo de execução.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#160](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#160)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#160](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#160)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#160](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#160)]  
  
8.  Implementar um manipulador para o <xref:System.Windows.Forms.DataGridView.CancelRowEdit> eventos que descarta os valores a `Customer` objeto que representa a linha atual.  
  
     Esse evento ocorre quando o usuário sinaliza a reversão da linha pressionando ESC duas vezes no modo de edição ou uma vez fora do modo de edição. Esse evento não ocorre se nenhuma célula na linha atual ter sido modificada ou se o valor da <xref:System.Windows.Forms.QuestionEventArgs.Response%2A?displayProperty=nameWithType> propriedade foi definida `false` em um <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded> manipulador de eventos.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#170](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#170)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#170](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#170)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#170](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#170)]  
  
9. Implementar um manipulador para o <xref:System.Windows.Forms.DataGridView.UserDeletingRow> evento que exclui uma existente `Customer` objeto do armazenamento de dados ou descarta um não salvas `Customer` objeto que representa uma linha criada recentemente.  
  
     Esse evento ocorre sempre que o usuário exclui uma linha clicando em um cabeçalho de linha e pressionando a tecla DELETE.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#180](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#180)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#180](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#180)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#180](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#180)]  
  
10. Implemente uma classe `Customers` simples para representar os itens de dados usados por este exemplo de código.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#200](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#200)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#200](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#200)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#200](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#200)]  
  
## <a name="testing-the-application"></a>Testando o aplicativo  
 Agora, é possível testar o formulário para garantir que ele se comporta da forma esperada.  
  
#### <a name="to-test-the-form"></a>Para testar o formulário  
  
-   Compile e execute o aplicativo.  
  
     Você verá um <xref:System.Windows.Forms.DataGridView> preenchido com três registros de cliente de controle. É possível modificar os valores de várias células em uma linha e pressionar ESC duas vezes no modo de edição e uma vez fora do modo de edição para reverter a linha inteira para seus valores originais. Quando você modifica, adiciona ou exclui linhas no controle, objetos `Customer` no armazenamento de dados também são modificados, adicionados ou excluídos.  
  
## <a name="next-steps"></a>Próximas etapas  
 Este aplicativo oferece uma compreensão básica dos eventos que você deve tratar para implementar o modo virtual no <xref:System.Windows.Forms.DataGridView> controle. É possível aprimorar esse aplicativo básico de várias maneiras:  
  
-   Implemente um armazenamento de dados que armazena em cache os valores de um banco de dados externo. O cache deve recuperar e descartar valores conforme necessário, de modo que ele contenha apenas o que é necessário para exibição enquanto consome uma quantidade pequena de memória no computador cliente.  
  
-   Ajuste o desempenho do armazenamento de dados dependendo de seus requisitos. Por exemplo, talvez você queira compensar conexões de rede lentas em vez de limitações de memória do computador cliente usando um tamanho de cache maior e minimizando o número de consultas ao banco de dados.  
  
 Para obter mais informações armazenar em cache valores de um banco de dados externo, consulte [Como implementar o modo virtual com carregamento de dados Just-In-Time no controle DataGridView dos Windows Forms](../../../../docs/framework/winforms/controls/virtual-mode-with-just-in-time-data-loading-in-the-datagrid.md).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>  
 <xref:System.Windows.Forms.DataGridView.CellValueNeeded>  
 <xref:System.Windows.Forms.DataGridView.CellValuePushed>  
 <xref:System.Windows.Forms.DataGridView.NewRowNeeded>  
 <xref:System.Windows.Forms.DataGridView.RowValidated>  
 <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded>  
 <xref:System.Windows.Forms.DataGridView.CancelRowEdit>  
 <xref:System.Windows.Forms.DataGridView.UserDeletingRow>  
 [Ajuste de desempenho no controle DataGridView do Windows Forms](../../../../docs/framework/winforms/controls/performance-tuning-in-the-windows-forms-datagridview-control.md)  
 [Práticas recomendadas para colocação em escala do controle DataGridView dos Windows Forms](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md)  
 [Implementando o modo virtual com carregamento de dados Just-In-Time no controle DataGridView dos Windows Forms](../../../../docs/framework/winforms/controls/implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)  
 [Como implementar o modo virtual no controle DataGridView dos Windows Forms](../../../../docs/framework/winforms/controls/how-to-implement-virtual-mode-in-the-windows-forms-datagridview-control.md)
