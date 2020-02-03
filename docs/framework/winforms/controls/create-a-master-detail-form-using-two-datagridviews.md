---
title: Criar um formulário mestre-de detalhes usando dois controles DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], master/detail form
- parent-child tables [Windows Forms], displaying on Windows Forms
- master-details lists [Windows Forms], creating
ms.assetid: 99f6e876-3f7f-4139-9063-e36587c95b02
ms.openlocfilehash: d317f4e592790c9b48b539b1601814569e14529f
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76737326"
---
# <a name="how-to-create-a-masterdetail-form-using-two-windows-forms-datagridview-controls"></a>Como criar um formulário mestre/detalhado usando dois controles DataGridView dos Windows Forms
O exemplo de código a seguir cria um formulário mestre/detalhado usando dois controles <xref:System.Windows.Forms.DataGridView> vinculados a dois componentes <xref:System.Windows.Forms.BindingSource>. A fonte de dados é uma <xref:System.Data.DataSet> que contém as tabelas `Customers` e `Orders` do banco de dados de exemplo Northwind SQL Server, juntamente com um <xref:System.Data.DataRelation> que relaciona os dois por meio da coluna `CustomerID`.  
  
 Um <xref:System.Windows.Forms.BindingSource> está associado à tabela de `Customers` pai no conjunto de dados. Esses dados são exibidos no controle de <xref:System.Windows.Forms.DataGridView> mestre. O outro <xref:System.Windows.Forms.BindingSource> está associado ao primeiro conector de dados. A propriedade <xref:System.Windows.Forms.BindingSource.DataMember%2A> da segunda <xref:System.Windows.Forms.BindingSource> é definida como o nome do <xref:System.Data.DataRelation>. Isso faz com que o controle de <xref:System.Windows.Forms.DataGridView> de detalhes associado exiba as linhas da tabela filho `Orders` que correspondem à linha atual no controle de <xref:System.Windows.Forms.DataGridView> mestre.  
  
 Para uma explicação completa desse código de exemplo, consulte [Instruções passo a passo: criando um formulário mestre/detalhes usando dois controles DataGridView dos Windows Forms](creating-a-master-detail-form-using-two-datagridviews.md).  
  
## <a name="example"></a>{1&gt;Exemplo&lt;1}  
 [!code-csharp[System.Windows.Forms.DataGridViewMasterDetails#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/CS/masterdetails.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewMasterDetails#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/VB/masterdetails.vb#00)]  
  
## <a name="compiling-the-code"></a>Compilando o Código  
 Este exemplo requer:  
  
 Referências aos assemblies System, System.Data, System.Windows.Forms e System.XML.  
  
## <a name="net-framework-security"></a>Segurança do .NET Framework  
 O armazenamento das informações confidenciais, como uma senha, dentro da cadeia de conexão pode afetar a segurança do aplicativo. O uso da Autenticação do Windows (também conhecida como segurança integrada) é uma maneira mais segura de controlar o acesso a um banco de dados. Para obter mais informações, consulte [Protegendo informações de conexão](../../data/adonet/protecting-connection-information.md).  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [Instruções passo a passo: criando um formulário mestre/detalhes usando dois controles DataGridView do Windows Forms](creating-a-master-detail-form-using-two-datagridviews.md)
- [Exibindo dados no controle DataGridView do Windows Forms](displaying-data-in-the-windows-forms-datagridview-control.md)
- [Protegendo informações de conexão](../../data/adonet/protecting-connection-information.md)
