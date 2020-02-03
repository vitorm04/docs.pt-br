---
title: Maneiras de selecionar um controle de botão
ms.date: 03/30/2017
helpviewer_keywords:
- Button control [Windows Forms], selecting
ms.assetid: fe2fc058-5118-4f70-b264-6147d64a7a8d
ms.openlocfilehash: 145166d182f1ec51068ab3e0c23c12b471b69231
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76740008"
---
# <a name="ways-to-select-a-windows-forms-button-control"></a>Forma de selecionar um controle de botão dos Windows Forms
Um botão dos Windows Forms pode ser selecionado das seguintes maneiras:  
  
- Use um mouse para clicar no botão.  
  
- Invocar o evento <xref:System.Windows.Forms.Control.Click> do botão no código.  
  
- Mova o foco para o botão pressionando a tecla TAB e, em seguida, escolha o botão pressionando a barra de espaços ou ENTER.  
  
- Pressione a tecla de acesso (ALT + a letra sublinhada) para o botão. Para obter mais informações sobre chaves de acesso, consulte [Como criar chaves de acesso para controles dos Windows Forms](how-to-create-access-keys-for-windows-forms-controls.md).  
  
- Se o botão for o botão "Aceitar" do formulário, pressionar ENTER seleciona o botão, mesmo se outro controle tiver o foco — exceto se o outro controle for outro botão, uma caixa de texto de várias linhas ou um controle personalizado que intercepte a tecla enter.  
  
- Se o botão for o botão "Cancelar" do formulário, pressionar ESC seleciona o botão, mesmo se outro controle tiver o foco.  
  
- Chame o método <xref:System.Windows.Forms.Button.PerformClick%2A> para selecionar o botão programaticamente.  
  
## <a name="see-also"></a>Consulte também

- [Visão geral do controle de botão](button-control-overview-windows-forms.md)
- [Como responder a cliques no botão dos Windows Forms](how-to-respond-to-windows-forms-button-clicks.md)
- [Controle de botão](button-control-windows-forms.md)
