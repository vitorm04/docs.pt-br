---
title: Como alterar o tipo de uma coluna DataGridView dos Windows Forms usando o designer
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Forms, columns
- columns [Windows Forms], types
- DataGridView control [Windows Forms], changing column type
- data [Windows Forms], displaying
ms.assetid: 7f994d45-600d-4190-a187-35803214b40c
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 020eca128300f964614423e3ce371c00cb437ffb
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-change-the-type-of-a-windows-forms-datagridview-column-using-the-designer"></a><span data-ttu-id="e37d6-102">Como alterar o tipo de uma coluna DataGridView dos Windows Forms usando o designer</span><span class="sxs-lookup"><span data-stu-id="e37d6-102">How to: Change the Type of a Windows Forms DataGridView Column Using the Designer</span></span>
<span data-ttu-id="e37d6-103">Às vezes você deseja alterar o tipo de uma coluna que já foi adicionado a um Windows Forms <xref:System.Windows.Forms.DataGridView> controle.</span><span class="sxs-lookup"><span data-stu-id="e37d6-103">Sometimes you will want to change the type of a column that has already been added to a Windows Forms <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="e37d6-104">Por exemplo, talvez deseje modificar os tipos de algumas das colunas que são geradas automaticamente quando você associa o controle a uma fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="e37d6-104">For example, you may want to modify the types of some of the columns that are generated automatically when you bind the control to a data source.</span></span> <span data-ttu-id="e37d6-105">Isso é útil quando a tabela exibida contém colunas com chaves estrangeiras para linhas em uma tabela relacionada.</span><span class="sxs-lookup"><span data-stu-id="e37d6-105">This is useful when the table you display has columns containing foreign keys to rows in a related table.</span></span> <span data-ttu-id="e37d6-106">Nesse caso, talvez você queira substituir as colunas da caixa de texto que exibem essas chaves estrangeiras com colunas de caixa de combinação que exibem os valores mais significativos da tabela relacionada.</span><span class="sxs-lookup"><span data-stu-id="e37d6-106">In this case, you may want to replace the text box columns that display these foreign keys with combo box columns that display more meaningful values from the related table.</span></span>  
  
 <span data-ttu-id="e37d6-107">O procedimento a seguir requer um **aplicativo do Windows** projeto com um formulário que contém um <xref:System.Windows.Forms.DataGridView> controle.</span><span class="sxs-lookup"><span data-stu-id="e37d6-107">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="e37d6-108">Para obter informações sobre como configurar um projeto desse tipo, consulte [Como criar um projeto de aplicativos do Windows](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) e [Como adicionar controles ao Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="e37d6-108">For information about setting up such a project, see [How to: Create a Windows Application Project](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) and [How to: Add Controls to Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e37d6-109">As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas.</span><span class="sxs-lookup"><span data-stu-id="e37d6-109">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="e37d6-110">Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="e37d6-110">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="e37d6-111">Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="e37d6-111">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-change-the-type-of-a-column-using-the-designer"></a><span data-ttu-id="e37d6-112">Para alterar o tipo de uma coluna usando o designer</span><span class="sxs-lookup"><span data-stu-id="e37d6-112">To change the type of a column using the designer</span></span>  
  
1.  <span data-ttu-id="e37d6-113">Clique na marca inteligente (![marca inteligente](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) no canto superior direito do <xref:System.Windows.Forms.DataGridView> de controle e, em seguida, selecione **Editar colunas**.</span><span class="sxs-lookup"><span data-stu-id="e37d6-113">Click the smart tag glyph (![Smart Tag Glyph](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) on the upper-right corner of the <xref:System.Windows.Forms.DataGridView> control, and then select **Edit Columns**.</span></span>  
  
2.  <span data-ttu-id="e37d6-114">Selecione uma coluna na lista **Colunas Selecionadas**.</span><span class="sxs-lookup"><span data-stu-id="e37d6-114">Select a column from the **Selected Columns** list.</span></span>  
  
3.  <span data-ttu-id="e37d6-115">Na grade **Propriedades da coluna** grade, defina a propriedade `ColumnType` como o novo tipo de coluna.</span><span class="sxs-lookup"><span data-stu-id="e37d6-115">In the **Column Properties** grid, set the `ColumnType` property to the new column type.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e37d6-116">A propriedade `ColumnType` é uma propriedade somente em tempo de design que indica a classe que representa o tipo de coluna.</span><span class="sxs-lookup"><span data-stu-id="e37d6-116">The `ColumnType` property is a design-time-only property that indicates the class representing the column type.</span></span> <span data-ttu-id="e37d6-117">Não é uma propriedade real definida em uma classe de coluna.</span><span class="sxs-lookup"><span data-stu-id="e37d6-117">It is not an actual property defined in a column class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e37d6-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e37d6-118">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewColumn>  
 [<span data-ttu-id="e37d6-119">Como: criar um projeto de aplicativo do Windows</span><span class="sxs-lookup"><span data-stu-id="e37d6-119">How to: Create a Windows Application Project</span></span>](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa)  
 [<span data-ttu-id="e37d6-120">Como Adicionar Controles ao Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e37d6-120">How to: Add Controls to Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)
