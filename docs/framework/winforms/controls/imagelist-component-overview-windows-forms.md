---
title: "Visão geral do componente ImageList (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: ImageList
helpviewer_keywords:
- collection controls [Windows Forms], images
- icon list control
- ImageList component [Windows Forms], about ImageList component
ms.assetid: 7e25d89b-5633-40c1-afc3-82e0e301ffa2
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a913de1a6808c7e600a4f28ed58dedf93506466b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="imagelist-component-overview-windows-forms"></a>Visão geral do componente ImageList (Windows Forms)
Windows Forms <xref:System.Windows.Forms.ImageList> componente é usado para armazenar as imagens, que podem ser exibidas por controles. Uma lista de imagens permite escrever código para um catálogo de imagens único e consistente. Por exemplo, você pode girar imagens exibidas por um <xref:System.Windows.Forms.Button> controle simplesmente alterando o botão <xref:System.Windows.Forms.ButtonBase.ImageIndex%2A> ou <xref:System.Windows.Forms.ButtonBase.ImageKey%2A> propriedade. Você também pode associar a mesma lista de imagem a vários controles. Por exemplo, se você estiver usando um <xref:System.Windows.Forms.ListView> controle e um <xref:System.Windows.Forms.TreeView> controle para exibir a mesma lista de arquivos, alterando o ícone de um arquivo na lista de imagens fará com que o ícone novo para aparecer em ambos os modos de exibição.  
  
## <a name="using-imagelist-with-controls"></a>Usando ImageList com controles  
 Você pode usar uma lista de imagens com qualquer controle que possui um `ImageList` propriedade — ou, no caso do <xref:System.Windows.Forms.ListView> controle, <xref:System.Windows.Forms.ListView.SmallImageList%2A> e <xref:System.Windows.Forms.ListView.LargeImageList%2A> propriedades. Os controles que podem ser associados uma lista de imagens incluem: o <xref:System.Windows.Forms.ListView>, <xref:System.Windows.Forms.TreeView>, <xref:System.Windows.Forms.ToolBar>, <xref:System.Windows.Forms.TabControl>, <xref:System.Windows.Forms.Button>, <xref:System.Windows.Forms.CheckBox>, <xref:System.Windows.Forms.RadioButton>, e <xref:System.Windows.Forms.Label> controles. Para associar um controle de lista de imagens, defina o controle `ImageList` o nome da propriedade a <xref:System.Windows.Forms.ImageList> componente.  
  
## <a name="key-properties"></a>Propriedades da chave  
 A propriedade de chave de <xref:System.Windows.Forms.ImageList> componente é <xref:System.Windows.Forms.ImageList.Images%2A>, que contém as imagens a serem usados pelo controle associado. Cada imagem individual pode ser acessada pelo seu valor de índice ou por sua chave. O <xref:System.Windows.Forms.ImageList.ColorDepth%2A> propriedade determina o número de cores que as imagens serão renderizadas. As imagens todos serão exibidas no mesmo tamanho, definido pelo <xref:System.Windows.Forms.ImageList.ImageSize%2A> propriedade. Imagens maiores terão a escala ajustada para caber.  
  
 Se você estiver usando [!INCLUDE[vsprvslong](../../../../includes/vsprvslong-md.md)], terá acesso a uma ampla biblioteca de imagens padrão que podem ser usadas em seus aplicativos.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.ImageList>  
 [Como adicionar ou remover imagens com o componente ImageList dos Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md)
