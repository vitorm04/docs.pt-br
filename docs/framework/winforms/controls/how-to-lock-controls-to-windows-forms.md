---
title: Como bloquear controles nos Windows Forms
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Forms controls, locking
- controls [Windows Forms], locking
ms.assetid: 94efe0d2-c14e-4d14-b903-63ea9b07e290
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7f5cd70e71a4a8bc48a3240055117dadc1086a50
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-lock-controls-to-windows-forms"></a>Como bloquear controles nos Windows Forms
Ao projetar a interface do usuário do seu aplicativo do Windows, você pode bloquear os controles quando eles são posicionados corretamente, para que você não os mova nem os redimensione inadvertidamente ao configurar outras propriedades.  
  
 Além disso, você pode bloquear e desbloquear todos os controles no formulário de uma vez, o que é útil para formulários com muitos controles ou você pode desbloquear controles individuais. Depois de colocar todos os controles no local desejado no formulário, bloqueie-os no local para evitar a movimentação incorreta.  
  
> [!NOTE]
>  As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas. Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**. Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-lock-a-control"></a>Para bloquear um controle  
  
1.  Na janela **Propriedades**, clique na propriedade **Bloqueado** e selecione `true`. (Clicar duas vezes no nome alterna a configuração da propriedade.)  
  
     Como alternativa, clique com o botão direito do mouse no controle e escolha **Bloquear Controles**.  
  
    > [!NOTE]
    >  O bloqueio dos controles evita que eles sejam arrastados para um novo tamanho ou local na superfície de design. No entanto, você ainda pode alterar o tamanho ou local dos controles por meio da janela **Propriedades** ou no código.  
  
### <a name="to-lock-all-the-controls-on-a-form"></a>Para bloquear todos os controles em um formulário  
  
1.  No menu **Formatar**, escolha **Bloquear Controles**.  
  
    > [!NOTE]
    >  Esse comando bloqueia também o tamanho do formulário, pois um formulário é um controle.  
  
### <a name="to-unlock-all-locked-controls-on-a-form"></a>Para desbloquear todos os controles bloqueados em um formulário  
  
1.  No menu **Formatar**, escolha **Bloquear Controles**.  
  
     Todos os controles bloqueados anteriormente no formulário agora estão desbloqueados.  
  
### <a name="to-unlock-locked-controls-individually"></a>Para desbloquear controles bloqueados individualmente  
  
1.  Na janela **Propriedades**, clique na propriedade **Bloqueado** e selecione `false`. (Clicar duas vezes no nome alterna a configuração da propriedade.)  
  
## <a name="see-also"></a>Consulte também  
 [Controles dos Windows Forms](../../../../docs/framework/winforms/controls/index.md)  
 [Organizando Controles nos Windows Forms](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)  
 [Rotulando controles individuais dos Windows Forms e fornecendo atalhos para eles](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)  
 [Controles a serem usados nos Windows Forms](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 [Controles dos Windows Forms por função](../../../../docs/framework/winforms/controls/windows-forms-controls-by-function.md)
