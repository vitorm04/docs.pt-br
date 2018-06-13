---
title: Efeitos da modificação de um formulário Base&#39;s aparência
ms.date: 03/30/2017
helpviewer_keywords:
- parent forms [Windows Forms]
- inherited forms [Windows Forms], modifications to base form
- Windows Forms, base form appearance
- base forms
- inheritance [Windows Forms], forms
ms.assetid: 1c3f2b29-a05c-4c6f-aa1a-4e66b94f343a
ms.openlocfilehash: 7ba4a78395bb93caa1d1d86dc135825ca2a58845
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33520546"
---
# <a name="effects-of-modifying-a-base-form39s-appearance"></a><span data-ttu-id="38ace-102">Efeitos da modificação de um formulário Base&#39;s aparência</span><span class="sxs-lookup"><span data-stu-id="38ace-102">Effects of Modifying a Base Form&#39;s Appearance</span></span>
<span data-ttu-id="38ace-103">Durante o desenvolvimento de aplicativo, geralmente você precisará alterar a aparência do formulário base do qual outros formulários no projeto (ou em outros projetos) são herdadas.</span><span class="sxs-lookup"><span data-stu-id="38ace-103">During application development, you may often need to change the appearance of the base form from which other forms in the project (or in other projects) are inheriting.</span></span>  
  
 <span data-ttu-id="38ace-104">Em tempo de design, altera a aparência do formulário base (seja a configuração das propriedades ou a adição e subtração de controles) são refletidas nos formulários herdados quando o projeto que contém o formulário base é criado.</span><span class="sxs-lookup"><span data-stu-id="38ace-104">At design time, changes to the base form's appearance (be it the setting of properties or the addition and subtraction of controls) are reflected on inherited forms when the project containing the base form is built.</span></span> <span data-ttu-id="38ace-105">Não é suficiente para que você simplesmente salve as alterações para o formulário base.</span><span class="sxs-lookup"><span data-stu-id="38ace-105">It is not sufficient for you to simply save the changes to the base form.</span></span> <span data-ttu-id="38ace-106">Para criar um projeto, escolha **criar** do **criar** menu.</span><span class="sxs-lookup"><span data-stu-id="38ace-106">To build a project, choose **Build** from the **Build** menu.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="38ace-107">As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas.</span><span class="sxs-lookup"><span data-stu-id="38ace-107">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="38ace-108">Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="38ace-108">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="38ace-109">Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="38ace-109">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
 <span data-ttu-id="38ace-110">As modificações feitas no formulário base no tempo de execução tem afetam formulários herdados que já são instanciados.</span><span class="sxs-lookup"><span data-stu-id="38ace-110">Modifications made to the base form at run time have no affect on inherited forms that are already instantiated.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38ace-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="38ace-111">See Also</span></span>  
 [<span data-ttu-id="38ace-112">base</span><span class="sxs-lookup"><span data-stu-id="38ace-112">base</span></span>](~/docs/csharp/language-reference/keywords/base.md)  
 [<span data-ttu-id="38ace-113">Como Herdar Windows Forms</span><span class="sxs-lookup"><span data-stu-id="38ace-113">How to: Inherit Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-inherit-windows-forms.md)  
 [<span data-ttu-id="38ace-114">Herança Visual dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="38ace-114">Windows Forms Visual Inheritance</span></span>](../../../../docs/framework/winforms/advanced/windows-forms-visual-inheritance.md)
