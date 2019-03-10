---
title: Efeitos da modificação da aparência de um formulário base
ms.date: 03/30/2017
helpviewer_keywords:
- parent forms [Windows Forms]
- inherited forms [Windows Forms], modifications to base form
- Windows Forms, base form appearance
- base forms
- inheritance [Windows Forms], forms
ms.assetid: 1c3f2b29-a05c-4c6f-aa1a-4e66b94f343a
ms.openlocfilehash: a253fef2bc7220d13c0ca373a38a5bf2f5842415
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57715549"
---
# <a name="effects-of-modifying-a-base-forms-appearance"></a><span data-ttu-id="f9490-102">Efeitos da modificação da aparência de um formulário base</span><span class="sxs-lookup"><span data-stu-id="f9490-102">Effects of Modifying a Base Form's Appearance</span></span>
<span data-ttu-id="f9490-103">Durante o desenvolvimento de aplicativo, geralmente você precisará alterar a aparência do formulário base do qual outros formulários no projeto (ou em outros projetos) estão herdando.</span><span class="sxs-lookup"><span data-stu-id="f9490-103">During application development, you may often need to change the appearance of the base form from which other forms in the project (or in other projects) are inheriting.</span></span>  
  
 <span data-ttu-id="f9490-104">No tempo de design, as alterações de aparência do formulário base (seja a configuração de propriedades ou a adição e subtração de controles) são refletidas nos formulários herdados quando o projeto que contém o formulário básico é criado.</span><span class="sxs-lookup"><span data-stu-id="f9490-104">At design time, changes to the base form's appearance (be it the setting of properties or the addition and subtraction of controls) are reflected on inherited forms when the project containing the base form is built.</span></span> <span data-ttu-id="f9490-105">Não é suficiente para que você possa simplesmente salvar as alterações para o formulário básico.</span><span class="sxs-lookup"><span data-stu-id="f9490-105">It is not sufficient for you to simply save the changes to the base form.</span></span> <span data-ttu-id="f9490-106">Para criar um projeto, escolha **construir** da **Build** menu.</span><span class="sxs-lookup"><span data-stu-id="f9490-106">To build a project, choose **Build** from the **Build** menu.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f9490-107">As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas.</span><span class="sxs-lookup"><span data-stu-id="f9490-107">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="f9490-108">Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="f9490-108">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="f9490-109">Para obter mais informações, confira [Personalizar o IDE do Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="f9490-109">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
 <span data-ttu-id="f9490-110">As modificações feitas no formulário de base no tempo de execução tem afetam formulários herdados que já são instanciados.</span><span class="sxs-lookup"><span data-stu-id="f9490-110">Modifications made to the base form at run time have no affect on inherited forms that are already instantiated.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9490-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f9490-111">See also</span></span>
- [<span data-ttu-id="f9490-112">base</span><span class="sxs-lookup"><span data-stu-id="f9490-112">base</span></span>](~/docs/csharp/language-reference/keywords/base.md)
- [<span data-ttu-id="f9490-113">Como: Herdar Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f9490-113">How to: Inherit Windows Forms</span></span>](how-to-inherit-windows-forms.md)
- [<span data-ttu-id="f9490-114">Herança Visual dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f9490-114">Windows Forms Visual Inheritance</span></span>](windows-forms-visual-inheritance.md)
