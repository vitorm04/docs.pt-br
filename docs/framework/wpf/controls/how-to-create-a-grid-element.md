---
title: 'Como: Criar um elemento de grade'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Grid control [WPF], creating [WPF], grid instance
ms.assetid: b2f07626-9df8-43b8-8d36-492f3cb42837
ms.openlocfilehash: 5aa0e5b617d952fd5df1f80ae0ff146a6899aa32
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57379504"
---
# <a name="how-to-create-a-grid-element"></a><span data-ttu-id="2a302-102">Como: Criar um elemento de grade</span><span class="sxs-lookup"><span data-stu-id="2a302-102">How to: Create a Grid Element</span></span>
## <a name="example"></a><span data-ttu-id="2a302-103">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2a302-103">Example</span></span>  
 <span data-ttu-id="2a302-104">O exemplo a seguir mostra como criar e usar uma instância do <xref:System.Windows.Controls.Grid> usando o [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] ou código.</span><span class="sxs-lookup"><span data-stu-id="2a302-104">The following example shows how to create and use an instance of <xref:System.Windows.Controls.Grid> by using either [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] or code.</span></span> <span data-ttu-id="2a302-105">Este exemplo usa três <xref:System.Windows.Controls.ColumnDefinition> objetos e três <xref:System.Windows.Controls.RowDefinition> objetos criar uma grade que tem nove células, como em uma planilha.</span><span class="sxs-lookup"><span data-stu-id="2a302-105">This example uses three <xref:System.Windows.Controls.ColumnDefinition> objects and three <xref:System.Windows.Controls.RowDefinition> objects to create a grid that has nine cells, such as in a worksheet.</span></span> <span data-ttu-id="2a302-106">Cada célula contém um <xref:System.Windows.Controls.TextBlock> elemento que representa a data e a linha superior contém uma <xref:System.Windows.Controls.TextBlock> com o <xref:System.Windows.Controls.Grid.ColumnSpan%2A> propriedade aplicado.</span><span class="sxs-lookup"><span data-stu-id="2a302-106">Each cell contains a <xref:System.Windows.Controls.TextBlock> element that represents data, and the top row contains a <xref:System.Windows.Controls.TextBlock> with the <xref:System.Windows.Controls.Grid.ColumnSpan%2A> property applied.</span></span> <span data-ttu-id="2a302-107">Para mostrar os limites de cada célula, o <xref:System.Windows.Controls.Grid.ShowGridLines%2A> propriedade está habilitada.</span><span class="sxs-lookup"><span data-stu-id="2a302-107">To show the boundaries of each cell, the <xref:System.Windows.Controls.Grid.ShowGridLines%2A> property is enabled.</span></span>  
  
 [!code-csharp[Grid#3](~/samples/snippets/csharp/VS_Snippets_Wpf/Grid/CSharp/Grid_Code.cs#3)]
 [!code-vb[Grid#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Grid/VisualBasic/grid_vb.vb#3)]
 [!code-xaml[Grid#3](~/samples/snippets/xaml/VS_Snippets_Wpf/Grid/XAML/default.xaml#3)]  
  
  <span data-ttu-id="2a302-108">Qualquer uma das abordagens irá gerar uma interface do usuário que se parece muito os mesmos, como a mostrada abaixo.</span><span class="sxs-lookup"><span data-stu-id="2a302-108">Either approach will generate a user interface that looks much the same, like the one below.</span></span>

  ![uma captura de tela mostra uma interface de usuário do WPF que contém uma grade, dividida em três colunas.](././media/how-to-create-a-grid-element/how-to-create-a-grid-element.png)
## <a name="see-also"></a><span data-ttu-id="2a302-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2a302-112">See also</span></span>
- <xref:System.Windows.Controls.Grid>
- [<span data-ttu-id="2a302-113">Visão geral de painéis</span><span class="sxs-lookup"><span data-stu-id="2a302-113">Panels Overview</span></span>](panels-overview.md)
