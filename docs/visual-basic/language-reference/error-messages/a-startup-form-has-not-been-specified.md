---
title: Não foi especificado um formulário de inicialização
ms.date: 07/20/2015
f1_keywords:
- vbrAppModel_NoStartupForm
ms.assetid: 8e04af49-4bef-49de-a7ec-e407e9873da7
ms.openlocfilehash: f05358f76829768d8ff5c4ac85b5134f35254126
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54627207"
---
# <a name="a-startup-form-has-not-been-specified"></a>Não foi especificado um formulário de inicialização
O aplicativo usa o <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase> classe, mas não especifica o formulário de inicialização.  
  
 Isso pode ocorrer se o **habilitar estrutura de aplicativo** caixa de seleção está selecionada no designer de projeto, mas o **formulário de inicialização** não for especificado. Para obter mais informações, consulte [Página de aplicativo, Designer de Projeto (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Especifique um objeto de inicialização para o aplicativo.  
  
     Para obter mais informações, consulte [Página de aplicativo, Designer de Projeto (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).  
  
2.  Substituir a <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateMainForm%2A> método para definir o <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MainForm%2A> propriedade para o formulário de inicialização.  
  
## <a name="see-also"></a>Consulte também
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateMainForm%2A>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MainForm%2A>
- [Visão geral do modelo de aplicativo do Visual Basic](../../../visual-basic/developing-apps/development-with-my/overview-of-the-visual-basic-application-model.md)
