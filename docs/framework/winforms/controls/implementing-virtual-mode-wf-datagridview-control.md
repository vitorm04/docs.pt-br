---
title: 'Passo a passo: Implementando o modo virtual no controle DataGridView do Windows Forms'
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
ms.openlocfilehash: 9e7fb3a42b56c40f713d73e3734142f4aab335f4
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64649989"
---
# <a name="walkthrough-implementing-virtual-mode-in-the-windows-forms-datagridview-control"></a>Passo a passo: Implementando o modo virtual no controle DataGridView do Windows Forms
Quando quiser exibir grandes quantidades de dados tabulares em uma <xref:System.Windows.Forms.DataGridView> controle, você pode definir o <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> propriedade `true` e gerenciar explicitamente a interação do controle com seu armazenamento de dados. Isso permite ajustar o desempenho do controle nessa situação.  
  
 O <xref:System.Windows.Forms.DataGridView> controle fornece vários eventos que você pode manipular para interagir com um armazenamento de dados personalizado. Este passo a passo orienta você ao longo do processo de implementar esses manipuladores de eventos. O exemplo de código neste tópico usa uma fonte de dados muito simples para fins de ilustração. Em um ambiente de produção, você normalmente carrega apenas as linhas que precisa exibir para um cache e manipular <xref:System.Windows.Forms.DataGridView> eventos para interagir com e atualizar o cache. Para obter mais informações, consulte [Implementando o modo virtual com carregamento de dados Just-In-Time no controle DataGridView dos Windows Forms](implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)  
  
 Para copiar o código deste tópico como uma única listagem, confira [Como: Implementar o modo Virtual no Windows Forms DataGridView Control](how-to-implement-virtual-mode-in-the-windows-forms-datagridview-control.md).  
  
## <a name="creating-the-form"></a>Criando o formulário  
  
#### <a name="to-implement-virtual-mode"></a>Para implementar o modo virtual  
  
1. Criar uma classe que deriva de <xref:System.Windows.Forms.Form> e contém um <xref:System.Windows.Forms.DataGridView> controle.  
  
     O código a seguir contém uma inicialização básica. Ele declara algumas variáveis que serão usadas em etapas posteriores, fornece um método `Main` e fornece um layout de formulário simples no construtor da classe.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#001](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#001)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#001](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#001)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#001](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#001)]  
    [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#002](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#002)]
    [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#002](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#002)]
    [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#002](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#002)]  
  
2. Implemente um manipulador para seu formulário <xref:System.Windows.Forms.Form.Load> evento que inicializa o <xref:System.Windows.Forms.DataGridView> controlar e preenche o armazenamento de dados com valores de exemplo.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#110](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#110)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#110](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#110)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#110](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#110)]  
  
3. Implemente um manipulador para o <xref:System.Windows.Forms.DataGridView.CellValueNeeded> eventos que recupera o valor da célula solicitada do armazenamento de dados ou o `Customer` objeto em edição no momento.  
  
     Esse evento ocorre sempre que o <xref:System.Windows.Forms.DataGridView> controle precisa pintar uma célula.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#120](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#120)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#120](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#120)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#120](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#120)]  
  
4. Implemente um manipulador para o <xref:System.Windows.Forms.DataGridView.CellValuePushed> evento que armazena um valor de célula editada no `Customer` objeto que representa a linha editada. Esse evento ocorre sempre que o usuário confirma uma alteração de valor da célula.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#130](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#130)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#130](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#130)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#130](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#130)]  
  
5. Implemente um manipulador para o <xref:System.Windows.Forms.DataGridView.NewRowNeeded> que cria um novo evento `Customer` objeto que representa uma linha recém-criada.  
  
     Esse evento ocorre sempre que o usuário insere a linha de novos registros.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#140](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#140)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#140](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#140)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#140](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#140)]  
  
6. Implemente um manipulador para o <xref:System.Windows.Forms.DataGridView.RowValidated> evento que salva linhas novas ou modificadas no armazenamento de dados.  
  
     Esse evento ocorre sempre que o usuário altera a linha atual.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#150](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#150)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#150](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#150)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#150](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#150)]  
  
7. Implemente um manipulador para o <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded> evento que indica se o <xref:System.Windows.Forms.DataGridView.CancelRowEdit> evento ocorrerá quando o usuário sinaliza a reversão da linha pressionando ESC duas vezes no modo de edição ou uma vez fora do modo de edição.  
  
     Por padrão, <xref:System.Windows.Forms.DataGridView.CancelRowEdit> ocorre após a reversão da linha quando qualquer célula na linha atual foram modificada, a menos que o <xref:System.Windows.Forms.QuestionEventArgs.Response%2A?displayProperty=nameWithType> estiver definida como `true` no <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded> manipulador de eventos. Esse evento é útil quando o escopo da confirmação é determinado em tempo de execução.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#160](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#160)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#160](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#160)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#160](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#160)]  
  
8. Implemente um manipulador para o <xref:System.Windows.Forms.DataGridView.CancelRowEdit> evento que descarta os valores do `Customer` objeto que representa a linha atual.  
  
     Esse evento ocorre quando o usuário sinaliza a reversão da linha pressionando ESC duas vezes no modo de edição ou uma vez fora do modo de edição. Esse evento não ocorre se nenhuma célula na linha atual foram modificada ou se o valor da <xref:System.Windows.Forms.QuestionEventArgs.Response%2A?displayProperty=nameWithType> propriedade foi definida como `false` em um <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded> manipulador de eventos.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#170](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#170)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#170](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#170)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#170](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#170)]  
  
9. Implemente um manipulador para o <xref:System.Windows.Forms.DataGridView.UserDeletingRow> evento que exclui uma existente `Customer` objeto do armazenamento de dados ou descarta um não salvas `Customer` objeto que representa uma linha recém-criada.  
  
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
  
     Você verá um <xref:System.Windows.Forms.DataGridView> preenchido com três registros de cliente do controle. É possível modificar os valores de várias células em uma linha e pressionar ESC duas vezes no modo de edição e uma vez fora do modo de edição para reverter a linha inteira para seus valores originais. Quando você modifica, adiciona ou exclui linhas no controle, objetos `Customer` no armazenamento de dados também são modificados, adicionados ou excluídos.  
  
## <a name="next-steps"></a>Próximas etapas  
 Esse aplicativo oferece uma compreensão básica dos eventos que você precisa manipular para implementar o modo virtual no <xref:System.Windows.Forms.DataGridView> controle. É possível aprimorar esse aplicativo básico de várias maneiras:  
  
- Implemente um armazenamento de dados que armazena em cache os valores de um banco de dados externo. O cache deve recuperar e descartar valores conforme necessário, de modo que ele contenha apenas o que é necessário para exibição enquanto consome uma quantidade pequena de memória no computador cliente.  
  
- Ajuste o desempenho do armazenamento de dados dependendo de seus requisitos. Por exemplo, talvez você queira compensar conexões de rede lentas em vez de limitações de memória do computador cliente usando um tamanho de cache maior e minimizando o número de consultas ao banco de dados.  
  
 Para obter mais informações sobre o cache de valores de um banco de dados externo, consulte [como: Implementar o modo Virtual com carregamento de dados Just-In-Time para o Windows Forms DataGridView Control](virtual-mode-with-just-in-time-data-loading-in-the-datagrid.md).  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>
- <xref:System.Windows.Forms.DataGridView.CellValueNeeded>
- <xref:System.Windows.Forms.DataGridView.CellValuePushed>
- <xref:System.Windows.Forms.DataGridView.NewRowNeeded>
- <xref:System.Windows.Forms.DataGridView.RowValidated>
- <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded>
- <xref:System.Windows.Forms.DataGridView.CancelRowEdit>
- <xref:System.Windows.Forms.DataGridView.UserDeletingRow>
- [Ajuste de desempenho no controle DataGridView do Windows Forms](performance-tuning-in-the-windows-forms-datagridview-control.md)
- [Práticas recomendadas para colocação em escala do controle DataGridView dos Windows Forms](best-practices-for-scaling-the-windows-forms-datagridview-control.md)
- [Implementando o modo virtual com carregamento de dados Just-In-Time no controle DataGridView dos Windows Forms](implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)
- [Como: Implementar o modo Virtual no controle DataGridView dos Windows Forms](how-to-implement-virtual-mode-in-the-windows-forms-datagridview-control.md)
