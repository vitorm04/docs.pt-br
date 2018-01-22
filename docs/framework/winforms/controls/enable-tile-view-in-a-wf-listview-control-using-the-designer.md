---
title: "Como habilitar exibição lado a lado em um controle ListView dos Windows Forms usando o designer"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- tile view feature
- ListView control [Windows Forms], tile view
- tiling [Windows Forms], Windows Forms, controls
ms.assetid: 12f0816a-52b8-41ee-a6d9-ded3a8a5817a
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 72fc1212e6e154cf3459d9ae6b94b6a8965fb151
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-enable-tile-view-in-a-windows-forms-listview-control-using-the-designer"></a>Como habilitar exibição lado a lado em um controle ListView dos Windows Forms usando o designer
O recurso de exibição lado a lado do <xref:System.Windows.Forms.ListView> controle permite que você fornecer um equilíbrio visual entre informações gráficas e textuais. As informações textuais exibidas para um item na exibição lado a lado são as mesmas que as informações de coluna definidas para exibição de detalhes. Funções de exibição lado a lado em combinação com o agrupamento ou inserção marcar recursos o <xref:System.Windows.Forms.ListView> controle.  
  
 O modo de exibição lado a lado usa um ícone de 32 x 32 e várias linhas de texto, conforme mostrado na imagem a seguir.  
  
 ![Exibição lado a lado em um controle ListView](../../../../docs/framework/winforms/controls/media/listviewtile.gif "ListViewTile")  
  
 Propriedades e métodos de exibição lado a lado permitem especificar quais campos de coluna devem ser exibidos para cada item e controlar coletivamente o tamanho e a aparência de todos os itens dentro de uma janela de exibição lado a lado. Para maior clareza, a primeira linha do texto em uma exibição lado a lado é sempre o nome do item; isso não pode ser alterado.  
  
 O procedimento a seguir requer um **aplicativo do Windows** projeto com um formulário que contém um <xref:System.Windows.Forms.ListView> controle. Para obter informações sobre como configurar um projeto desse tipo, consulte [Como criar um projeto de aplicativos do Windows](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) e [Como adicionar controles ao Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).  
  
> [!NOTE]
>  A exibição lado a lado está disponível apenas em [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] quando o aplicativo chama o <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> método. Em sistemas operacionais anteriores, qualquer código relacionado ao modo de exibição lado a lado não tem efeito e o <xref:System.Windows.Forms.ListView> controle exibe no modo de exibição ícones grandes. Para obter mais informações, consulte <xref:System.Windows.Forms.ListView.View%2A?displayProperty=nameWithType>.  
>   
>  As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas. Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**. Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-set-tile-view-in-the-designer"></a>Para definir a exibição lado a lado no designer  
  
1.  Selecione o <xref:System.Windows.Forms.ListView> controle do formulário.  
  
2.  No **propriedades** janela, selecione o <xref:System.Windows.Forms.ListView.View%2A> propriedade e escolha **bloco**.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.ListView.TileSize%2A>  
 [Recursos do Windows XP e controles do Windows Forms](http://msdn.microsoft.com/library/bc7fab94-fce9-4bf1-a8ad-a5837c91c3c0)  
 [Visão geral do controle ListView](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)
