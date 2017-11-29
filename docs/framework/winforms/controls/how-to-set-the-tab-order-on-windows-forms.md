---
title: "Como definir a ordem de tabulação nos Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- TabStop
- TabIndex
helpviewer_keywords:
- tab order [Windows Forms], controls on Windows forms
- Windows Forms controls, setting tab order
- controls [Windows Forms], setting tab order
- Windows Forms, setting tab order
ms.assetid: 71fa8e76-0472-414b-ad3c-0f90166e0ad7
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a7acca633a5a2b98d7c4b6dd64355996e763d6df
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-set-the-tab-order-on-windows-forms"></a>Como definir a ordem de tabulação nos Windows Forms
A ordem de tabulação é a ordem em que um usuário move o foco de um controle para outro pressionando a tecla TAB. Cada formulário tem sua própria ordem de tabulação. Por padrão, a ordem de tabulação é igual à ordem em que você criou os controles. A numeração da ordem de tabulação começa com zero.  
  
> [!NOTE]
>  As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas. Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**. Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-set-the-tab-order-of-a-control"></a>Para definir a ordem de tabulação de um controle  
  
1.  No menu **Exibir**, clique em **Ordem de Tabulação**.  
  
     Isso ativa o modo de seleção de ordem de tabulação do formulário. Um número (que representa o <xref:System.Windows.Forms.Control.TabIndex%2A> propriedade) é exibido no canto superior esquerdo de cada controle.  
  
2.  Clique nos controles sequencialmente para estabelecer a ordem de tabulação desejada.  
  
    > [!NOTE]
    >  Local do controle na ordem de tabulação pode ser definido como qualquer valor maior ou igual a 0. Quando ocorrem duplicatas, a ordem z dos dois controles é avaliada e o controle na parte superior é tabulado primeiro. (A ordem z consiste na disposição em camadas visuais de controles em um formulário ao longo do eixo z do formulário [profundidade]. A ordem z determina quais controles estão na frente de outros controles.) Para obter mais informações sobre a ordem z, consulte [Colocando objetos em camadas nos Windows Forms](../../../../docs/framework/winforms/controls/how-to-layer-objects-on-windows-forms.md).  
  
3.  Quando você tiver terminado, clique em **Ordem de Tabulação** no menu **Exibir** novamente para sair do modo de ordem de tabulação.  
  
    > [!NOTE]
    >  Controles que não é possível obter o foco, bem como controles invisíveis e desativados, não tem um <xref:System.Windows.Forms.Control.TabIndex%2A> propriedade e são não incluídos na ordem de tabulação. Conforme um usuário pressiona a tecla TAB, esses controles são ignorados.  
  
 Como alternativa, ordem de tabulação pode ser definida na janela de propriedades usando o <xref:System.Windows.Forms.Control.TabIndex%2A> propriedade. O <xref:System.Windows.Forms.Control.TabIndex%2A> propriedade de um controle determina onde é posicionado na ordem de tabulação. Por padrão, o primeiro controle desenhado tem um <xref:System.Windows.Forms.Control.TabIndex%2A> valor de 0, o segundo tem um <xref:System.Windows.Forms.Control.TabIndex%2A> de 1 e assim por diante.  
  
 Além disso, por padrão, um <xref:System.Windows.Forms.GroupBox> controle tem seu próprio <xref:System.Windows.Forms.Control.TabIndex%2A> valor, que é um número inteiro. Um <xref:System.Windows.Forms.GroupBox> controle em si não pode ter o foco em tempo de execução. Assim, cada controle dentro de um <xref:System.Windows.Forms.GroupBox> tem seu próprio decimal <xref:System.Windows.Forms.Control.TabIndex%2A> valor, começando com.0. Naturalmente, como o <xref:System.Windows.Forms.Control.TabIndex%2A> de um <xref:System.Windows.Forms.GroupBox> controle é aumentado, os controles dentro dele serão incrementados adequadamente. Se você tiver alterado um <xref:System.Windows.Forms.Control.TabIndex%2A> valor de 5 a 6, o <xref:System.Windows.Forms.Control.TabIndex%2A> altera automaticamente o valor do primeiro controle em seu grupo 6.0, e assim por diante.  
  
 Por fim, qualquer controle dos muitos no seu formulário podem ser ignorados na ordem de tabulação. Geralmente, pressionar TAB sucessivamente no tempo de execução seleciona cada controle na ordem de tabulação. Desativando o <xref:System.Windows.Forms.Control.TabStop%2A> propriedade, você pode fazer um controle passa na ordem de tabulação do formulário.  
  
#### <a name="to-remove-a-control-from-the-tab-order"></a>Para remover um controle da ordem de tabulação  
  
1.  Definir o controle <xref:System.Windows.Forms.Control.TabStop%2A> propriedade `false` na janela Propriedades.  
  
     Um controle cuja <xref:System.Windows.Forms.Control.TabStop%2A> propriedade foi definida `false` ainda mantém sua posição na ordem de tabulação, mesmo que o controle é ignorado quando você percorrer os controles com a tecla TAB.  
  
    > [!NOTE]
    >  Um grupo de botões de opção tem uma única parada de tabulação no tempo de execução. O botão selecionado (ou seja, o botão com seu <xref:System.Windows.Forms.RadioButton.Checked%2A> propriedade definida como `true`) tem seu <xref:System.Windows.Forms.Control.TabStop%2A> propriedade é definida automaticamente como `true`, enquanto os outros botões têm seus <xref:System.Windows.Forms.Control.TabStop%2A> propriedade definida como `false`. Para obter mais informações sobre agrupamento <xref:System.Windows.Forms.RadioButton> controles, consulte [agrupamento RadioButton controles dos Windows Forms para funcionar como um conjunto](../../../../docs/framework/winforms/controls/how-to-group-windows-forms-radiobutton-controls-to-function-as-a-set.md).  
  
## <a name="see-also"></a>Consulte também  
 [Controles dos Windows Forms](../../../../docs/framework/winforms/controls/index.md)  
 [Organizando Controles nos Windows Forms](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)  
 [Controles a serem usados nos Windows Forms](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 [Controles dos Windows Forms por função](../../../../docs/framework/winforms/controls/windows-forms-controls-by-function.md)
