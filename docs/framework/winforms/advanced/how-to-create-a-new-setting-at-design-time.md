---
title: 'Como: criar uma nova configuração em tempo de design'
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], design time
- application settings [Windows Forms], creating
ms.assetid: c5d60a66-6507-462f-a81f-e3bc0a804e16
ms.openlocfilehash: 35a7cd8cc1daaf76a25977751ddc9ec0709e5947
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69037899"
---
# <a name="how-to-create-a-new-setting-at-design-time"></a>Como: Criar uma nova configuração em tempo de design

Você pode criar uma nova configuração no tempo de design usando o Settings designer no Visual Studio. O designer de configurações é uma interface de estilo de grade que permite criar novas configurações e especificar propriedades para essas configurações. Você deve especificar nome, valor, tipo e escopo para as novas configurações. Quando uma configuração é criada, ela é acessível no código.

## <a name="create-a-new-setting-at-design-time-in-c"></a>Criar uma nova configuração em tempo de design em C\#

1. Abra o Visual Studio.

2. Em **Gerenciador de soluções**, expanda o nó **Propriedades** do seu projeto.

3. Clique duas vezes no arquivo. Settings no qual você deseja adicionar uma nova configuração. O nome padrão para esse arquivo é Settings. Settings.

4. No designer de configurações, defina o **nome**, o **valor**, o **tipo**e o **escopo** da sua configuração. Cada linha representa uma única configuração.

## <a name="create-a-new-setting-at-design-time-in-visual-basic"></a>Criar uma nova configuração em tempo de design no Visual Basic

1. Abra o Visual Studio.

2. Em **Gerenciador de soluções**, clique com o botão direito do mouse no nó do projeto e escolha **Propriedades**.

3. Na página **Propriedades** , selecione a guia **configurações** .

4. No designer de configurações, defina o **nome**, o **valor**, o **tipo**e o **escopo** da sua configuração. Cada linha representa uma única configuração.

## <a name="see-also"></a>Consulte também

- [Usando configurações do aplicativo e configurações do usuário](using-application-settings-and-user-settings.md)
- [Visão Geral das Configurações do Aplicativo](application-settings-overview.md)
- [Como: Alterar o valor de uma configuração existente no tempo de design](how-to-change-the-value-of-an-existing-setting-at-design-time.md)
