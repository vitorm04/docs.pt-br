---
title: Solucionando problemas do controle DataRepeater (Visual Studio)
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataRepeater, troubleshooting
ms.assetid: c0ab9469-eced-4f52-aa18-4bd8dd4f1a9a
ms.openlocfilehash: 7b045e1c45221cbde82c88286da8e698a763d844
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54580597"
---
# <a name="troubleshooting-the-datarepeater-control-visual-studio"></a>Solucionando problemas do controle DataRepeater (Visual Studio)
Este tópico lista os problemas comuns que podem ocorrer quando você estiver trabalhando com o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle.  
  
## <a name="datarepeater-keyboard-and-mouse-events-are-not-raised"></a>Eventos de Mouse e teclado DataRepeater não serão gerados  
 Alguns <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> eventos de controle, como eventos de teclado e mouse, não serão gerados. Esse comportamento é esperado. O <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle em si é um contêiner para <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> objetos e não pode ser acessado no tempo de execução. O <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> não expõe eventos em tempo de design. Portanto, clicar em um item ou pressionar uma tecla quando o item tem o foco não gera um evento.  
  
 A exceção é quando o <xref:System.Windows.Forms.Control.Padding%2A> estiver definida como um grande valor suficiente para expor as bordas do <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle. Nesse caso, clique na margem exposta irá disparar eventos de mouse.  
  
 Para resolver esse problema, adicione uma <xref:System.Windows.Forms.Panel> o controle para o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> seção o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controlar e, em seguida, adicione o restante dos controles para o <xref:System.Windows.Forms.Panel>. Em seguida, você pode adicionar código para o <xref:System.Windows.Forms.Panel> manipuladores de eventos do controle para eventos de teclado e mouse.  
  
## <a name="the-datarepeater-is-partially-hidden-behind-the-binding-navigator"></a>DataRepeater parcialmente está oculto por trás do navegador de associação  
 Quando você adiciona primeiro uma <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controlar a um formulário e, em seguida, adicione os controles de associação de dados da **fontes de dados** janela, o <xref:System.Windows.Forms.BindingNavigator> controle pode aparecer na parte superior do <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle. Essa é uma limitação conhecida do **fontes de dados** janela e é consistente com o comportamento de outros controles, como o <xref:System.Windows.Forms.DataGridView> controle.  
  
 É possível que qualquer movimentação a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> menor do que o <xref:System.Windows.Forms.BindingNavigator> controlar em tempo de design ou adicionar código a seguir no `Load` manipulador de eventos.  
  
```vb  
DataRepeater1.Top = ProductsBindingNavigator.Height  
```  
  
```csharp  
dataRepeater1.Top = productsBindingNavigator.Height;  
```  
  
## <a name="controls-are-not-displayed-correctly-at-run-time"></a>Controles não são exibidos corretamente no tempo de execução  
 Alguns controles em um <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle pode não ser exibido como esperado em tempo de execução. O processo usado para clonar controles a partir o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> para o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> nem sempre podem determinar todas as propriedades de todos os controles. Por exemplo, se você adicionar um desassociado <xref:System.Windows.Forms.ListBox> o controle para uma <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controlar em tempo de design e preencher seus <xref:System.Windows.Forms.ListBox.Items%2A> coleção com uma lista de cadeias de caracteres, o <xref:System.Windows.Forms.ListBox> estará vazio em tempo de execução. Isso ocorre porque o processo de clonagem não pode levar em conta o <xref:System.Windows.Forms.ListBox.Items%2A> propriedade.  
  
 Você pode corrigir problemas como esse, restaurando as propriedades ausentes no <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemCloned> evento, que ocorre depois que o padrão de clonagem for concluída. O exemplo a seguir demonstra como reparar o <xref:System.Windows.Forms.ListBox.Items%2A> coleção de um <xref:System.Windows.Forms.ListBox> no controlar o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemCloned> manipulador de eventos.  
  
 [!code-csharp[VbPowerPacksDataRepeaterItemCloned#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/troubleshooting-the-datarepeater-control-visual-studio_1.cs)]
 [!code-vb[VbPowerPacksDataRepeaterItemCloned#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/troubleshooting-the-datarepeater-control-visual-studio_1.vb)]  
  
## <a name="the-selection-symbol-on-the-item-header-is-missing"></a>O símbolo de seleção no cabeçalho do Item está ausente  
 Quando você altera a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A> propriedade do cabeçalho do item em um <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle, algumas opções de cor podem causar o símbolo de seleção desapareça. Alterando o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderSize%2A> propriedade também pode fazer com que o símbolo de seleção desapareça.  
  
 A cor e tamanho do símbolo de seleção não podem ser alterados.  
  
-   Se você definir a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A> para <xref:System.Drawing.Color.White%2A>, o símbolo de seleção não ficará visível quando um item é selecionado pela primeira vez.  
  
-   Se você definir a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A> para <xref:System.Drawing.Color.Black%2A>, o símbolo de seleção não ficará visível quando um controle está selecionado e o símbolo de lápis não ficará visível quando um controle está no modo de edição.  
  
-   Se o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderSize%2A> estiver definida como um valor que é menor que 11, os símbolos de indicador no cabeçalho do item não serão exibidos.  
  
 Você pode fornecer seu próprio símbolo de cabeçalho e a seleção de item usando um <xref:System.Windows.Forms.PictureBox> monitoramento e controle o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem.IsCurrent%2A> propriedade da <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> no <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> eventos do <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle. Para obter mais informações, consulte <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem.IsCurrent%2A>.  
  
## <a name="see-also"></a>Consulte também
- [Introdução ao Controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)
- [Como: Exibir dados associados em um controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md)
- [Como: Exibir controles não associados em um controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio.md)
- [Como: Alterar o Layout de um controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-layout-of-a-datarepeater-control-visual-studio.md)
- [Como: Alterar a aparência de um controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)
- [Como: Exibir cabeçalhos de Item em um controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-item-headers-in-a-datarepeater-control-visual-studio.md)
- [Como: Desabilitar a adição e exclusão de itens DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio.md)
- [Como: Dados de pesquisa em um controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-search-data-in-a-datarepeater-control-visual-studio.md)
- [Como: Criar um formulário mestre/detalhes usando dois controles DataRepeater (Visual Studio)](../../../visual-basic/developing-apps/windows-forms/how-to-create-a-master-detail-form-by-using-two-datarepeater-controls.md)
