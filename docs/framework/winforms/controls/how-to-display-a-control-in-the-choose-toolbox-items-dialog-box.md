---
title: 'Como: Exibir um controle na caixa de diálogo de itens de caixa de ferramentas de escolha'
ms.date: 03/30/2017
helpviewer_keywords:
- global assembly cache [Windows Forms], Choose Toolbox Items dialog box
- AssemblyFoldersEx [Windows Forms], Choose Toolbox Items dialog box
- controls [Windows Forms], display in Choose Toolbox Items dialog box
- assembly folder registration [Windows Forms], Choose Toolbox Items dialog box
- Choose Toolbox Items dialog box [Windows Forms], display control
ms.assetid: 01ef6eba-d044-40f0-951d-78eff7ebd9a9
ms.openlocfilehash: 3893859071b49c2ce0a01ca9d31fbee4474f21c9
ms.sourcegitcommit: 07c4368273b446555cb2c85397ea266b39d5fe50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56583150"
---
# <a name="how-to-display-a-control-in-the-choose-toolbox-items-dialog-box"></a>Como: Exibir um controle na caixa de diálogo de itens de caixa de ferramentas de escolha
Ao desenvolver e distribuir controles, é possível fazer com que esses controles apareçam na caixa de diálogo **Escolher itens da caixa de ferramentas** que é exibida quando você clica com o botão direito do mouse na **Caixa de ferramentas** e seleciona **Escolher itens**. Você pode permitir que seu controle apareça na caixa de diálogo usando o procedimento de registro AssemblyFoldersEx.  
  
### <a name="to-display-your-control-in-the-choose-toolbox-items-dialog-box"></a>Para exibir o controle na caixa de diálogo Escolher itens da caixa de ferramentas  
  
-   Instale o assembly do controle no cache de assembly global. Para obter mais informações, confira [Como: Instalar um assembly no cache de assembly global](../../../../docs/framework/app-domains/how-to-install-an-assembly-into-the-gac.md)  
  
     -ou-  
  
-   Registre o controle e assemblies de tempo de design associados usando o procedimento de registro AssemblyFoldersEx. AssemblyFoldersEx é um local de Registro em que os fornecedores de terceiros armazenam caminhos para cada versão da estrutura à qual dão suporte. A resolução de tempo de design pode procurar neste local do Registro para localizar assemblies de referência. O script de Registro pode especificar os controles que deseja que apareçam na caixa de ferramentas. Para obter mais informações, consulte [Implantando um controle personalizado e Assemblies de tempo de Design](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ee849818(v=vs.100)).  
  
## <a name="see-also"></a>Consulte também
- [Caixa de diálogo Escolher Itens da Caixa de Ferramentas (Visual Studio)](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/dyca0t6t(v=vs.100))
- [Implantando um controle personalizado e Assemblies de tempo de Design](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ee849818(v=vs.100))
- [Desenvolvendo controles dos Windows Forms em tempo de design](../../../../docs/framework/winforms/controls/developing-windows-forms-controls-at-design-time.md)
- [Como: Instalar um assembly no cache de assembly global](../../../../docs/framework/app-domains/how-to-install-an-assembly-into-the-gac.md)
- [Passo a passo: Preenchendo automaticamente a caixa de ferramentas com componentes personalizados](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md)
