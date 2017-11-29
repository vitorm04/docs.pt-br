---
title: Como criar um controle dos Windows Forms que mostre o progresso
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], progress tracking
- controls [Windows Forms], creating
- progress [Windows Forms], reporting [Windows Forms]
- FlashTrackBar custom control
ms.assetid: 24c5a2e3-058c-4b8d-a217-c06e6a130c2f
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 55b3879b894658c9a649004348a198d004040af3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-windows-forms-control-that-shows-progress"></a>Como criar um controle dos Windows Forms que mostre o progresso
O exemplo de código a seguir mostra um controle personalizado chamado `FlashTrackBar` que pode ser usado para mostrar ao usuário o nível ou o andamento de um aplicativo. Ele usa um gradiente para representar visualmente o progresso.  
  
 O controle `FlashTrackBar` ilustra os seguintes conceitos:  
  
-   Definindo propriedades personalizadas.  
  
-   Definindo eventos personalizados. (`FlashTrackBar` define o evento `ValueChanged`.)  
  
-   Substituindo o <xref:System.Windows.Forms.Control.OnPaint%2A> método para fornecer a lógica para desenhar o controle.  
  
-   Calculando a área disponível para desenhar o controle usando seu <xref:System.Windows.Forms.Control.ClientRectangle%2A> propriedade. `FlashTrackBar` faz isso no seu método `OptimizedInvalidate`.  
  
-   Implementação de serialização ou persistência em uma propriedade quando ela for alterada no Designer de Formulários do Windows. `FlashTrackBar` define os métodos `ShouldSerializeStartColor` e `ShouldSerializeEndColor` para serializar suas propriedades `StartColor` e `EndColor`.  
  
 A tabela a seguir mostra as propriedades personalizadas definidas por `FlashTrackBar`.  
  
|Propriedade|Descrição|  
|--------------|-----------------|  
|`AllowUserEdit`|Indica se o usuário pode alterar o valor da barra de acompanhamento dinâmica clicando nela e arrastando-a.|  
|`EndColor`|Especifica a cor final da barra de acompanhamento.|  
|`DarkenBy`|Especifica quanto a tela de fundo é escurecida em relação ao gradiente em primeiro plano.|  
|`Max`|Especifica o valor máximo da barra de acompanhamento.|  
|`Min`|Especifica o valor mínimo da barra de acompanhamento.|  
|`StartColor`|Especifica a cor inicial do gradiente.|  
|`ShowPercentage`|Indica se um percentual deve ser exibido com relação ao gradiente.|  
|`ShowValue`|Indica se o valor atual deve ser exibido com relação ao gradiente.|  
|`ShowGradient`|Indica se a barra de acompanhamento deve exibir um gradiente de cores mostrando o valor atual.|  
|-   `Value`|Especifica o valor atual da barra de acompanhamento.|  
  
 A tabela a seguir mostra os membros adicionais definidos pelo `FlashTrackBar:` o evento de propriedade alterada e o método que gera o evento.  
  
|Membro|Descrição|  
|------------|-----------------|  
|`ValueChanged`|O evento que é gerado quando a propriedade `Value` da barra de acompanhamento é alterada.|  
|`OnValueChanged`|O método que gera o evento `ValueChanged`.|  
  
> [!NOTE]
>  `FlashTrackBar`usa o <xref:System.EventArgs> classe para dados de evento e <xref:System.EventHandler> para o delegado do evento.  
  
 Para lidar com a correspondente *EventName* eventos, `FlashTrackBar` substitui os seguintes métodos que ele herda de <xref:System.Windows.Forms.Control?displayProperty=nameWithType>:  
  
-   <xref:System.Windows.Forms.Control.OnPaint%2A>  
  
-   <xref:System.Windows.Forms.Control.OnMouseDown%2A>  
  
-   <xref:System.Windows.Forms.Control.OnMouseMove%2A>  
  
-   <xref:System.Windows.Forms.Control.OnMouseUp%2A>  
  
-   <xref:System.Windows.Forms.Control.OnResize%2A>  
  
 Para manipular os eventos correspondentes da propriedade alterada, `FlashTrackBar` substitui os seguintes métodos que ele herda de <xref:System.Windows.Forms.Control?displayProperty=nameWithType>:  
  
-   <xref:System.Windows.Forms.Control.OnBackColorChanged%2A>  
  
-   <xref:System.Windows.Forms.Control.OnBackgroundImageChanged%2A>  
  
-   <xref:System.Windows.Forms.Control.OnTextChanged%2A>  
  
## <a name="example"></a>Exemplo  
 O controle `FlashTrackBar` define dois editores de tipo de interface do usuário, `FlashTrackBarValueEditor` e `FlashTrackBarDarkenByEditor`, que são mostrados nas listagens de código a seguir. A classe `HostApp` usa o controle `FlashTrackBar` em um Windows Form.  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#1)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#1)]  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBarDarkenByEditor.cs#10)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBarDarkenByEditor.vb#10)]  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBarValueEditor.cs#20)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBarValueEditor.vb#20)]  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#30](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/HostApp.cs#30)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#30](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/HostApp.vb#30)]  
  
## <a name="see-also"></a>Consulte também  
 [Estendendo o suporte ao tempo de design](http://msdn.microsoft.com/library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)  
 [Noções básicas sobre o desenvolvimento de controles dos Windows Forms](../../../../docs/framework/winforms/controls/windows-forms-control-development-basics.md)
