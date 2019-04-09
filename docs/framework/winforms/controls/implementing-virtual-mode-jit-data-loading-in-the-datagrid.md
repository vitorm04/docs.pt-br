---
title: Implementando o modo virtual com carregamento de dados Just-In-Time no controle DataGridView dos Windows Forms
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- examples [Windows Forms], just-in-time data loading
- data [Windows Forms], managing large data sets
- DataGridView control [Windows Forms], virtual mode
- just-in-time data loading
- DataGridView control [Windows Forms], large data sets
- virtual mode [Windows Forms], just-in-time data loading
ms.assetid: c2a052b9-423c-4ff7-91dc-d8c7c79345f6
ms.openlocfilehash: 641db19cc6493a20c9f9a34622f466e3623c32ad
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59088646"
---
# <a name="implementing-virtual-mode-with-just-in-time-data-loading-in-the-windows-forms-datagridview-control"></a>Implementando o modo virtual com carregamento de dados Just-In-Time no controle DataGridView dos Windows Forms
Um motivo para implementar o modo virtual no <xref:System.Windows.Forms.DataGridView> controle é recuperar dados somente conforme necessário. Isso é chamado de *carregamento de dados Just-In-Time*.  
  
 Se estiver trabalhando com uma tabela muito grande em um banco de dados remoto, por exemplo, talvez você queira evitar atrasos de inicialização recuperando somente os dados necessários para exibição e recuperando dados adicionais somente quando o usuário rolar novas linhas para a área de exibição. Se os computadores cliente que estão executando seu aplicativo tiverem uma quantidade limitada de memória disponível para armazenar dados, você também pode querer descartar dados não utilizados quando recuperar novos valores do banco de dados.  
  
 As seções a seguir descrevem como usar um <xref:System.Windows.Forms.DataGridView> controle com um cache just-in-time.  
  
 Para copiar o código deste tópico como uma única listagem, confira [Como: Implementar o modo Virtual com carregamento de dados Just-In-Time para o Windows Forms DataGridView Control](virtual-mode-with-just-in-time-data-loading-in-the-datagrid.md).  
  
## <a name="the-form"></a>O formulário  
 O exemplo de código a seguir define um formulário que contenha somente leitura <xref:System.Windows.Forms.DataGridView> controle interage com um `Cache` do objeto por meio de um <xref:System.Windows.Forms.DataGridView.CellValueNeeded> manipulador de eventos. O objeto `Cache` gerencia os valores armazenados localmente e usa um objeto `DataRetriever` para recuperar valores da tabela Orders do banco de dados de exemplo Northwind. O `DataRetriever` objeto, que implementa o `IDataPageRetriever` interface requerida pela `Cache` da classe, também é usado para inicializar o <xref:System.Windows.Forms.DataGridView> controlar as linhas e colunas.  
  
 Os tipos `IDataPageRetriever`, `DataRetriever` e `Cache` são descritos mais adiante neste tópico.  
  
> [!NOTE]
>  O armazenamento das informações confidenciais (tal como uma senha) dentro da cadeia de conexão pode afetar a segurança do aplicativo. O uso da Autenticação do Windows (também conhecida como segurança integrada) é uma maneira mais segura de controlar o acesso a um banco de dados. Para obter mais informações, consulte [Protegendo informações de conexão](../../data/adonet/protecting-connection-information.md).  
  
 [!code-csharp[System.Windows.Forms.DataGridView.Virtual_lazyloading#100](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/CS/lazyloading.cs#100)]
 [!code-vb[System.Windows.Forms.DataGridView.Virtual_lazyloading#100](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/VB/lazyloading.vb#100)]  
  
## <a name="the-idatapageretriever-interface"></a>A Interface IDataPageRetriever  
 O exemplo de código a seguir define a interface `IDataPageRetriever`, que é implementada pela classe `DataRetriever`. O único método declarado nessa interface é o método `SupplyPageOfData`, que requer um índice de linhas inicial e uma contagem do número de linhas em uma única página de dados. Esses valores são usados pelo implementador para recuperar um subconjunto de dados de uma fonte de dados.  
  
 Um objeto `Cache` usa uma implementação dessa interface durante a construção para carregar duas páginas iniciais de dados. Sempre que um valor fora do cache é necessário, o cache descarta uma dessas páginas e solicita uma nova página que contém o valor do `IDataPageRetriever`.  
  
 [!code-csharp[System.Windows.Forms.DataGridView.Virtual_lazyloading#201](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/CS/lazyloading.cs#201)]
 [!code-vb[System.Windows.Forms.DataGridView.Virtual_lazyloading#201](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/VB/lazyloading.vb#201)]  
  
## <a name="the-dataretriever-class"></a>A classe DataRetriever  
 O exemplo de código a seguir define a classe `DataRetriever`, que implementa a interface `IDataPageRetriever` para recuperar páginas de dados de um servidor. O `DataRetriever` classe também fornece `Columns` e `RowCount` propriedades, que o <xref:System.Windows.Forms.DataGridView> controle usa para criar as colunas necessárias e para adicionar o número apropriado de linhas vazias para o <xref:System.Windows.Forms.DataGridView.Rows%2A> coleção. Adicionar as linhas vazias é necessário para que o controle se comporte como se contivesse todos os dados na tabela. Isso significa que a caixa de rolagem na barra de rolagem terá o tamanho apropriado e o usuário será capaz de acessar qualquer linha na tabela. As linhas são preenchidas pelo <xref:System.Windows.Forms.DataGridView.CellValueNeeded> manipulador de eventos somente quando eles são colocados na exibição.  
  
 [!code-csharp[System.Windows.Forms.DataGridView.Virtual_lazyloading#200](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/CS/lazyloading.cs#200)]
 [!code-vb[System.Windows.Forms.DataGridView.Virtual_lazyloading#200](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/VB/lazyloading.vb#200)]  
  
## <a name="the-cache-class"></a>A classe Cache  
 O exemplo de código a seguir define a classe `Cache`, que gerencia duas páginas de dados preenchidas por meio de uma implementação de `IDataPageRetriever`. O `Cache` classe define interna `DataPage` estrutura, que contém um <xref:System.Data.DataTable> para armazenar os valores em um cache de único página e que calcula a linha de índices que representam os limites superiores e inferiores da página.  
  
 A classe `Cache` carrega duas páginas de dados no momento da construção. Sempre que o <xref:System.Windows.Forms.DataGridView.CellValueNeeded> evento solicita um valor, o `Cache` objeto determina se o valor está disponível em uma de suas duas páginas e, nesse caso, retorna-a. Se o valor não estiver disponível localmente, o objeto `Cache` determinará qual das duas páginas está mais distante das linhas exibidas atualmente e substituirá a página por uma nova, que contém o valor solicitado que, então, é retornado.  
  
 Supondo que o número de linhas em uma página de dados seja igual ao número de linhas que podem ser exibidas na tela de uma só vez, esse modelo permite que os usuários que estão percorrendo a tabela por paginação retornem para a página exibida mais recentemente.  
  
 [!code-csharp[System.Windows.Forms.DataGridView.Virtual_lazyloading#300](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/CS/lazyloading.cs#300)]
 [!code-vb[System.Windows.Forms.DataGridView.Virtual_lazyloading#300](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/VB/lazyloading.vb#300)]  
  
## <a name="additional-considerations"></a>Considerações adicionais  
 Os exemplos de código anteriores são fornecidos como uma demonstração de carregamento de dados Just-In-Time. Você precisará modificar o código de acordo com suas necessidades alcançar a máxima eficiência. No mínimo, você precisará escolher um valor apropriado para o número de linhas por página de dados no cache. Esse valor é passado para o construtor `Cache`. O número de linhas por página deve ser não menos do que o número de linhas que podem ser exibidos simultaneamente no seu <xref:System.Windows.Forms.DataGridView> controle.  
  
 Para obter melhores resultados, você precisará realizar testes de desempenho e testes de usabilidade para determinar os requisitos do sistema e de seus usuários. Os diversos fatores que você precisará levar em consideração incluem a quantidade de memória nas máquinas cliente que executam seu aplicativo, a largura de banda disponível da conexão de rede usada e a latência do servidor usado. A largura de banda e a latência devem ser determinadas em momentos de pico.  
  
 Para melhorar o desempenho de rolagem do seu aplicativo, você pode aumentar a quantidade de dados armazenados localmente. Para melhorar o tempo de inicialização, no entanto, você deve evitar o carregamento de muitos dados inicialmente. Talvez você queira modificar a classe `Cache` para aumentar o número de páginas de dados que ela pode armazenar. Usar mais páginas de dados pode melhorar a eficiência de rolagem, mas você precisará determinar o número ideal de linhas em uma página de dados, dependendo da largura de banda disponível e da latência do servidor. Com páginas menores, o servidor será acessado com mais frequência, mas levará menos tempo para retornar os dados solicitados. Se a latência for mais importante que a largura de banda, talvez você queira usar páginas de dados maiores.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>
- [Ajuste de desempenho no controle DataGridView dos Windows Forms](performance-tuning-in-the-windows-forms-datagridview-control.md)
- [Práticas recomendadas para dimensionamento do controle DataGridView dos Windows Forms](best-practices-for-scaling-the-windows-forms-datagridview-control.md)
- [Modo virtual no controle DataGridView dos Windows Forms](virtual-mode-in-the-windows-forms-datagridview-control.md)
- [Passo a passo: Implementando o modo virtual no controle DataGridView do Windows Forms](implementing-virtual-mode-wf-datagridview-control.md)
- [Como: Implementar o modo virtual com carregamento de dados Just-In-Time no controle DataGridView do Windows Forms](virtual-mode-with-just-in-time-data-loading-in-the-datagrid.md)
