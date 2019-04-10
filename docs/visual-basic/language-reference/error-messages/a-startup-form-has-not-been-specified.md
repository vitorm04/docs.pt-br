---
title: Não foi especificado um formulário de inicialização
ms.date: 07/20/2015
f1_keywords:
- vbrAppModel_NoStartupForm
ms.assetid: 8e04af49-4bef-49de-a7ec-e407e9873da7
ms.openlocfilehash: 2bbae640ca65c95411cae24a9506fe2076b62cba
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59296466"
---
# <a name="a-startup-form-has-not-been-specified"></a><span data-ttu-id="48860-102">Não foi especificado um formulário de inicialização</span><span class="sxs-lookup"><span data-stu-id="48860-102">A startup form has not been specified</span></span>
<span data-ttu-id="48860-103">O aplicativo usa o <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase> classe, mas não especifica o formulário de inicialização.</span><span class="sxs-lookup"><span data-stu-id="48860-103">The application uses the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase> class but does not specify the startup form.</span></span>  
  
 <span data-ttu-id="48860-104">Isso pode ocorrer se o **habilitar estrutura de aplicativo** caixa de seleção está selecionada no designer de projeto, mas o **formulário de inicialização** não for especificado.</span><span class="sxs-lookup"><span data-stu-id="48860-104">This can occur if the **Enable application framework** check box is selected in the project designer but the **Startup form** is not specified.</span></span> <span data-ttu-id="48860-105">Para obter mais informações, consulte [Página de aplicativo, Designer de Projeto (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="48860-105">For more information, see [Application Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="48860-106">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="48860-106">To correct this error</span></span>  
  
1. <span data-ttu-id="48860-107">Especifique um objeto de inicialização para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="48860-107">Specify a startup object for the application.</span></span>  
  
     <span data-ttu-id="48860-108">Para obter mais informações, consulte [Página de aplicativo, Designer de Projeto (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="48860-108">For more information, see [Application Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).</span></span>  
  
2. <span data-ttu-id="48860-109">Substituir a <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateMainForm%2A> método para definir o <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MainForm%2A> propriedade para o formulário de inicialização.</span><span class="sxs-lookup"><span data-stu-id="48860-109">Override the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateMainForm%2A> method to set the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MainForm%2A> property to the startup form.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48860-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="48860-110">See also</span></span>

- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateMainForm%2A>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MainForm%2A>
- [<span data-ttu-id="48860-111">Visão geral do modelo de aplicativo do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="48860-111">Overview of the Visual Basic Application Model</span></span>](../../../visual-basic/developing-apps/development-with-my/overview-of-the-visual-basic-application-model.md)
