---
title: 'Walkthrough: implementar o modo virtual no controle DataGridView'
ms.date: 03/30/2017
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
ms.openlocfilehash: 5db97b321238bc371c94e627a387bd83ca31b58a
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746522"
---
# <a name="walkthrough-implementing-virtual-mode-in-the-windows-forms-datagridview-control"></a>Instruções passo a passo: implementando o modo virtual no controle DataGridView dos Windows Forms
Quando você quiser exibir quantidades muito grandes de dados tabulares em um controle de <xref:System.Windows.Forms.DataGridView>, poderá definir a propriedade <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> como `true` e gerenciar explicitamente a interação do controle com seu armazenamento de dados. Isso permite ajustar o desempenho do controle nessa situação.  
  
 O controle de <xref:System.Windows.Forms.DataGridView> fornece vários eventos que você pode manipular para interagir com um repositório de dados personalizado. Este passo a passo orienta você ao longo do processo de implementar esses manipuladores de eventos. O exemplo de código neste tópico usa uma fonte de dados muito simples para fins de ilustração. Em uma configuração de produção, você normalmente carregará apenas as linhas que precisa exibir em um cache e manipulará <xref:System.Windows.Forms.DataGridView> eventos para interagir com o cache e atualizá-lo. Para obter mais informações, consulte [Implementando o modo virtual com carregamento de dados Just-In-Time no controle DataGridView dos Windows Forms](implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)  
  
 Para copiar o código deste tópico como uma única lista, consulte [Como implementar o modo virtual no controle DataGridView dos Windows Forms](how-to-implement-virtual-mode-in-the-windows-forms-datagridview-control.md).  
  
## <a name="creating-the-form"></a>Criando o formulário  
  
#### <a name="to-implement-virtual-mode"></a>Para implementar o modo virtual  
  
1. Crie uma classe que derive de <xref:System.Windows.Forms.Form> e contenha um controle de <xref:System.Windows.Forms.DataGridView>.  
  
     O código a seguir contém uma inicialização básica. Ele declara algumas variáveis que serão usadas em etapas posteriores, fornece um método `Main` e fornece um layout de formulário simples no construtor da classe.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#001](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#001)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#001](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#001)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#001](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#001)]  
    [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#002](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#002)]
    [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#002](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#002)]
    [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#002](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#002)]  
  
2. Implemente um manipulador para o evento de <xref:System.Windows.Forms.Form.Load> do seu formulário que inicializa o controle de <xref:System.Windows.Forms.DataGridView> e popula o armazenamento de dados com valores de exemplo.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#110](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#110)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#110](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#110)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#110](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#110)]  
  
3. Implemente um manipulador para o evento <xref:System.Windows.Forms.DataGridView.CellValueNeeded> que recupera o valor de célula solicitado do armazenamento de dados ou o objeto `Customer` no momento em Editar.  
  
     Esse evento ocorre sempre que o controle de <xref:System.Windows.Forms.DataGridView> precisa pintar uma célula.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#120](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#120)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#120](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#120)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#120](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#120)]  
  
4. Implemente um manipulador para o evento <xref:System.Windows.Forms.DataGridView.CellValuePushed> que armazena um valor de célula editado no objeto `Customer` que representa a linha editada. Esse evento ocorre sempre que o usuário confirma uma alteração de valor da célula.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#130](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#130)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#130](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#130)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#130](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#130)]  
  
5. Implemente um manipulador para o evento <xref:System.Windows.Forms.DataGridView.NewRowNeeded> que cria um novo objeto `Customer` que representa uma linha recém-criada.  
  
     Esse evento ocorre sempre que o usuário insere a linha de novos registros.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#140](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#140)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#140](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#140)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#140](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#140)]  
  
6. Implemente um manipulador para o evento <xref:System.Windows.Forms.DataGridView.RowValidated> que salva linhas novas ou modificadas no repositório de dados.  
  
     Esse evento ocorre sempre que o usuário altera a linha atual.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#150](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#150)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#150](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#150)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#150](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#150)]  
  
7. Implemente um manipulador para o evento <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded> que indica se o evento de <xref:System.Windows.Forms.DataGridView.CancelRowEdit> ocorrerá quando o usuário sinalizar a reversão de linha pressionando ESC duas vezes no modo de edição ou uma vez fora do modo de edição.  
  
     Por padrão, <xref:System.Windows.Forms.DataGridView.CancelRowEdit> ocorrerá na reversão da linha quando as células na linha atual tiverem sido modificadas, a menos que a propriedade <xref:System.Windows.Forms.QuestionEventArgs.Response%2A?displayProperty=nameWithType> esteja definida como `true` no manipulador de eventos <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded>. Esse evento é útil quando o escopo da confirmação é determinado em tempo de execução.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#160](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#160)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#160](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#160)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#160](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#160)]  
  
8. Implemente um manipulador para o evento <xref:System.Windows.Forms.DataGridView.CancelRowEdit> que descarta os valores do objeto `Customer` que representa a linha atual.  
  
     Esse evento ocorre quando o usuário sinaliza a reversão da linha pressionando ESC duas vezes no modo de edição ou uma vez fora do modo de edição. Esse evento não ocorrerá se nenhuma célula na linha atual tiver sido modificada ou se o valor da propriedade <xref:System.Windows.Forms.QuestionEventArgs.Response%2A?displayProperty=nameWithType> tiver sido definido como `false` em um manipulador de eventos <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded>.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#170](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#170)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#170](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#170)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#170](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#170)]  
  
9. Implemente um manipulador para o evento <xref:System.Windows.Forms.DataGridView.UserDeletingRow> que exclui um objeto `Customer` existente do armazenamento de dados ou descarta um objeto `Customer` não salvo que representa uma linha recém-criada.  
  
     Esse evento ocorre sempre que o usuário exclui uma linha clicando em um cabeçalho de linha e pressionando a tecla DELETE.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#180](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#180)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#180](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#180)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#180](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#180)]  
  
10. Implemente uma classe `Customers` simples para representar os itens de dados usados por este exemplo de código.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#200](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#200)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#200](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#200)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#200](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#200)]  
  
## <a name="testing-the-application"></a>Testando o aplicativo  
 Agora, é possível testar o formulário para garantir que ele se comporta da forma esperada.  
  
#### <a name="to-test-the-form"></a>Para testar o formulário  
  
- Compile e execute o aplicativo.  
  
     Você verá um controle de <xref:System.Windows.Forms.DataGridView> populado com três registros de cliente. É possível modificar os valores de várias células em uma linha e pressionar ESC duas vezes no modo de edição e uma vez fora do modo de edição para reverter a linha inteira para seus valores originais. Quando você modifica, adiciona ou exclui linhas no controle, objetos `Customer` no armazenamento de dados também são modificados, adicionados ou excluídos.  
  
## <a name="next-steps"></a>Próximas etapas  
 Esse aplicativo fornece uma compreensão básica dos eventos que você deve manipular para implementar o modo virtual no controle de <xref:System.Windows.Forms.DataGridView>. É possível aprimorar esse aplicativo básico de várias maneiras:  
  
- Implemente um armazenamento de dados que armazena em cache os valores de um banco de dados externo. O cache deve recuperar e descartar valores conforme necessário, de modo que ele contenha apenas o que é necessário para exibição enquanto consome uma quantidade pequena de memória no computador cliente.  
  
- Ajuste o desempenho do armazenamento de dados dependendo de seus requisitos. Por exemplo, talvez você queira compensar conexões de rede lentas em vez de limitações de memória do computador cliente usando um tamanho de cache maior e minimizando o número de consultas ao banco de dados.  
  
 Para obter mais informações armazenar em cache valores de um banco de dados externo, consulte [Como implementar o modo virtual com carregamento de dados Just-In-Time no controle DataGridView dos Windows Forms](virtual-mode-with-just-in-time-data-loading-in-the-datagrid.md).  
  
## <a name="see-also"></a>Veja também

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>
- <xref:System.Windows.Forms.DataGridView.CellValueNeeded>
- <xref:System.Windows.Forms.DataGridView.CellValuePushed>
- <xref:System.Windows.Forms.DataGridView.NewRowNeeded>
- <xref:System.Windows.Forms.DataGridView.RowValidated>
- <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded>
- <xref:System.Windows.Forms.DataGridView.CancelRowEdit>
- <xref:System.Windows.Forms.DataGridView.UserDeletingRow>
- [Ajuste de desempenho no controle DataGridView dos Windows Forms](performance-tuning-in-the-windows-forms-datagridview-control.md)
- [Práticas recomendadas para colocação em escala do controle DataGridView dos Windows Forms](best-practices-for-scaling-the-windows-forms-datagridview-control.md)
- [Implementando o modo virtual com carregamento de dados Just-In-Time no controle DataGridView dos Windows Forms](implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)
- [Como implementar o modo virtual no controle DataGridView dos Windows Forms](how-to-implement-virtual-mode-in-the-windows-forms-datagridview-control.md)
