---
title: 'Como: Exibir um controle na caixa de diálogo Escolher Itens da Caixa de Ferramentas'
ms.date: 03/30/2017
helpviewer_keywords:
- global assembly cache [Windows Forms], Choose Toolbox Items dialog box
- AssemblyFoldersEx [Windows Forms], Choose Toolbox Items dialog box
- controls [Windows Forms], display in Choose Toolbox Items dialog box
- assembly folder registration [Windows Forms], Choose Toolbox Items dialog box
- Choose Toolbox Items dialog box [Windows Forms], display control
ms.assetid: 01ef6eba-d044-40f0-951d-78eff7ebd9a9
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 9a6938b4fe651e13f3ec96642db6027143f1f028
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/24/2019
ms.locfileid: "70015889"
---
# <a name="how-to-display-a-control-in-the-choose-toolbox-items-dialog-box"></a>Como: Exibir um controle na caixa de diálogo Escolher Itens da Caixa de Ferramentas

À medida que desenvolver e distribuir controles, talvez você queira que esses controles apareçam na caixa de diálogo **escolher itens da Toolbox** do Visual Studio, que é exibido quando você clica com o botão direito do mouse na **Toolbox** e seleciona **escolher itens**. Você pode permitir que seu controle apareça na caixa de diálogo usando o procedimento de registro AssemblyFoldersEx.

Para exibir seu controle na caixa de diálogo escolher itens de caixa de ferramentas:

- Instale o assembly do controle no cache de assembly global. Para obter mais informações, confira [Como: Instalar um assembly no cache de assembly global](../../app-domains/how-to-install-an-assembly-into-the-gac.md)

  - ou -

- Registre o controle e assemblies de tempo de design associados usando o procedimento de registro AssemblyFoldersEx. AssemblyFoldersEx é um local de Registro em que os fornecedores de terceiros armazenam caminhos para cada versão da estrutura à qual dão suporte. A resolução de tempo de design pode procurar neste local do Registro para localizar assemblies de referência. O script de Registro pode especificar os controles que deseja que apareçam na caixa de ferramentas.

## <a name="see-also"></a>Consulte também

- [Desenvolvendo controles dos Windows Forms em tempo de design](developing-windows-forms-controls-at-design-time.md)
- [Como: Instalar um assembly no cache de assembly global](../../app-domains/how-to-install-an-assembly-into-the-gac.md)
- [Passo a passo: Populando automaticamente a caixa de ferramentas com componentes personalizados](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)
