---
title: 'Como: Classificar e filtrar dados ADO.NET com o componente BindingSource do Windows Forms'
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
ms.openlocfilehash: ae331ca9e3fd2aed654659e11434454874eff8fa
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69960419"
---
# <a name="how-to-sort-and-filter-adonet-data-with-the-windows-forms-bindingsource-component"></a>Como: Classificar e filtrar dados ADO.NET com o componente BindingSource do Windows Forms
Você pode expor a capacidade de classificação e filtragem <xref:System.Windows.Forms.BindingSource> de controle por <xref:System.Windows.Forms.BindingSource.Sort%2A> meio <xref:System.Windows.Forms.BindingSource.Filter%2A> das propriedades e. Você pode aplicar a classificação simples quando a fonte de dados subjacente <xref:System.ComponentModel.IBindingList>for um, e poderá aplicar filtragem e classificação avançada quando a fonte de dados <xref:System.ComponentModel.IBindingListView>for um. A <xref:System.Windows.Forms.BindingSource.Sort%2A> propriedade requer a sintaxe ADO.NET padrão: uma cadeia de caracteres que representa o nome de uma coluna de dados na fonte `ASC` de `DESC` dados seguida por ou para indicar se a lista deve ser classificada em ordem crescente ou decrescente. Você pode definir a classificação avançada ou a classificação em várias colunas separando cada coluna com um separador de vírgula. A <xref:System.Windows.Forms.BindingSource.Filter%2A> propriedade usa uma expressão de cadeia de caracteres.  
  
> [!NOTE]
> O armazenamento das informações confidenciais (tal como uma senha) dentro da cadeia de conexão pode afetar a segurança do aplicativo. O uso da Autenticação do Windows (também conhecida como segurança integrada) é uma maneira mais segura de controlar o acesso a um banco de dados. Para obter mais informações, consulte [Protegendo informações de conexão](../../data/adonet/protecting-connection-information.md).  
  
### <a name="to-filter-data-with-the-bindingsource"></a>Filtrar os dados com o BindingSource  
  
- Defina a <xref:System.Windows.Forms.BindingSource.Filter%2A> Propriedade como a expressão desejada.  
  
     No exemplo de código a seguir, a expressão é um nome de coluna seguido pelo valor que você deseja para a coluna.  
  
 [!code-csharp[System.Windows.Forms.DataConnectorFilterAndSort#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/CS/form1.cs#11)]
 [!code-vb[System.Windows.Forms.DataConnectorFilterAndSort#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/VB/form1.vb#11)]  
  
### <a name="to-sort-data-with-the-bindingsource"></a>Classificar os dados com o BindingSource  
  
1. Defina a <xref:System.Windows.Forms.BindingSource.Sort%2A> Propriedade como o nome da coluna que você deseja que `ASC` seja `DESC` seguido por ou para indicar a ordem crescente ou decrescente.  
  
2. Separe múltiplas colunas com uma vírgula.  
  
 [!code-csharp[System.Windows.Forms.DataConnectorFilterAndSort#12](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/CS/form1.cs#12)]
 [!code-vb[System.Windows.Forms.DataConnectorFilterAndSort#12](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/VB/form1.vb#12)]  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir carrega dados da tabela Customers do banco de dados de <xref:System.Windows.Forms.DataGridView> exemplo Northwind em um controle e filtra e classifica os dados exibidos.  
  
 [!code-csharp[System.Windows.Forms.DataConnectorFilterAndSort#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnectorFilterAndSort#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Para executar este exemplo, Cole o código em um formulário que contenha <xref:System.Windows.Forms.BindingSource> um `BindingSource1` nome e <xref:System.Windows.Forms.DataGridView> um `dataGridView1`nomeado. Manipule o <xref:System.Windows.Forms.Form.Load> evento para o formulário e chame `InitializeSortedFilteredBindingSource` o método Carregar manipulador de eventos.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.BindingSource.Sort%2A>
- <xref:System.Windows.Forms.BindingSource.Filter%2A>
- [Como: Instalar bancos de dados de exemplo](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/8b6y4c7s(v=vs.120))
- [Componente BindingSource](bindingsource-component.md)
