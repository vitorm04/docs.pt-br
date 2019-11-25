---
title: Não foi especificado um formulário de inicialização
ms.date: 07/20/2015
f1_keywords:
- vbrAppModel_NoStartupForm
ms.assetid: 8e04af49-4bef-49de-a7ec-e407e9873da7
ms.openlocfilehash: 301f249e6222c929d2c513964ecbb21df5fbc47f
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73976186"
---
# <a name="a-startup-form-has-not-been-specified"></a><span data-ttu-id="8e1f7-102">Não foi especificado um formulário de inicialização</span><span class="sxs-lookup"><span data-stu-id="8e1f7-102">A startup form has not been specified</span></span>

<span data-ttu-id="8e1f7-103">O aplicativo usa a classe <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>, mas não especifica o formulário de inicialização.</span><span class="sxs-lookup"><span data-stu-id="8e1f7-103">The application uses the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase> class but does not specify the startup form.</span></span>  
  
 <span data-ttu-id="8e1f7-104">Isso pode ocorrer se a caixa de seleção **habilitar estrutura de aplicativo** estiver marcada no designer de projeto, mas o **formulário de inicialização** não for especificado.</span><span class="sxs-lookup"><span data-stu-id="8e1f7-104">This can occur if the **Enable application framework** check box is selected in the project designer but the **Startup form** is not specified.</span></span> <span data-ttu-id="8e1f7-105">Para obter mais informações, consulte [Página de aplicativo, Designer de Projeto (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="8e1f7-105">For more information, see [Application Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="8e1f7-106">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="8e1f7-106">To correct this error</span></span>  
  
1. <span data-ttu-id="8e1f7-107">Especifique um objeto de inicialização para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8e1f7-107">Specify a startup object for the application.</span></span>  
  
     <span data-ttu-id="8e1f7-108">Para obter mais informações, consulte [Página de aplicativo, Designer de Projeto (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="8e1f7-108">For more information, see [Application Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).</span></span>  
  
2. <span data-ttu-id="8e1f7-109">Substitua o método <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateMainForm%2A> para definir a propriedade <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MainForm%2A> como o formulário de inicialização.</span><span class="sxs-lookup"><span data-stu-id="8e1f7-109">Override the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateMainForm%2A> method to set the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MainForm%2A> property to the startup form.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e1f7-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8e1f7-110">See also</span></span>

- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateMainForm%2A>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MainForm%2A>
- [<span data-ttu-id="8e1f7-111">Visão geral do modelo de aplicativo do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="8e1f7-111">Overview of the Visual Basic Application Model</span></span>](../../../visual-basic/developing-apps/development-with-my/overview-of-the-visual-basic-application-model.md)
