---
title: Adicionar tabelas e colunas ao controle DataGrid
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- columns [Windows Forms], adding to DataGrid control
- tables [Windows Forms], adding to DataGrid control
- DataGrid control [Windows Forms], adding tables and columns
ms.assetid: 2fe661b9-aa06-49b9-a314-a0d3cbfdcb4d
ms.openlocfilehash: 2db2e38c326cbcd78c58ee4fe00cd9ed20ae0e8a
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76747212"
---
# <a name="how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control"></a>Como adicionar tabelas e colunas ao controle DataGrid dos Windows Forms

> [!NOTE]
> O controle <xref:System.Windows.Forms.DataGridView> substitui e adiciona funcionalidade ao controle <xref:System.Windows.Forms.DataGrid>, no entanto, o controle <xref:System.Windows.Forms.DataGrid> é mantido para compatibilidade com versões anteriores e para uso futuro, se desejado. Para obter mais informações, consulte [Diferenças Entre o Windows Forms DataGridView e os Controles do DataGrid](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).

Você pode exibir dados no Windows Forms <xref:System.Windows.Forms.DataGrid> controle em tabelas e colunas criando objetos **DataGridTableStyle** e adicionando-os ao objeto **GridTableStylesCollection** , que é acessado por meio da propriedade **tablestyles** do controle de <xref:System.Windows.Forms.DataGrid>. Cada estilo de tabela exibe o conteúdo da tabela de dados especificada na propriedade **MappingName** do objeto **DataGridTableStyle**. Por padrão, um estilo de tabela sem estilos de coluna especificados exibirá todas as colunas dentro dessa tabela de dados. Você pode restringir quais colunas da tabela aparecem adicionando objetos **DataGridColumnStyle** ao objeto **GridColumnStylesCollection**, que é acessado por meio da propriedade **GridColumnStyles** de cada objeto **DataGridTableStyle**.

### <a name="to-add-a-table-and-column-to-a-datagrid-programmatically"></a>Adicionar uma tabela e uma coluna a um DataGrid com programação

1. Para exibir os dados na tabela, primeiro você deve associar o controle de <xref:System.Windows.Forms.DataGrid> a um DataSet. Para obter mais informações, consulte [Como associar o controle DataGrid dos Windows Forms a uma fonte de dados](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md).

    > [!CAUTION]
    > Ao especificar os estilos de coluna com programação, sempre crie os objetos **DataGridColumnStyle** e adicione-os ao objeto **GridColumnStylesCollection** objeto antes de adicionar objetos **DataGridTableStyle** para o objeto **GridTableStylesCollection**. Ao adicionar um objeto **DataGridTableStyle** vazio à coleção, os objetos **DataGridColumnStyle** são gerados automaticamente para você. Consequentemente, uma exceção será gerada se você tentar adicionar novos objetos **DataGridColumnStyle** com valores de **MappingName** duplicados ao objeto **GridColumnStylesCollection**.

2. Declare um novo estilo de tabela e defina seu nome de mapeamento.

    ```vb
    Dim ts1 As New DataGridTableStyle()
    ts1.MappingName = "Customers"
    ```

    ```csharp
    DataGridTableStyle ts1 = new DataGridTableStyle();
    ts1.MappingName = "Customers";
    ```

    ```cpp
    DataGridTableStyle* ts1 = new DataGridTableStyle();
    ts1->MappingName = S"Customers";
    ```

3. Declare um novo estilo de coluna e defina seu nome de mapeamento e outras propriedades.

    ```vb
    Dim myDataCol As New DataGridBoolColumn()
    myDataCol.HeaderText = "My New Column"
    myDataCol.MappingName = "Current"
    ```

    ```csharp
    DataGridBoolColumn myDataCol = new DataGridBoolColumn();
    myDataCol.HeaderText = "My New Column";
    myDataCol.MappingName = "Current";
    ```

    ```cpp
    DataGridBoolColumn^ myDataCol = gcnew DataGridBoolColumn();
    myDataCol->HeaderText = "My New Column";
    myDataCol->MappingName = "Current";
    ```

4. Chame o método **Adicionar** do objeto **GridColumnStylesCollection** para adicionar a coluna ao estilo de tabela

    ```vb
    ts1.GridColumnStyles.Add(myDataCol)
    ```

    ```csharp
    ts1.GridColumnStyles.Add(myDataCol);
    ```

    ```cpp
    ts1->GridColumnStyles->Add(myDataCol);
    ```

5. Chame o método **Adicionar** do objeto **GridTableStylesCollection** para adicionar o estilo de tabela para a grade de dados.

    ```vb
    DataGrid1.TableStyles.Add(ts1)
    ```

    ```csharp
    dataGrid1.TableStyles.Add(ts1);
    ```

    ```cpp
    dataGrid1->TableStyles->Add(ts1);
    ```

## <a name="see-also"></a>Consulte também

- [Controle DataGrid](datagrid-control-windows-forms.md)
- [Como excluir ou ocultar colunas no controle DataGrid dos Windows Forms](how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)
