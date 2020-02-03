---
title: Classificar e filtrar dados do ADO.NET com o componente BindingSource
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sorting data
- data sorting [Windows Forms], ADO.NET
- data [Windows Forms], filtering
- BindingSource component [Windows Forms], sorting and filtering data
- filtering [Windows Forms], ADO.NET
- data [Windows Forms], sorting
- ADO.NET [Windows Forms]
ms.assetid: 6c206daf-d706-4602-9dbe-435343052063
ms.openlocfilehash: cf1da3bb94b26449eb72b0e4930b262236487acc
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742968"
---
# <a name="how-to-sort-and-filter-adonet-data-with-the-windows-forms-bindingsource-component"></a>Como classificar e filtrar dados ADO.NET com o componente BindingSource dos Windows Forms
Você pode expor o recurso de classificação e filtragem do controle de <xref:System.Windows.Forms.BindingSource> por meio das propriedades <xref:System.Windows.Forms.BindingSource.Sort%2A> e <xref:System.Windows.Forms.BindingSource.Filter%2A>. Você pode aplicar a classificação simples quando a fonte de dados subjacente é uma <xref:System.ComponentModel.IBindingList>, e você pode aplicar filtragem e classificação avançada quando a fonte de dados é uma <xref:System.ComponentModel.IBindingListView>. A propriedade <xref:System.Windows.Forms.BindingSource.Sort%2A> requer a sintaxe ADO.NET padrão: uma cadeia de caracteres que representa o nome de uma coluna de dados na fonte de dados seguida por `ASC` ou `DESC` para indicar se a lista deve ser classificada em ordem crescente ou decrescente. Você pode definir a classificação avançada ou a classificação em várias colunas separando cada coluna com um separador de vírgula. A propriedade <xref:System.Windows.Forms.BindingSource.Filter%2A> usa uma expressão de cadeia de caracteres.  
  
> [!NOTE]
> O armazenamento das informações confidenciais, como uma senha, dentro da cadeia de conexão pode afetar a segurança do aplicativo. O uso da Autenticação do Windows (também conhecida como segurança integrada) é uma maneira mais segura de controlar o acesso a um banco de dados. Para obter mais informações, consulte [Protegendo informações de conexão](../../data/adonet/protecting-connection-information.md).  
  
### <a name="to-filter-data-with-the-bindingsource"></a>Filtrar os dados com o BindingSource  
  
- Defina a propriedade <xref:System.Windows.Forms.BindingSource.Filter%2A> como a expressão desejada.  
  
     No exemplo de código a seguir, a expressão é um nome de coluna seguido pelo valor que você deseja para a coluna.  
  
 [!code-csharp[System.Windows.Forms.DataConnectorFilterAndSort#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/CS/form1.cs#11)]
 [!code-vb[System.Windows.Forms.DataConnectorFilterAndSort#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/VB/form1.vb#11)]  
  
### <a name="to-sort-data-with-the-bindingsource"></a>Classificar os dados com o BindingSource  
  
1. Defina a propriedade <xref:System.Windows.Forms.BindingSource.Sort%2A> como o nome da coluna que você deseja que seja seguido por `ASC` ou `DESC` para indicar a ordem crescente ou decrescente.  
  
2. Separe múltiplas colunas com uma vírgula.  
  
 [!code-csharp[System.Windows.Forms.DataConnectorFilterAndSort#12](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/CS/form1.cs#12)]
 [!code-vb[System.Windows.Forms.DataConnectorFilterAndSort#12](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/VB/form1.vb#12)]  
  
## <a name="example"></a>{1&gt;Exemplo&lt;1}  
 O exemplo de código a seguir carrega dados da tabela Customers do banco de dados de exemplo Northwind em um controle <xref:System.Windows.Forms.DataGridView> e filtra e classifica os dados exibidos.  
  
 [!code-csharp[System.Windows.Forms.DataConnectorFilterAndSort#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnectorFilterAndSort#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Compilando o Código  
 Para executar este exemplo, Cole o código em um formulário que contenha um <xref:System.Windows.Forms.BindingSource> chamado `BindingSource1` e um <xref:System.Windows.Forms.DataGridView> chamado `dataGridView1`. Manipule o evento <xref:System.Windows.Forms.Form.Load> para o formulário e chame `InitializeSortedFilteredBindingSource` no método Carregar manipulador de eventos.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.BindingSource.Sort%2A>
- <xref:System.Windows.Forms.BindingSource.Filter%2A>
- [Como instalar bancos de dados de exemplo](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/8b6y4c7s(v=vs.120))
- [Componente BindingSource](bindingsource-component.md)
