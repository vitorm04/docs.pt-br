---
title: 'Como: Criar um formulário mestre / detalhes usando dois controles de Windows Forms DataGridView'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], master/detail form
- parent-child tables [Windows Forms], displaying on Windows Forms
- master-details lists [Windows Forms], creating
ms.assetid: 99f6e876-3f7f-4139-9063-e36587c95b02
ms.openlocfilehash: 16f23fac53cee5f6c007df6046e73cb7d9e1fbca
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65589206"
---
# <a name="how-to-create-a-masterdetail-form-using-two-windows-forms-datagridview-controls"></a><span data-ttu-id="bfeb7-102">Como: Criar um formulário mestre/de detalhes usando dois controles DataGridView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="bfeb7-102">How to: Create a Master/Detail Form Using Two Windows Forms DataGridView Controls</span></span>
<span data-ttu-id="bfeb7-103">O exemplo de código a seguir cria um formulário mestre/detalhes usando dois <xref:System.Windows.Forms.DataGridView> controles associados a dois <xref:System.Windows.Forms.BindingSource> componentes.</span><span class="sxs-lookup"><span data-stu-id="bfeb7-103">The following code example creates a master/detail form using two <xref:System.Windows.Forms.DataGridView> controls bound to two <xref:System.Windows.Forms.BindingSource> components.</span></span> <span data-ttu-id="bfeb7-104">A fonte de dados é um <xref:System.Data.DataSet> que contém o `Customers` e `Orders` tabelas do banco de dados de exemplo Northwind do SQL Server juntamente com um <xref:System.Data.DataRelation> que relaciona as duas as `CustomerID` coluna.</span><span class="sxs-lookup"><span data-stu-id="bfeb7-104">The data source is a <xref:System.Data.DataSet> that contains the `Customers` and `Orders` tables from the Northwind SQL Server sample database along with a <xref:System.Data.DataRelation> that relates the two through the `CustomerID` column.</span></span>  
  
 <span data-ttu-id="bfeb7-105">Uma <xref:System.Windows.Forms.BindingSource> está associado ao pai `Customers` tabela no conjunto de dados.</span><span class="sxs-lookup"><span data-stu-id="bfeb7-105">One <xref:System.Windows.Forms.BindingSource> is bound to the parent `Customers` table in the data set.</span></span> <span data-ttu-id="bfeb7-106">Esses dados são exibidos no mestre <xref:System.Windows.Forms.DataGridView> controle.</span><span class="sxs-lookup"><span data-stu-id="bfeb7-106">This data is displayed in the master <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="bfeb7-107">O outro <xref:System.Windows.Forms.BindingSource> está associado ao primeiro conector de dados.</span><span class="sxs-lookup"><span data-stu-id="bfeb7-107">The other <xref:System.Windows.Forms.BindingSource> is bound to the first data connector.</span></span> <span data-ttu-id="bfeb7-108">O <xref:System.Windows.Forms.BindingSource.DataMember%2A> propriedade da segunda <xref:System.Windows.Forms.BindingSource> é definido como o <xref:System.Data.DataRelation> nome.</span><span class="sxs-lookup"><span data-stu-id="bfeb7-108">The <xref:System.Windows.Forms.BindingSource.DataMember%2A> property of the second <xref:System.Windows.Forms.BindingSource> is set to the <xref:System.Data.DataRelation> name.</span></span> <span data-ttu-id="bfeb7-109">Isso faz com que os detalhes associados <xref:System.Windows.Forms.DataGridView> controle para exibir as linhas do filho `Orders` tabela que correspondem à linha atual no mestre <xref:System.Windows.Forms.DataGridView> controle.</span><span class="sxs-lookup"><span data-stu-id="bfeb7-109">This causes the associated detail <xref:System.Windows.Forms.DataGridView> control to display the rows of the child `Orders` table that correspond to the current row in the master <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 <span data-ttu-id="bfeb7-110">Para obter uma explicação completa sobre este exemplo de código, consulte [passo a passo: Criando um formulário mestre/detalhes usando dois Windows Forms a controles DataGridView](creating-a-master-detail-form-using-two-datagridviews.md).</span><span class="sxs-lookup"><span data-stu-id="bfeb7-110">For a complete explanation of this code example, see [Walkthrough: Creating a Master/Detail Form Using Two Windows Forms DataGridView Controls](creating-a-master-detail-form-using-two-datagridviews.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="bfeb7-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="bfeb7-111">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewMasterDetails#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/CS/masterdetails.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewMasterDetails#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/VB/masterdetails.vb#00)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="bfeb7-112">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="bfeb7-112">Compiling the Code</span></span>  
 <span data-ttu-id="bfeb7-113">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="bfeb7-113">This example requires:</span></span>  
  
 <span data-ttu-id="bfeb7-114">Referências aos assemblies System, System.Data, System.Windows.Forms e System.XML.</span><span class="sxs-lookup"><span data-stu-id="bfeb7-114">References to the System, System.Data, System.Windows.Forms, and System.XML assemblies.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="bfeb7-115">Segurança do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="bfeb7-115">.NET Framework Security</span></span>  
 <span data-ttu-id="bfeb7-116">O armazenamento das informações confidenciais (tal como uma senha) dentro da cadeia de conexão pode afetar a segurança do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="bfeb7-116">Storing sensitive information, such as a password, within the connection string can affect the security of your application.</span></span> <span data-ttu-id="bfeb7-117">O uso da Autenticação do Windows (também conhecida como segurança integrada) é uma maneira mais segura de controlar o acesso a um banco de dados.</span><span class="sxs-lookup"><span data-stu-id="bfeb7-117">Using Windows Authentication (also known as integrated security) is a more secure way to control access to a database.</span></span> <span data-ttu-id="bfeb7-118">Para obter mais informações, consulte [Protegendo informações de conexão](../../data/adonet/protecting-connection-information.md).</span><span class="sxs-lookup"><span data-stu-id="bfeb7-118">For more information, see [Protecting Connection Information](../../data/adonet/protecting-connection-information.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bfeb7-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bfeb7-119">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [<span data-ttu-id="bfeb7-120">Passo a passo: Criando um formulário mestre/detalhes usando dois controles de Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="bfeb7-120">Walkthrough: Creating a Master/Detail Form Using Two Windows Forms DataGridView Controls</span></span>](creating-a-master-detail-form-using-two-datagridviews.md)
- [<span data-ttu-id="bfeb7-121">Exibindo dados no controle DataGridView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="bfeb7-121">Displaying Data in the Windows Forms DataGridView Control</span></span>](displaying-data-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="bfeb7-122">Protegendo informações de conexão</span><span class="sxs-lookup"><span data-stu-id="bfeb7-122">Protecting Connection Information</span></span>](../../data/adonet/protecting-connection-information.md)
