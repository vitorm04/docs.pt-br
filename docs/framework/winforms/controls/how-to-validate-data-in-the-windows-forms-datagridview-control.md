---
title: 'Como: Validar dados no controle DataGridView do Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data [Windows Forms], validation
- DataGridView control [Windows Forms], data validation
- data grids [Windows Forms], validating data
- data validation [Windows Forms], Windows Forms
ms.assetid: d10aef35-701e-4a3c-a684-2a2ed1aeaca6
ms.openlocfilehash: 12fd668e22703271f8c629baf56487dd084cfd8b
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65591039"
---
# <a name="how-to-validate-data-in-the-windows-forms-datagridview-control"></a>Como: Validar dados no controle DataGridView do Windows Forms
O exemplo de código a seguir demonstra como validar dados inseridos por um usuário em um <xref:System.Windows.Forms.DataGridView> controle. Neste exemplo, o <xref:System.Windows.Forms.DataGridView> é preenchida com linhas do `Customers` tabela do banco de dados de exemplo Northwind. Quando o usuário edita uma célula no `CompanyName` coluna, seu valor é testada quanto à validade, verificando se ele não está vazio. Se o manipulador de eventos para o <xref:System.Windows.Forms.DataGridView.CellValidating> evento localiza que o valor é uma cadeia de caracteres vazia, o <xref:System.Windows.Forms.DataGridView> impede que o usuário sair da célula até que uma cadeia de caracteres não vazia seja inserida.  
  
 Para obter uma explicação completa sobre este exemplo de código, consulte [passo a passo: Validando dados em que o Windows Forms DataGridView Control](walkthrough-validating-data-in-the-windows-forms-datagridview-control.md).  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewDataValidation#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#00)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer:  
  
- Referências aos assemblies System, System. Data, System e System. XML.  
  
## <a name="net-framework-security"></a>Segurança do .NET Framework  
 O armazenamento das informações confidenciais (tal como uma senha) dentro da cadeia de conexão pode afetar a segurança do aplicativo. O uso da Autenticação do Windows (também conhecida como segurança integrada) é uma maneira mais segura de controlar o acesso a um banco de dados. Para obter mais informações, consulte [Protegendo informações de conexão](../../data/adonet/protecting-connection-information.md).  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [Passo a passo: Validando dados no controle DataGridView dos Windows Forms](walkthrough-validating-data-in-the-windows-forms-datagridview-control.md)
- [Entrada de Dados no controle DataGridView dos Windows Forms](data-entry-in-the-windows-forms-datagridview-control.md)
- [Passo a passo: Tratamento de erros que ocorrem durante a entrada de dados no controle DataGridView dos Windows Forms](handling-errors-that-occur-during-data-entry-in-the-datagrid.md)
- [Protegendo informações de conexão](../../data/adonet/protecting-connection-information.md)
