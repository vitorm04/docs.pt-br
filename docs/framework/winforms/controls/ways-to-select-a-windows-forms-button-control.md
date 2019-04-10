---
title: Forma de selecionar um controle de botão dos Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- Button control [Windows Forms], selecting
ms.assetid: fe2fc058-5118-4f70-b264-6147d64a7a8d
ms.openlocfilehash: f2881646a05d257044c6461f822a4c35a225f8c8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59223284"
---
# <a name="ways-to-select-a-windows-forms-button-control"></a>Forma de selecionar um controle de botão dos Windows Forms
Um botão dos Windows Forms pode ser selecionado das seguintes maneiras:  
  
-   Use um mouse para clicar no botão.  
  
-   Invocar o botão <xref:System.Windows.Forms.Control.Click> evento no código.  
  
-   Mova o foco para o botão pressionando a tecla TAB e, em seguida, escolha o botão pressionando a barra de espaços ou ENTER.  
  
-   Pressione a tecla de acesso (ALT + a letra sublinhada) para o botão. Para obter mais informações sobre chaves de acesso, consulte [como: Criar chaves de acesso para controles do Windows Forms](how-to-create-access-keys-for-windows-forms-controls.md).  
  
-   Se o botão for o botão "Aceitar" do formulário, pressionar ENTER seleciona o botão, mesmo se outro controle tiver o foco — exceto se o outro controle for outro botão, uma caixa de texto de várias linhas ou um controle personalizado que intercepte a tecla enter.  
  
-   Se o botão for o botão "Cancelar" do formulário, pressionar ESC seleciona o botão, mesmo se outro controle tiver o foco.  
  
-   Chamar o <xref:System.Windows.Forms.Button.PerformClick%2A> método para selecionar o botão programaticamente.  
  
## <a name="see-also"></a>Consulte também

- [Visão geral do controle de botão](button-control-overview-windows-forms.md)
- [Como: Responder a cliques no botão do Windows Forms](how-to-respond-to-windows-forms-button-clicks.md)
- [Controle de botão](button-control-windows-forms.md)
