---
title: "Como: criar um formulário mestre / detalhes usando dois controles DataGridView dos Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], master/detail form
- parent-child tables [Windows Forms], displaying on Windows Forms
- master-details lists [Windows Forms], creating
ms.assetid: 99f6e876-3f7f-4139-9063-e36587c95b02
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4a7d61af639e14948ab84c5e1a4d57030ecff122
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-masterdetail-form-using-two-windows-forms-datagridview-controls"></a>Como criar um formulário mestre/detalhado usando dois controles DataGridView dos Windows Forms
O exemplo de código a seguir cria um formulário mestre/detalhado usando dois <xref:System.Windows.Forms.DataGridView> controles associados a dois <xref:System.Windows.Forms.BindingSource> componentes. A fonte de dados é um <xref:System.Data.DataSet> que contém o `Customers` e `Orders` tabelas do banco de dados de exemplo Northwind SQL Server junto com um <xref:System.Data.DataRelation> que relaciona os dois por meio de `CustomerID` coluna.  
  
 Um <xref:System.Windows.Forms.BindingSource> está vinculado ao pai `Customers` tabela no conjunto de dados. Esses dados são exibidos no mestre <xref:System.Windows.Forms.DataGridView> controle. O outro <xref:System.Windows.Forms.BindingSource> está associado ao conector de dados primeiro. O <xref:System.Windows.Forms.BindingSource.DataMember%2A> propriedade da segunda <xref:System.Windows.Forms.BindingSource> é definido como o <xref:System.Data.DataRelation> nome. Isso faz com que os detalhes associados <xref:System.Windows.Forms.DataGridView> controle para exibir as linhas do filho `Orders` tabela que correspondem à linha atual no mestre <xref:System.Windows.Forms.DataGridView> controle.  
  
 Para uma explicação completa desse código de exemplo, consulte [Instruções passo a passo: criando um formulário mestre/detalhes usando dois controles DataGridView dos Windows Forms](../../../../docs/framework/winforms/controls/creating-a-master-detail-form-using-two-datagridviews.md).  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[System.Windows.Forms.DataGridViewMasterDetails#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/CS/masterdetails.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewMasterDetails#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/VB/masterdetails.vb#00)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer:  
  
 Referências aos assemblies System, System.Data, System.Windows.Forms e System.XML.  
  
 Para obter informações sobre como compilar este exemplo na linha de comando para [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] ou [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], consulte [Building from the Command Line (Compilando na linha de comando)](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [Compilando pela linha de comando com csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Também é possível compilar este exemplo em [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] colando o código em um novo projeto.  Consulte também [Como compilar e executar um exemplo completo de códigos dos Windows Forms usando o Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\))  
  
## <a name="net-framework-security"></a>Segurança do .NET Framework  
 O armazenamento das informações confidenciais (tal como uma senha) dentro da cadeia de conexão pode afetar a segurança do aplicativo. O uso da Autenticação do Windows (também conhecida como segurança integrada) é uma maneira mais segura de controlar o acesso a um banco de dados. Para obter mais informações, consulte [Protegendo informações de conexão](../../../../docs/framework/data/adonet/protecting-connection-information.md).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.BindingSource>  
 [Instruções passo a passo: criando um formulário mestre/detalhes usando dois controles DataGridView do Windows Forms](../../../../docs/framework/winforms/controls/creating-a-master-detail-form-using-two-datagridviews.md)  
 [Exibindo dados no controle DataGridView do Windows Forms](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)  
 [Protegendo informações de conexão](../../../../docs/framework/data/adonet/protecting-connection-information.md)
