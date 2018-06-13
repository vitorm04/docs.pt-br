---
title: Como colocar objetos em camadas nos Windows Forms
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms controls, layering
- controls [Windows Forms], layering
- z order
- controls [Windows Forms], positioning
- z-order
ms.assetid: 1acc4281-2976-4715-86f4-bda68134baaf
ms.openlocfilehash: 1a2a25f2e7eaa6618c0bf535a34f7dc6a28d51fa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33533680"
---
# <a name="how-to-layer-objects-on-windows-forms"></a>Como colocar objetos em camadas nos Windows Forms
Ao criar uma interface do usuário complexa ou trabalhar com um formulário MDI (interface de múltiplos documentos), geralmente se deseja dispor em camadas controles e formulários filho para criar interfaces do usuário (UI) mais complexas. Para mover e acompanhar os controles e janelas no contexto de um grupo, manipule a ordem z. A *ordem z* consiste na disposição em camadas visuais de controles em um formulário ao longo do eixo z do formulário (profundidade). A janela na parte superior da ordem z se sobrepõe a todas as outras janelas. Todas as outras janelas se sobrepõe a janela na parte inferior da ordem z.  
  
> [!NOTE]
>  As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas. Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**. Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-layer-controls-at-design-time"></a>Dispondo controles em camadas no design time  
  
1.  Selecione o controle que deseja dispor em camadas.  
  
2.  No menu **Formato**, aponte para **Pedido** e depois clique em **Trazer para frente** ou **Enviar para trás**.  
  
### <a name="to-layer-controls-programmatically"></a>Dispondo controles em camadas de forma programática  
  
-   Use o <xref:System.Windows.Forms.Control.BringToFront%2A> e <xref:System.Windows.Forms.Control.SendToBack%2A> métodos para manipular a ordem z dos controles.  
  
     Por exemplo, se um <xref:System.Windows.Forms.TextBox> controle, `txtFirstName`, é sob outro controle e quiser que ele seja visível, use o seguinte código:  
  
    ```vb  
    txtFirstName.BringToFront()  
    ```  
  
    ```csharp  
    txtFirstName.BringToFront();  
    ```  
  
    ```cpp  
    txtFirstName->BringToFront();  
    ```  
  
> [!NOTE]
>  Windows Forms dá suporte a *Contenção de controle*. Contenção de controle envolve colocar um número de controles em um controle que contém, como um número de <xref:System.Windows.Forms.RadioButton> controla dentro de um <xref:System.Windows.Forms.GroupBox> controle. Em seguida, é possível dispor os controles em camadas no controle de contenção. Mover a caixa de grupo move também os controles, já que estes estão contidos dentro dela.  
  
## <a name="see-also"></a>Consulte também  
 [Controles dos Windows Forms](../../../../docs/framework/winforms/controls/index.md)  
 [Organizando Controles nos Windows Forms](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)  
 [Rotulando controles individuais dos Windows Forms e fornecendo atalhos para eles](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)  
 [Controles a serem usados nos Windows Forms](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 [Controles dos Windows Forms por função](../../../../docs/framework/winforms/controls/windows-forms-controls-by-function.md)
