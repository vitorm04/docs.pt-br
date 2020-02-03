---
title: bloquear controles
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms controls, locking
- controls [Windows Forms], locking
ms.assetid: 94efe0d2-c14e-4d14-b903-63ea9b07e290
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 16eb151dc435614e1edc82bf9f0acf3974f36690
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76736238"
---
# <a name="how-to-lock-controls-to-windows-forms"></a>Como bloquear controles para Windows Forms

Ao projetar a interface do usuário do seu aplicativo do Windows, você pode bloquear os controles quando eles são posicionados corretamente, para que você não os mova nem os redimensione inadvertidamente ao configurar outras propriedades.

Além disso, você pode bloquear e desbloquear todos os controles no formulário de uma vez, o que é útil para formulários com muitos controles ou você pode desbloquear controles individuais. Depois de colocar todos os controles no local desejado no formulário, bloqueie-os no local para evitar a movimentação incorreta.

## <a name="to-lock-a-control"></a>Para bloquear um controle

Na janela **Propriedades** do Visual Studio, selecione a propriedade **bloqueado** e, em seguida, selecione **verdadeiro**. (Clicar duas vezes no nome alterna a configuração da propriedade.)

Como alternativa, clique com o botão direito do mouse no controle e escolha **Bloquear Controles**.

> [!NOTE]
> O bloqueio dos controles evita que eles sejam arrastados para um novo tamanho ou local na superfície de design. No entanto, você ainda pode alterar o tamanho ou local dos controles por meio da janela **Propriedades** ou no código.

## <a name="to-lock-all-the-controls-on-a-form"></a>Para bloquear todos os controles em um formulário

No menu **Formatar**, escolha **Bloquear Controles**.

> [!NOTE]
> Esse comando bloqueia também o tamanho do formulário, pois um formulário é um controle.

## <a name="to-unlock-all-locked-controls-on-a-form"></a>Para desbloquear todos os controles bloqueados em um formulário

No menu **Formatar**, escolha **Bloquear Controles**.

Todos os controles bloqueados anteriormente no formulário agora estão desbloqueados.

## <a name="to-unlock-locked-controls-individually"></a>Para desbloquear controles bloqueados individualmente

Na janela **Propriedades** , selecione a propriedade **bloqueado** e, em seguida, selecione **falso**. (Clicar duas vezes no nome alterna a configuração da propriedade.)

## <a name="see-also"></a>Consulte também

- [Controles dos Windows Forms](index.md)
- [Rotulando controles individuais dos Windows Forms e fornecendo atalhos para eles](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [Controles a serem usados no Windows Forms](controls-to-use-on-windows-forms.md)
- [Controles dos Windows Forms por função](windows-forms-controls-by-function.md)
