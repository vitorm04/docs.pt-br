---
title: Como exibir um controle na caixa de diálogo Escolher Itens da Caixa de Ferramentas
ms.date: 03/30/2017
helpviewer_keywords:
- global assembly cache [Windows Forms], Choose Toolbox Items dialog box
- AssemblyFoldersEx [Windows Forms], Choose Toolbox Items dialog box
- controls [Windows Forms], display in Choose Toolbox Items dialog box
- assembly folder registration [Windows Forms], Choose Toolbox Items dialog box
- Choose Toolbox Items dialog box [Windows Forms], display control
ms.assetid: 01ef6eba-d044-40f0-951d-78eff7ebd9a9
ms.openlocfilehash: fdda72d60b0f18e76b03e9b7f05060a09763a3f7
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/03/2018
ms.locfileid: "43488255"
---
# <a name="how-to-display-a-control-in-the-choose-toolbox-items-dialog-box"></a>Como exibir um controle na caixa de diálogo Escolher Itens da Caixa de Ferramentas
Ao desenvolver e distribuir controles, é possível fazer com que esses controles apareçam na caixa de diálogo **Escolher itens da caixa de ferramentas** que é exibida quando você clica com o botão direito do mouse na **Caixa de ferramentas** e seleciona **Escolher itens**. Você pode permitir que seu controle apareça na caixa de diálogo usando o procedimento de registro AssemblyFoldersEx.  
  
### <a name="to-display-your-control-in-the-choose-toolbox-items-dialog-box"></a>Para exibir o controle na caixa de diálogo Escolher itens da caixa de ferramentas  
  
-   Instale o assembly do controle no cache de assembly global. Para obter mais informações, consulte [Como instalar um assembly no cache de assembly global](../../../../docs/framework/app-domains/how-to-install-an-assembly-into-the-gac.md)  
  
     -ou-  
  
-   Registre o controle e assemblies de tempo de design associados usando o procedimento de registro AssemblyFoldersEx. AssemblyFoldersEx é um local de Registro em que os fornecedores de terceiros armazenam caminhos para cada versão da estrutura à qual dão suporte. A resolução de tempo de design pode procurar neste local do Registro para localizar assemblies de referência. O script de Registro pode especificar os controles que deseja que apareçam na caixa de ferramentas. Para obter mais informações, consulte [Implantando um controle personalizado e assemblies de tempo de Design (Visual Studio 2013)](https://msdn.microsoft.com/library/96158eb0-b691-4ae1-9e7b-3c65a1b798cb).  
  
## <a name="see-also"></a>Consulte também  
 [Caixa de diálogo Escolher Itens da Caixa de Ferramentas (Visual Studio)](https://msdn.microsoft.com/library/bd07835f-18a8-433e-bccc-7141f65263bb)  
 [Implantando um controle personalizado e Assemblies de tempo de Design (Visual Studio 2013)](https://msdn.microsoft.com/library/96158eb0-b691-4ae1-9e7b-3c65a1b798cb)  
 [Desenvolvendo controles dos Windows Forms em tempo de design](../../../../docs/framework/winforms/controls/developing-windows-forms-controls-at-design-time.md)  
 [Como instalar um assembly no cache de assembly global](../../../../docs/framework/app-domains/how-to-install-an-assembly-into-the-gac.md)  
 [Passo a passo: preenchendo automaticamente a caixa de ferramentas com componentes personalizados](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md)
