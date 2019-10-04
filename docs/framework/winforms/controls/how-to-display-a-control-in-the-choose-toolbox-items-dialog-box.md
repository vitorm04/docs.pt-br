---
title: 'Como: Exibir um controle na caixa de diálogo Escolher Itens da Caixa de Ferramentas'
ms.date: 08/23/2019
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
ms.openlocfilehash: 86ec8f9ae76f010ebbc3be393d8d257ba5cfc6b6
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834619"
---
# <a name="how-to-display-a-control-in-the-choose-toolbox-items-dialog-box"></a>Como: Exibir um controle na caixa de diálogo Escolher Itens da Caixa de Ferramentas

À medida que desenvolver e distribuir controles, talvez você queira que esses controles apareçam na caixa de diálogo **escolher itens da Toolbox** do Visual Studio, que é exibido quando você clica com o botão direito do mouse na **Toolbox** e seleciona **escolher itens**. Você pode permitir que seu controle apareça na caixa de diálogo usando o procedimento de registro AssemblyFoldersEx.

Para exibir seu controle na caixa de diálogo escolher itens de caixa de ferramentas:

- Instale o assembly do controle no cache de assembly global. Para obter mais informações, confira [Como: Instalar um assembly no cache de assembly global](../../app-domains/install-assembly-into-gac.md).

  - ou -

- Registre o controle e assemblies de tempo de design associados usando o procedimento de registro AssemblyFoldersEx. AssemblyFoldersEx é um local de Registro em que os fornecedores de terceiros armazenam caminhos para cada versão da estrutura à qual dão suporte. A resolução de tempo de design pode procurar neste local do Registro para localizar assemblies de referência. O script de Registro pode especificar os controles que deseja que apareçam na caixa de ferramentas.

## <a name="see-also"></a>Consulte também

- [Desenvolvendo controles dos Windows Forms em tempo de design](developing-windows-forms-controls-at-design-time.md)
- [Como: Instalar um assembly no cache de assembly global](../../app-domains/install-assembly-into-gac.md)
- [Passo a passo: Populando automaticamente a caixa de ferramentas com componentes personalizados](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)
