---
title: Visão geral do componente ImageList
ms.date: 03/30/2017
f1_keywords:
- ImageList
helpviewer_keywords:
- collection controls [Windows Forms], images
- icon list control
- ImageList component [Windows Forms], about ImageList component
ms.assetid: 7e25d89b-5633-40c1-afc3-82e0e301ffa2
ms.openlocfilehash: b46204375cb046d637f4c9e1d888f37d10ea1f57
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76728096"
---
# <a name="imagelist-component-overview-windows-forms"></a>Visão geral do componente ImageList (Windows Forms)

O componente Windows Forms <xref:System.Windows.Forms.ImageList> é usado para armazenar imagens, que podem ser exibidas por controles. Uma lista de imagens permite escrever código para um catálogo de imagens único e consistente. Por exemplo, você pode girar imagens exibidas por um controle de <xref:System.Windows.Forms.Button> simplesmente alterando a propriedade <xref:System.Windows.Forms.ButtonBase.ImageIndex%2A> ou <xref:System.Windows.Forms.ButtonBase.ImageKey%2A> do botão. Você também pode associar a mesma lista de imagem a vários controles. Por exemplo, se você estiver usando um controle de <xref:System.Windows.Forms.ListView> e um controle de <xref:System.Windows.Forms.TreeView> para exibir a mesma lista de arquivos, a alteração do ícone de um arquivo na lista de imagens fará com que o novo ícone apareça em ambos os modos de exibição.

## <a name="using-imagelist-with-controls"></a>Usando ImageList com controles

Você pode usar uma lista de imagens com qualquer controle que tenha uma propriedade `ImageList` — ou, no caso do controle <xref:System.Windows.Forms.ListView>, <xref:System.Windows.Forms.ListView.SmallImageList%2A> e propriedades <xref:System.Windows.Forms.ListView.LargeImageList%2A>. Os controles que podem ser associados a uma lista de imagens incluem: os controles <xref:System.Windows.Forms.ListView>, <xref:System.Windows.Forms.TreeView>, <xref:System.Windows.Forms.ToolBar>, <xref:System.Windows.Forms.TabControl>, <xref:System.Windows.Forms.Button>, <xref:System.Windows.Forms.CheckBox>, <xref:System.Windows.Forms.RadioButton>e <xref:System.Windows.Forms.Label>. Para associar a lista de imagens a um controle, defina a propriedade `ImageList` do controle como o nome do componente <xref:System.Windows.Forms.ImageList>.

## <a name="key-properties"></a>Propriedades da chave

A propriedade de chave do componente <xref:System.Windows.Forms.ImageList> é <xref:System.Windows.Forms.ImageList.Images%2A>, que contém as imagens a serem usadas pelo controle associado. Cada imagem individual pode ser acessada pelo seu valor de índice ou por sua chave. A propriedade <xref:System.Windows.Forms.ImageList.ColorDepth%2A> determina o número de cores com as quais as imagens são renderizadas. As imagens serão exibidas no mesmo tamanho, definidas pela propriedade <xref:System.Windows.Forms.ImageList.ImageSize%2A>. Imagens maiores terão a escala ajustada para caber.

## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.ImageList>
- [Como adicionar ou remover imagens com o componente ImageList dos Windows Forms](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md)
