---
title: 'Como: Definir a máscara de entrada'
ms.date: 03/30/2017
f1_keywords:
- net.ComponentModel.MaskPropertyEditor
helpviewer_keywords:
- MaskedTextBox control [Windows Forms]
ms.assetid: 779b3a12-cd74-4e58-b46e-04983bda5b2c
ms.openlocfilehash: 14591b313b0ba4fc2a0a30a45c693147f00050b5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59207533"
---
# <a name="how-to-set-the-input-mask"></a>Como: Definir a máscara de entrada
O controle de caixa de texto mascarado é um controle de caixa de texto avançado que dá suporte a uma sintaxe declarativa para aceitar ou rejeitar a entrada do usuário. Definindo a propriedade Máscara, você pode especificar a entrada do usuário permitida sem escrever qualquer lógica de validação personalizada no seu aplicativo. Para obter mais informações, consulte a seção comentários do <xref:System.Windows.Forms.MaskedTextBox> classe.  
  
## <a name="setting-the-mask-property-manually"></a>Definindo definir a propriedade Máscara manualmente  
 Se estiver familiarizado com os caracteres que a propriedade Máscara dá suporte, você poderá inseri-los manualmente. Para obter um resumo dos caracteres que a propriedade máscara dá suporte, consulte a seção de comentários do <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> propriedade.  
  
#### <a name="to-set-the-mask-property-manually"></a>Definir a propriedade Mask manualmente  
  
1.  Na **Design** exibição, selecione um <xref:System.Windows.Forms.MaskedTextBox>.  
  
2.  No **propriedades** janela, localize o <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> propriedade.  
  
3.  Digite a máscara desejada. Por exemplo, digite `###`.  
  
## <a name="using-the-input-mask-dialog-box"></a>Usando a caixa de diálogo Máscara de Entrada  
 A caixa de diálogo Máscara de Entrada fornece algumas máscaras de entrada predefinidas. Você também pode alterar as máscaras predefinidas ou inserir sua própria máscara manualmente.  
  
#### <a name="to-open-the-input-mask-dialog-box"></a>Abrir a caixa de diálogo Máscara de Entrada  
  
1.  Na **Design** exibição, selecione um <xref:System.Windows.Forms.MaskedTextBox>.  
  
    1.  Clique na marca inteligente para abrir o painel **Tarefas de MaskedTextBox**.  
  
    2.  Clique em **Definir Máscara**.  
  
     \- ou -  
  
    1.  No **propriedades** janela, selecione o <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> propriedade.  
  
    2.  Clique no botão de reticências na coluna do valor da propriedade.  
  
     A caixa de diálogo **Máscara de Entrada** é exibida.  
  
#### <a name="to-use-the-input-mask-dialog-box"></a>Usar a caixa de diálogo Máscara de Entrada  
  
1.  (Opcional) Clique em uma das máscaras predefinidas na lista.  
  
2.  (Opcional) Edite a máscara predefinida na caixa **Máscara**.  
  
3.  (Opcional) Digite uma nova máscara na caixa **Máscara**. Ou seja, não é necessário usar uma das máscaras predefinidas.  
  
    > [!NOTE]
    >  A caixa visualização exibe os caracteres que o usuário vê no <xref:System.Windows.Forms.MaskedTextBox>. Esses caracteres são um guia para ajudar o usuário a inserir os dados corretamente.  
  
4.  Selecione ou desmarque a caixa de seleção **Usar ValidatingType**. A caixa de seleção **Usar ValidatingType** especifica se um tipo de dados é usado para verificar a entrada de dados pelo usuário. Para obter mais informações, consulte a propriedade <xref:System.Windows.Forms.MaskedTextBox.ValidatingType%2A>.  
  
5.  Clique em **OK**.  
  
     A máscara é inserida na propriedade **Máscara** na janela **Propriedades**.  
  
## <a name="see-also"></a>Consulte também

- [Passo a passo: Trabalhando com o controle MaskedTextBox](walkthrough-working-with-the-maskedtextbox-control.md)
