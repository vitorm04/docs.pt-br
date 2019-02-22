---
title: 'Como: Alterar as bordas de formulários do Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms, changing the borders
ms.assetid: b3d5fa56-80c6-4b10-b505-f9672307ed55
ms.openlocfilehash: 5efda369b2059afd350fc947b706fb9f4c27ae14
ms.sourcegitcommit: 2b986afe4ce9e13bbeec929c9737757eb61de60e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56664439"
---
# <a name="how-to-change-the-borders-of-windows-forms"></a><span data-ttu-id="abd0c-102">Como: Alterar as bordas de formulários do Windows</span><span class="sxs-lookup"><span data-stu-id="abd0c-102">How to: Change the Borders of Windows Forms</span></span>
<span data-ttu-id="abd0c-103">Você tem vários estilos de borda para escolher quando estiver determinando a aparência e comportamento dos Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="abd0c-103">You have several border styles to choose from when you are determining the appearance and behavior of your Windows Forms.</span></span> <span data-ttu-id="abd0c-104">Alterando o <xref:System.Windows.Forms.Form.FormBorderStyle%2A> propriedade, você pode controlar o comportamento de redimensionamento do formulário.</span><span class="sxs-lookup"><span data-stu-id="abd0c-104">By changing the <xref:System.Windows.Forms.Form.FormBorderStyle%2A> property, you can control the resizing behavior of the form.</span></span> <span data-ttu-id="abd0c-105">Além disso, definindo o <xref:System.Windows.Forms.Form.FormBorderStyle%2A> afeta como a barra de legenda é exibida, bem como quais botões podem aparecer nela.</span><span class="sxs-lookup"><span data-stu-id="abd0c-105">In addition, setting the <xref:System.Windows.Forms.Form.FormBorderStyle%2A> affects how the caption bar is displayed as well as what buttons might appear on it.</span></span> <span data-ttu-id="abd0c-106">Para obter mais informações, consulte <xref:System.Windows.Forms.FormBorderStyle>.</span><span class="sxs-lookup"><span data-stu-id="abd0c-106">For more information, see <xref:System.Windows.Forms.FormBorderStyle>.</span></span>  
  
 <span data-ttu-id="abd0c-107">Há um suporte abrangente para esta tarefa no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="abd0c-107">There is extensive support for this task in Visual Studio.</span></span>  
  
 <span data-ttu-id="abd0c-108">Confira também [Como: Alterar as bordas dos Windows Forms usando o Designer](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/yettzh3e(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="abd0c-108">See also [How to: Change the Borders of Windows Forms Using the Designer](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/yettzh3e(v=vs.100)).</span></span>  
  
### <a name="to-set-the-border-style-of-windows-forms-programmatically"></a><span data-ttu-id="abd0c-109">Para definir o estilo de borda dos Windows Forms de maneira programática</span><span class="sxs-lookup"><span data-stu-id="abd0c-109">To set the border style of Windows Forms programmatically</span></span>  
  
-   <span data-ttu-id="abd0c-110">Defina o <xref:System.Windows.Forms.Form.FormBorderStyle%2A> propriedade para o estilo desejado.</span><span class="sxs-lookup"><span data-stu-id="abd0c-110">Set the <xref:System.Windows.Forms.Form.FormBorderStyle%2A> property to the style you want.</span></span> <span data-ttu-id="abd0c-111">O exemplo de código a seguir define o estilo de borda do formulário `DlgBx1` para <xref:System.Windows.Forms.FormBorderStyle.FixedDialog>.</span><span class="sxs-lookup"><span data-stu-id="abd0c-111">The following code example sets the border style of form `DlgBx1` to <xref:System.Windows.Forms.FormBorderStyle.FixedDialog>.</span></span>  
  
    ```vb  
    DlgBx1.FormBorderStyle = System.Windows.Forms.FormBorderStyle.FixedDialog  
    ```  
  
    ```csharp  
    DlgBx1.FormBorderStyle = System.Windows.Forms.FormBorderStyle.FixedDialog;  
    ```  
  
    ```cpp  
    DlgBx1->FormBorderStyle =  
       System::Windows::Forms::FormBorderStyle::FixedDialog;  
    ```  
  
     <span data-ttu-id="abd0c-112">Consulte também [como: Criar caixas de diálogo em tempo de Design](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/55cz5x2c(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="abd0c-112">Also see [How to: Create Dialog Boxes at Design Time](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/55cz5x2c(v=vs.100)).</span></span>  
  
     <span data-ttu-id="abd0c-113">Além disso, se você escolheu um estilo de borda para o formulário que fornece botões opcionais **Minimizar** e **Maximizar**, é possível especificar se deseja que um ou os dois botões sejam funcionais.</span><span class="sxs-lookup"><span data-stu-id="abd0c-113">Additionally, if you have chosen a border style for the form that provides optional **Minimize** and **Maximize** buttons, you can specify whether you want either or both of these buttons to be functional.</span></span> <span data-ttu-id="abd0c-114">Esses botões são úteis quando quiser controlar de perto a experiência do usuário.</span><span class="sxs-lookup"><span data-stu-id="abd0c-114">These buttons are useful when you want to closely control the user experience.</span></span> <span data-ttu-id="abd0c-115">Os botões **Minimizar** e **Maximizar** são habilitados por padrão e sua funcionalidade é manipulada por meio da janela **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="abd0c-115">The **Minimize** and **Maximize** buttons are enabled by default, and their functionality is manipulated through the **Properties** window.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="abd0c-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="abd0c-116">See also</span></span>
- <xref:System.Windows.Forms.FormBorderStyle>
- <xref:System.Windows.Forms.FormBorderStyle.FixedDialog>
- [<span data-ttu-id="abd0c-117">Guia de introdução ao Windows Forms</span><span class="sxs-lookup"><span data-stu-id="abd0c-117">Getting Started with Windows Forms</span></span>](../../../docs/framework/winforms/getting-started-with-windows-forms.md)
