---
title: Solucionando problemas do controle DataRepeater (Visual Studio) | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- DataRepeater, troubleshooting
ms.assetid: c0ab9469-eced-4f52-aa18-4bd8dd4f1a9a
caps.latest.revision: 10
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: bda2fdf120e275ec1e4c326649906a33c9b1206d
ms.lasthandoff: 03/13/2017

---
# <a name="troubleshooting-the-datarepeater-control-visual-studio"></a>Solucionando problemas do controle DataRepeater (Visual Studio)
Este tópico lista problemas comuns que podem ocorrer quando você estiver trabalhando com o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>controle.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
  
## <a name="datarepeater-keyboard-and-mouse-events-are-not-raised"></a>Eventos de Mouse e teclado DataRepeater não são gerados  
 Algumas <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>não são gerados eventos de controle, como eventos de teclado e mouse,.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> Esse comportamento é esperado. O <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>controle em si é um contêiner para <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem>objetos e não pode ser acessado no tempo de execução.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> </xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> O <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem>não expõe eventos em tempo de design.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> Portanto, ao clicar em um item ou pressionando uma tecla quando o item tem o foco não gera um evento.  
  
 A exceção é quando o <xref:System.Windows.Forms.Control.Padding%2A>estiver definida como um grande valor suficiente para expor as bordas do <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>controle.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> </xref:System.Windows.Forms.Control.Padding%2A> Nesse caso, clique na margem exposta irá disparar eventos de mouse.  
  
 Para resolver esse problema, adicione um <xref:System.Windows.Forms.Panel>controle para a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A>seção de <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>controle, e, em seguida, adicione o restante dos controles para <xref:System.Windows.Forms.Panel>.</xref:System.Windows.Forms.Panel> </xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> </xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> </xref:System.Windows.Forms.Panel> Você pode adicionar código para o <xref:System.Windows.Forms.Panel>manipuladores de eventos do controle para eventos de teclado e mouse.</xref:System.Windows.Forms.Panel>  
  
## <a name="the-datarepeater-is-partially-hidden-behind-the-binding-navigator"></a>DataRepeater parcialmente estiver oculto por trás do navegador de ligação  
 Quando você adiciona pela primeira vez um <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>controle a um formulário e, em seguida, adicionar controles ligados a dados do **fontes de dados** janela, o <xref:System.Windows.Forms.BindingNavigator>controle pode aparecer na parte superior do <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>controle.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> </xref:System.Windows.Forms.BindingNavigator> </xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> Isso é uma limitação conhecida do **fontes de dados** janela e é consistente com o comportamento de outros controles, como o <xref:System.Windows.Forms.DataGridView>controle.</xref:System.Windows.Forms.DataGridView>  
  
 Pode qualquer movimentação de <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>menor do que o <xref:System.Windows.Forms.BindingNavigator>controlar em tempo de design ou adicionar código a seguir no `Load` manipulador de eventos.</xref:System.Windows.Forms.BindingNavigator> </xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
  
```vb  
DataRepeater1.Top = ProductsBindingNavigator.Height  
```  
  
```cs  
dataRepeater1.Top = productsBindingNavigator.Height;  
```  
  
## <a name="controls-are-not-displayed-correctly-at-run-time"></a>Controles não são exibidos corretamente no tempo de execução  
 Alguns controles em um <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>controle pode não ser exibido conforme o esperado em tempo de execução.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> O processo usado para clonar os controles a partir de <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A>para o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem>nem sempre pode determinar todas as propriedades de todos os controles.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> </xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> Por exemplo, se você adicionar um desassociado <xref:System.Windows.Forms.ListBox>controle um <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>controlar em tempo de design e preencher seus <xref:System.Windows.Forms.ListBox.Items%2A>coleção com uma lista de cadeias de caracteres, o <xref:System.Windows.Forms.ListBox>estará vazia em tempo de execução.</xref:System.Windows.Forms.ListBox> </xref:System.Windows.Forms.ListBox.Items%2A> </xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> </xref:System.Windows.Forms.ListBox> Isso ocorre porque o processo de clonagem não pode levar em conta o <xref:System.Windows.Forms.ListBox.Items%2A>propriedade.</xref:System.Windows.Forms.ListBox.Items%2A>  
  
 Você pode corrigir problemas como este, restaurando as propriedades ausentes no <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemCloned>evento que ocorre após a clonagem padrão.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemCloned> O exemplo a seguir demonstra como reparar o <xref:System.Windows.Forms.ListBox.Items%2A>coleção de um <xref:System.Windows.Forms.ListBox>controlar o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemCloned>manipulador de eventos.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemCloned> </xref:System.Windows.Forms.ListBox> </xref:System.Windows.Forms.ListBox.Items%2A>  
  
 [!code-cs[&#1; VbPowerPacksDataRepeaterItemCloned](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/troubleshooting-the-datarepeater-control-visual-studio_1.cs) ] 
 [!code-vb [VbPowerPacksDataRepeaterItemCloned n º&1;](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/troubleshooting-the-datarepeater-control-visual-studio_1.vb)]  
  
## <a name="the-selection-symbol-on-the-item-header-is-missing"></a>O símbolo de seleção no cabeçalho do Item está ausente  
 Quando você altera o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A>propriedade do cabeçalho do item em uma <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>controle, algumas opções de cor podem causar o símbolo de seleção desapareça.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> </xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A> Alterando o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderSize%2A>propriedade também pode causar o símbolo de seleção desapareça.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderSize%2A>  
  
 A cor e o tamanho do símbolo de seleção não podem ser alterados.  
  
-   Se você definir o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A>para <xref:System.Drawing.Color.White%2A>, o símbolo de seleção não ficará visível quando um item é selecionado pela primeira vez.</xref:System.Drawing.Color.White%2A> </xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A>  
  
-   Se você definir o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A>para <xref:System.Drawing.Color.Black%2A>, o símbolo de seleção não fica visível quando um controle é selecionado e o símbolo de lápis não ficará visível quando um controle está no modo de edição.</xref:System.Drawing.Color.Black%2A> </xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A>  
  
-   Se o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderSize%2A>propriedade é definida como um valor que seja menor do que 11, os símbolos de indicador no cabeçalho do item não serão exibidos.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderSize%2A>  
  
 Você pode fornecer seu próprio símbolo de cabeçalho e seleção de item usando um <xref:System.Windows.Forms.PictureBox>monitoramento e controle o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem.IsCurrent%2A>propriedade do <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem>no <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem>eventos do <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>controle.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> </xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> </xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> </xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem.IsCurrent%2A> </xref:System.Windows.Forms.PictureBox> Para obter mais informações, consulte <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem.IsCurrent%2A>.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem.IsCurrent%2A>  
  
## <a name="see-also"></a>Consulte também  
 [Introdução ao controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)   
 [Como: exibir dados associados em um controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md)   
 [Como: exibir controles não associados em um controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio.md)   
 [Como: alterar o Layout de um controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-layout-of-a-datarepeater-control-visual-studio.md)   
 [Como: alterar a aparência de um controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)   
 [Como: exibir cabeçalhos de Item em um controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-item-headers-in-a-datarepeater-control-visual-studio.md)   
 [Como: desabilitar a adição e exclusão de itens DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio.md)   
 [Como: pesquisar dados em um controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-search-data-in-a-datarepeater-control-visual-studio.md)   
 [Como: criar um formulário mestre/detalhes usando dois controles DataRepeater (Visual Studio)](../../../visual-basic/developing-apps/windows-forms/how-to-create-a-master-detail-form-by-using-two-datarepeater-controls.md)
