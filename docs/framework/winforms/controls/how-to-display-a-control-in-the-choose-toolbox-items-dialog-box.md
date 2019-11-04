---
title: Como exibir um controle na caixa de diálogo Escolher Itens da Caixa de Ferramentas
ms.date: 08/23/2019
helpviewer_keywords:
- global assembly cache [Windows Forms], Choose Toolbox Items dialog box
- AssemblyFoldersEx [Windows Forms], Choose Toolbox Items dialog box
- controls [Windows Forms], display in Choose Toolbox Items dialog box
- assembly folder registration [Windows Forms], Choose Toolbox Items dialog box
- Choose Toolbox Items dialog box [Windows Forms], display control
ms.assetid: 01ef6eba-d044-40f0-951d-78eff7ebd9a9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: db4b3ac020e967a6a0c291103d825ac71cebda23
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458276"
---
# <a name="how-to-display-a-control-in-the-choose-toolbox-items-dialog-box"></a>Como exibir um controle na caixa de diálogo Escolher Itens da Caixa de Ferramentas

À medida que desenvolver e distribuir controles, talvez você queira que esses controles apareçam na caixa de diálogo **escolher itens da Toolbox** do Visual Studio, que é exibido quando você clica com o botão direito do mouse na **Toolbox** e seleciona **escolher itens**. Você pode permitir que seu controle apareça na caixa de diálogo usando o procedimento de registro AssemblyFoldersEx.

Para exibir seu controle na caixa de diálogo escolher itens de caixa de ferramentas:

- Instale o assembly do controle no cache de assembly global. Para obter mais informações, consulte [Como instalar um assembly no cache de assembly global](../../app-domains/install-assembly-into-gac.md).

  \- ou -

- Registre o controle e assemblies de tempo de design associados usando o procedimento de registro AssemblyFoldersEx. AssemblyFoldersEx é um local de Registro em que os fornecedores de terceiros armazenam caminhos para cada versão da estrutura à qual dão suporte. A resolução de tempo de design pode procurar neste local do Registro para localizar assemblies de referência. O script de Registro pode especificar os controles que deseja que apareçam na caixa de ferramentas.

## <a name="see-also"></a>Consulte também

- [Desenvolvendo controles dos Windows Forms em tempo de design](developing-windows-forms-controls-at-design-time.md)
- [Como instalar um assembly no cache de assembly global](../../app-domains/install-assembly-into-gac.md)
- [Instruções passo a passo: preenchendo de forma automática a caixa de ferramentas com componentes personalizados](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)
