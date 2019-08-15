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
ms.openlocfilehash: 5239017eb63ca6360ae8811a76497256fafbd1b1
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040142"
---
# <a name="effects-of-modifying-a-base-forms-appearance"></a><span data-ttu-id="1c870-102">Efeitos da modificação da aparência de um formulário base</span><span class="sxs-lookup"><span data-stu-id="1c870-102">Effects of modifying a base form's appearance</span></span>

<span data-ttu-id="1c870-103">Durante o desenvolvimento de aplicativos, você geralmente precisa alterar a aparência do formulário base do qual outros formulários no projeto (ou em outros projetos) estão herdando.</span><span class="sxs-lookup"><span data-stu-id="1c870-103">During application development, you may often need to change the appearance of the base form from which other forms in the project (or in other projects) are inheriting.</span></span>

<span data-ttu-id="1c870-104">No momento do design, as alterações na aparência do formulário base (seja a configuração das propriedades ou a adição e a subtração de controles) são refletidas nos formulários herdados quando o projeto que contém o formulário base é criado.</span><span class="sxs-lookup"><span data-stu-id="1c870-104">At design time, changes to the base form's appearance (be it the setting of properties or the addition and subtraction of controls) are reflected on inherited forms when the project containing the base form is built.</span></span> <span data-ttu-id="1c870-105">Não é suficiente para você simplesmente salvar as alterações no formulário base.</span><span class="sxs-lookup"><span data-stu-id="1c870-105">It is not sufficient for you to simply save the changes to the base form.</span></span> <span data-ttu-id="1c870-106">Para criar um projeto, escolha **Compilar** no menu **Compilar** .</span><span class="sxs-lookup"><span data-stu-id="1c870-106">To build a project, choose **Build** from the **Build** menu.</span></span>

<span data-ttu-id="1c870-107">As modificações feitas no formulário base em tempo de execução não afetam os formulários herdados já instanciados.</span><span class="sxs-lookup"><span data-stu-id="1c870-107">Modifications made to the base form at run time have no affect on inherited forms that are already instantiated.</span></span>

## <a name="see-also"></a><span data-ttu-id="1c870-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1c870-108">See also</span></span>

- [<span data-ttu-id="1c870-109">base</span><span class="sxs-lookup"><span data-stu-id="1c870-109">base</span></span>](~/docs/csharp/language-reference/keywords/base.md)
- [<span data-ttu-id="1c870-110">Como: Herdar Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1c870-110">How to: Inherit Windows Forms</span></span>](how-to-inherit-windows-forms.md)
- [<span data-ttu-id="1c870-111">Herança Visual dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1c870-111">Windows Forms Visual Inheritance</span></span>](windows-forms-visual-inheritance.md)
