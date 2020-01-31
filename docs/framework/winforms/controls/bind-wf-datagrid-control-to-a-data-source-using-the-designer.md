---
title: Associar controle DataGrid a uma fonte de dados usando o designer
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- datasets [Windows Forms], binding to DataGrid control
- data binding [Windows Forms], DataGrid control
- DataGrid control [Windows Forms], data binding
- Windows Forms controls, data binding
- bound controls [Windows Forms]
ms.assetid: 4e96e3d0-b1cc-4de1-8774-bc9970ec4554
ms.openlocfilehash: cc0a74eca40e34f06b065980d25d922b919b0c3c
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744093"
---
# <a name="how-to-bind-the-windows-forms-datagrid-control-to-a-data-source-using-the-designer"></a>Como associar o controle DataGrid dos Windows Forms a uma fonte de dados usando o designer

> [!NOTE]
> O controle <xref:System.Windows.Forms.DataGridView> substitui e adiciona funcionalidade ao controle <xref:System.Windows.Forms.DataGrid>, no entanto, o controle <xref:System.Windows.Forms.DataGrid> é mantido para compatibilidade com versões anteriores e para uso futuro, se desejado. Para obter mais informações, consulte [Diferenças Entre o Windows Forms DataGridView e os Controles do DataGrid](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).

 O controle de <xref:System.Windows.Forms.DataGrid> de Windows Forms é especificamente projetado para exibir informações de uma fonte de dados. Você associa o controle em tempo de design definindo as propriedades <xref:System.Windows.Forms.DataGrid.DataSource%2A> e <xref:System.Windows.Forms.DataGrid.DataMember%2A> ou em tempo de execução chamando o método <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A>. Embora seja possível exibir dados de uma variedade de fontes de dados, as fontes mais comuns são conjuntos de dados e exibições de dados.

 Se a fonte de dados estiver disponível em tempo de design – por exemplo, se o formulário contiver uma instância de um conjunto ou exibição de dados –, será possível associar a grade à fonte de dados em tempo de design. Então, será possível visualizar a aparência dos dados na grade.

 Também é possível associar a grade programaticamente, em tempo de execução. Isso é útil quando se deseja definir uma fonte de dados com base nas informações obtidas em tempo de execução. Por exemplo, o aplicativo pode permitir que o usuário especifique o nome de uma tabela para exibir. Também é necessário em situações em que a fonte de dados não existe em tempo de design. Isso inclui fontes de dados como matrizes, coleções, conjuntos de dados não tipados e leitores de dados.

 O procedimento a seguir requer um projeto de **aplicativo do Windows** com um formulário que contém um controle <xref:System.Windows.Forms.DataGrid>. Para obter informações sobre como configurar esse projeto, consulte [como: criar um projeto de aplicativo Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project) e [como adicionar controles ao Windows Forms](how-to-add-controls-to-windows-forms.md). No Visual Studio 2005, o controle <xref:System.Windows.Forms.DataGrid> não está na **caixa de ferramentas** por padrão. Para obter informações sobre como adicioná-lo, consulte [Como Adicionar Itens à Caixa de Ferramentas](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms165355(v=vs.100)). Além disso, no Visual Studio 2005, você pode usar a janela **fontes de dados** para associação de dados de tempo de design. Para obter mais informações, consulte [Associar Controles a Dados no Visual Studio](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio).

## <a name="to-data-bind-the-datagrid-control-to-a-single-table-in-the-designer"></a>Associar os dados do controle DataGrid a uma única tabela no designer

1. Defina a propriedade <xref:System.Windows.Forms.DataGrid.DataSource%2A> do controle como o objeto que contém os itens de dados aos quais você deseja associar.

2. Se a fonte de dados for um DataSet, defina a propriedade <xref:System.Windows.Forms.DataGrid.DataMember%2A> como o nome da tabela à qual associar.

3. Se a fonte de dados for um conjunto de dados ou uma exibição de dados com base em uma tabela de conjunto de dados, adicione código ao formulário para preencher o conjunto de dados.

     O código exato usado depende do local em que o conjunto de dados está recebendo dados. Se o conjunto de dados estiver sendo preenchido diretamente de um banco de dados, normalmente, chama-se o método `Fill` de um adaptador de dados, como no exemplo de código a seguir, que preenche um conjunto de dados chamado `DsCategories1`:

    ```vb
    sqlDataAdapter1.Fill(DsCategories1)
    ```

    ```csharp
    sqlDataAdapter1.Fill(DsCategories1);
    ```

    ```cpp
    sqlDataAdapter1->Fill(dsCategories1);
    ```

4. (Opcional) Adicione os estilos apropriados de tabela e coluna à grade.

     Se não houver nenhum estilo de tabela, a tabela ainda será vista, mas com formatação mínima e todas as colunas visíveis.

## <a name="to-data-bind-the-datagrid-control-to-multiple-tables-in-a-dataset-in-the-designer"></a>Associar os dados do controle DataGrid a várias tabelas em um conjunto de dados no designer

1. Defina a propriedade <xref:System.Windows.Forms.DataGrid.DataSource%2A> do controle como o objeto que contém os itens de dados aos quais você deseja associar.

2. Se o conjunto de conteúdo contiver tabelas relacionadas (ou seja, se contiver um objeto relation), defina a propriedade <xref:System.Windows.Forms.DataGrid.DataMember%2A> como o nome da tabela pai.

3. Grave código para preencher o conjunto de dados.

## <a name="see-also"></a>Veja também

- [Visão geral do controle DataGrid](datagrid-control-overview-windows-forms.md)
- [Como adicionar tabelas e colunas ao controle DataGrid do Windows Forms](how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)
- [Controle DataGrid](datagrid-control-windows-forms.md)
- [Vinculação de dados dos Windows Forms](../windows-forms-data-binding.md)
- [Acessando dados no Visual Studio](/visualstudio/data-tools/accessing-data-in-visual-studio)
