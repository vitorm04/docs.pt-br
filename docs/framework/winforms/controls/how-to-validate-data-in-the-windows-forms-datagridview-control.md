---
title: Como validar dados no controle DataGridView dos Windows Forms
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
ms.openlocfilehash: 989952803d6fa81195107da5b0308c942c575589
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-validate-data-in-the-windows-forms-datagridview-control"></a>Como validar dados no controle DataGridView dos Windows Forms
O exemplo de código a seguir demonstra como validar dados inseridos por um usuário em um <xref:System.Windows.Forms.DataGridView> controle. Neste exemplo, o <xref:System.Windows.Forms.DataGridView> é preenchida com linhas do `Customers` tabela do banco de dados de exemplo Northwind. Quando o usuário edita uma célula a `CompanyName` coluna, seu valor é testada quanto à validade, verificando se ela não está vazia. Se o manipulador de eventos para o <xref:System.Windows.Forms.DataGridView.CellValidating> evento localiza o valor é uma cadeia de caracteres vazia, o <xref:System.Windows.Forms.DataGridView> impede que o usuário sair da célula até que uma cadeia de caracteres não vazia é inserida.  
  
 Para obter uma explicação completa sobre este exemplo de código, consulte [passo a passo: validando dados em controle de DataGridView dos Windows Forms](../../../../docs/framework/winforms/controls/walkthrough-validating-data-in-the-windows-forms-datagridview-control.md).  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewDataValidation#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#00)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer:  
  
-   Referências aos assemblies System, System. Data, System e System. XML.  
  
 Para obter informações sobre como criar este exemplo da linha de comando para o Visual Basic ou Visual c#, consulte [Compilando a partir da linha de comando](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [criação de linha de comando com csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Você também pode criar este exemplo no Visual Studio colando o código em um novo projeto.  Consulte também [Como compilar e executar um exemplo completo de código do Windows Forms usando o Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="net-framework-security"></a>Segurança do .NET Framework  
 O armazenamento das informações confidenciais (tal como uma senha) dentro da cadeia de conexão pode afetar a segurança do aplicativo. O uso da Autenticação do Windows (também conhecida como segurança integrada) é uma maneira mais segura de controlar o acesso a um banco de dados. Para obter mais informações, consulte [Protegendo informações de conexão](../../../../docs/framework/data/adonet/protecting-connection-information.md).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.BindingSource>  
 [Passo a passo: validando dados no controle DataGridView dos Windows Forms](../../../../docs/framework/winforms/controls/walkthrough-validating-data-in-the-windows-forms-datagridview-control.md)  
 [Entrada de Dados no controle DataGridView dos Windows Forms](../../../../docs/framework/winforms/controls/data-entry-in-the-windows-forms-datagridview-control.md)  
 [Passo a passo: manipulando erros que ocorrem durante a entrada de dados no controle DataGridView dos Windows Forms](../../../../docs/framework/winforms/controls/handling-errors-that-occur-during-data-entry-in-the-datagrid.md)  
 [Protegendo informações de conexão](../../../../docs/framework/data/adonet/protecting-connection-information.md)
