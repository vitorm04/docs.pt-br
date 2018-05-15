---
title: Como recuperar dados em um formato de dados específico
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- drag-and-drop [WPF], retrieving data
- DataFormats class [WPF], retrieving data
- DataObject class [WPF], retrieving data
ms.assetid: a625acf3-1144-44cd-add7-456aefc3859f
ms.openlocfilehash: 405fff1b586207249fbabafb28791ffa2901cf49
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-retrieve-data-in-a-particular-data-format"></a><span data-ttu-id="4dd47-102">Como recuperar dados em um formato de dados específico</span><span class="sxs-lookup"><span data-stu-id="4dd47-102">How to: Retrieve Data in a Particular Data Format</span></span>
<span data-ttu-id="4dd47-103">Os exemplos a seguir mostram como recuperar dados de um objeto de dados em um formato especificado.</span><span class="sxs-lookup"><span data-stu-id="4dd47-103">The following examples show how to retrieve data from a data object in a specified format.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4dd47-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4dd47-104">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="4dd47-105">Descrição</span><span class="sxs-lookup"><span data-stu-id="4dd47-105">Description</span></span>  
 <span data-ttu-id="4dd47-106">O código de exemplo a seguir usa o <xref:System.Windows.DataObject.GetDataPresent%28System.String%29> sobrecarga para verificar primeiro se formatar um dado especificado está disponível (modo nativo ou por conversão automática); se o formato especificado estiver disponível, o exemplo recupera os dados usando o <xref:System.Windows.DataObject.GetData%28System.String%29> método.</span><span class="sxs-lookup"><span data-stu-id="4dd47-106">The following example code uses the <xref:System.Windows.DataObject.GetDataPresent%28System.String%29> overload to first check if a specified data format is available (natively or by auto-convert); if the specified format is available, the example retrieves the data by using the <xref:System.Windows.DataObject.GetData%28System.String%29> method.</span></span>  
  
### <a name="code"></a><span data-ttu-id="4dd47-107">Código</span><span class="sxs-lookup"><span data-stu-id="4dd47-107">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getspecificdataformat)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getspecificdataformat)]  
  
## <a name="example"></a><span data-ttu-id="4dd47-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4dd47-108">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="4dd47-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="4dd47-109">Description</span></span>  
 <span data-ttu-id="4dd47-110">O código de exemplo a seguir usa o <xref:System.Windows.DataObject.GetDataPresent%28System.String%2CSystem.Boolean%29> sobrecarga para primeiro verificar se um formato de dados especificado está disponível de forma nativa (formatos de dados auto conversíveis são filtrados); se o formato especificado estiver disponível, o exemplo recupera os dados usando o <xref:System.Windows.DataObject.GetData%28System.String%29>método.</span><span class="sxs-lookup"><span data-stu-id="4dd47-110">The following example code uses the <xref:System.Windows.DataObject.GetDataPresent%28System.String%2CSystem.Boolean%29> overload to first check if a specified data format is available natively (auto-convertible data formats are filtered); if the specified format is available, the example retrieves the data by using the <xref:System.Windows.DataObject.GetData%28System.String%29> method.</span></span>  
  
### <a name="code"></a><span data-ttu-id="4dd47-111">Código</span><span class="sxs-lookup"><span data-stu-id="4dd47-111">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat_Native](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getspecificdataformat_native)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat_Native](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getspecificdataformat_native)]  
  
## <a name="see-also"></a><span data-ttu-id="4dd47-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4dd47-112">See Also</span></span>  
 <xref:System.Windows.IDataObject>  
 [<span data-ttu-id="4dd47-113">Visão geral de arrastar e soltar</span><span class="sxs-lookup"><span data-stu-id="4dd47-113">Drag and Drop Overview</span></span>](../../../../docs/framework/wpf/advanced/drag-and-drop-overview.md)
