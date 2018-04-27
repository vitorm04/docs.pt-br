---
title: Como definir o comportamento de redimensionamento e posicionamento em uma janela dividida
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- split windows [Windows Forms], resizing
- splitter windows [Windows Forms], resizing
- SplitContainer control [Windows Forms], resizing
ms.assetid: 9bf73f36-ed2d-4a02-b15a-0770eff4fdfa
caps.latest.revision: 13
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e62091addfb64c287154b190f02caf1600533b3b
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-define-resize-and-positioning-behavior-in-a-split-window"></a>Como definir o comportamento de redimensionamento e posicionamento em uma janela dividida
Os painéis do <xref:System.Windows.Forms.SplitContainer> controle se prestam a que está sendo redimensionada e manipulados pelos usuários. No entanto, há momentos em que é útil controlar o divisor com programação, onde ele está posicionado e em que grau pode ser movido.  
  
 O <xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A> propriedade e as outras propriedades de <xref:System.Windows.Forms.SplitContainer> proporciona controle preciso sobre o comportamento da interface do usuário para atender às suas necessidades. Tais propriedades são listadas na tabela a seguir.  
  
|Nome|Descrição|  
|----------|-----------------|  
|Propriedade <xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A>|Determina se o divisor pode ser movido com o teclado ou mouse.|  
|Propriedade <xref:System.Windows.Forms.SplitContainer.SplitterDistance%2A>|Determina a distância em pixels da borda esquerda ou superior para o divisor móvel.|  
|Propriedade <xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A>|Determina a distância mínima, em pixels, que o divisor pode ser movido pelo usuário.|  
  
 O exemplo a seguir modifica o <xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A> propriedade para criar um efeito "ajuste divisor"; quando o usuário arrasta o divisor, ele é incrementado em unidades de 10 pixels em vez do padrão 1.  
  
### <a name="to-define-splitcontainer-resize-behavior"></a>Definir o comportamento de redimensionamento do SplitContainer  
  
1.  Em um procedimento, defina o <xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A> propriedade para o tamanho desejado, para que o comportamento do separador 'Ajuste' é obtido.  
  
     No seguinte exemplo de código, dentro do formulário <xref:System.Windows.Forms.Form.Load> evento, o separador de dentro do <xref:System.Windows.Forms.SplitContainer> controle está definido para 10 pixels quando arrastado de salto.  
  
    ```vb  
    Private Sub Form1_Load(ByVal sender As System.Object, _  
        ByVal e As System.EventArgs) Handles MyBase.Load  
        Dim splitSnapper as new SplitContainer()  
        splitSnapper.SplitterIncrement = 10  
        splitSnapper.Dock = DockStyle.Fill  
        splitSnapper.Parent = me  
    End Sub  
    ```  
  
    ```csharp  
    private void Form1_Load(System.Object sender, System.EventArgs e)  
    {  
        SplitContainer splitSnapper = new SplitContainer();  
        splitSnapper.SplitterIncrement = 10;  
        splitSnapper.Dock = DockStyle.Fill;  
        splitSnapper.Parent = this;  
    }  
    ```  
  
     (Visual c#) Coloque o seguinte código no construtor do formulário para registrar o manipulador de eventos.  
  
    ```csharp  
    this.Load += new System.EventHandler(this.Form1_Load);  
    ```  
  
     Mover o divisor ligeiramente para a esquerda ou direita não terá nenhum efeito; no entanto, quando o ponteiro do mouse se move em 10 pixels em qualquer direção, o divisor se ajustará à nova posição.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.SplitContainer>  
 <xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A>
