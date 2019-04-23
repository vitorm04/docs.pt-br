---
title: 'Como: Habilitar a reorganização da coluna no controle DataGridView do Windows Forms usando o designer'
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], column order
- Windows Forms, columns
- columns [Windows Forms], reordering
- data [Windows Forms], displaying
ms.assetid: d82bd69c-6799-4439-a32c-91139c5901d1
ms.openlocfilehash: 966ffe131d10b97fe9632bb1ff23273b1dabd061
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59194962"
---
# <a name="how-to-enable-column-reordering-in-the-windows-forms-datagridview-control-using-the-designer"></a><span data-ttu-id="203c6-102">Como: Habilitar a reorganização da coluna no controle DataGridView do Windows Forms usando o designer</span><span class="sxs-lookup"><span data-stu-id="203c6-102">How to: Enable Column Reordering in the Windows Forms DataGridView Control Using the Designer</span></span>
<span data-ttu-id="203c6-103">Ao exibir os dados exibidos em um Windows Forms <xref:System.Windows.Forms.DataGridView> controle, os usuários desejam, às vezes comparar os valores em colunas específicas.</span><span class="sxs-lookup"><span data-stu-id="203c6-103">When viewing data displayed in a Windows Forms <xref:System.Windows.Forms.DataGridView> control, users sometimes want to compare the values in specific columns.</span></span> <span data-ttu-id="203c6-104">Isso pode ser inconveniente se as colunas são separadas amplamente no controle, especialmente se os usuários devem rolar horizontalmente e voltar para ver todas as colunas que estão interessados.</span><span class="sxs-lookup"><span data-stu-id="203c6-104">This can be inconvenient if the columns are widely separated in the control, especially if users must scroll back and forth horizontally in order to see all the columns they are interested in.</span></span> <span data-ttu-id="203c6-105">Você pode tornar a tarefa de comparar valores de coluna mais fácil, habilitando os usuários reordenar as colunas.</span><span class="sxs-lookup"><span data-stu-id="203c6-105">You can make the task of comparing column values easier by enabling your users to reorder the columns.</span></span> <span data-ttu-id="203c6-106">Quando você habilita a reordenação de coluna, os usuários podem mover uma coluna para uma nova posição, arrastando o cabeçalho de coluna com o mouse.</span><span class="sxs-lookup"><span data-stu-id="203c6-106">When you enable column reordering, users can move a column to a new position by dragging the column header with the mouse.</span></span>  
  
 <span data-ttu-id="203c6-107">O procedimento a seguir exige um **aplicativo do Windows** projeto com um formulário que contém um <xref:System.Windows.Forms.DataGridView> controle.</span><span class="sxs-lookup"><span data-stu-id="203c6-107">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="203c6-108">Para obter informações sobre como configurar um projeto desse tipo, consulte [como: Criar um projeto de aplicativo do Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project) e [como: Adicionar controles ao Windows Forms](how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="203c6-108">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="203c6-109">As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas.</span><span class="sxs-lookup"><span data-stu-id="203c6-109">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="203c6-110">Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="203c6-110">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="203c6-111">Para obter mais informações, confira [Personalizar o IDE do Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="203c6-111">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-enable-column-reordering"></a><span data-ttu-id="203c6-112">Para habilitar a reorganização de colunas</span><span class="sxs-lookup"><span data-stu-id="203c6-112">To enable column reordering</span></span>  
  
-   <span data-ttu-id="203c6-113">Clique no glifo de marca inteligente (![glifo de Smart Tag](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) no canto superior direito dos <xref:System.Windows.Forms.DataGridView> controle e, em seguida, selecione **habilitar reorganização de colunas**.</span><span class="sxs-lookup"><span data-stu-id="203c6-113">Click the smart tag glyph (![Smart Tag Glyph](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) on the upper-right corner of the <xref:System.Windows.Forms.DataGridView> control, and then select **Enable Column Reordering**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="203c6-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="203c6-114">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.AllowUserToOrderColumns%2A?displayProperty=nameWithType>
- [<span data-ttu-id="203c6-115">Como: Congelar colunas no controle DataGridView do Windows Forms usando o Designer</span><span class="sxs-lookup"><span data-stu-id="203c6-115">How to: Freeze Columns in the Windows Forms DataGridView Control Using the Designer</span></span>](freeze-columns-in-the-datagrid-using-the-designer.md)
- [<span data-ttu-id="203c6-116">Como: Criar um projeto de aplicativo do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="203c6-116">How to: Create a Windows Forms application project</span></span>](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [<span data-ttu-id="203c6-117">Como: Adicionar controles ao Windows Forms</span><span class="sxs-lookup"><span data-stu-id="203c6-117">How to: Add Controls to Windows Forms</span></span>](how-to-add-controls-to-windows-forms.md)
