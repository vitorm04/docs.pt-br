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
# <a name="a-startup-form-has-not-been-specified"></a>Não foi especificado um formulário de inicialização

O aplicativo usa a classe <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>, mas não especifica o formulário de inicialização.  
  
 Isso pode ocorrer se a caixa de seleção **habilitar estrutura de aplicativo** estiver marcada no designer de projeto, mas o **formulário de inicialização** não for especificado. Para obter mais informações, consulte [Página de aplicativo, Designer de Projeto (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1. Especifique um objeto de inicialização para o aplicativo.  
  
     Para obter mais informações, consulte [Página de aplicativo, Designer de Projeto (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).  
  
2. Substitua o método <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateMainForm%2A> para definir a propriedade <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MainForm%2A> como o formulário de inicialização.  
  
## <a name="see-also"></a>Consulte também

- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateMainForm%2A>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MainForm%2A>
- [Visão geral do modelo de aplicativo do Visual Basic](../../../visual-basic/developing-apps/development-with-my/overview-of-the-visual-basic-application-model.md)
