---
title: Como determinar se um formato de dados está presente em um objeto de dados
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataFormats class [WPF]
- drag-and-drop [WPF], data formats present
- data formats [WPF], determining if present
ms.assetid: e487a454-c9fc-4e53-aeaa-c458d059ad4c
ms.openlocfilehash: e3e2f47df0ae1fdf0fe875827473f2c3a1b53fb5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33543413"
---
# <a name="how-to-determine-if-a-data-format-is-present-in-a-data-object"></a><span data-ttu-id="e479d-102">Como determinar se um formato de dados está presente em um objeto de dados</span><span class="sxs-lookup"><span data-stu-id="e479d-102">How to: Determine if a Data Format is Present in a Data Object</span></span>
<span data-ttu-id="e479d-103">Os exemplos a seguir mostram como usar as várias <xref:System.Windows.DataObject.GetDataPresent%2A> sobrecargas do método para consultar se um formato específico de dados está presente em um objeto de dados.</span><span class="sxs-lookup"><span data-stu-id="e479d-103">The following examples show how to use the various <xref:System.Windows.DataObject.GetDataPresent%2A> method overloads to query whether a particular data format is present in a data object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e479d-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e479d-104">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="e479d-105">Descrição</span><span class="sxs-lookup"><span data-stu-id="e479d-105">Description</span></span>  
 <span data-ttu-id="e479d-106">O código de exemplo a seguir usa o <xref:System.Windows.DataObject.GetDataPresent%28System.String%29> sobrecarga para consultar a presença de um formato específico de dados pela cadeia de caracteres do descritor.</span><span class="sxs-lookup"><span data-stu-id="e479d-106">The following example code uses the <xref:System.Windows.DataObject.GetDataPresent%28System.String%29> overload to query for the presence of a particular data format by descriptor string.</span></span>  
  
### <a name="code"></a><span data-ttu-id="e479d-107">Código</span><span class="sxs-lookup"><span data-stu-id="e479d-107">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_QueryDataFormats_String](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_querydataformats_string)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_QueryDataFormats_String](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_querydataformats_string)]  
  
## <a name="example"></a><span data-ttu-id="e479d-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e479d-108">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="e479d-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="e479d-109">Description</span></span>  
 <span data-ttu-id="e479d-110">O código de exemplo a seguir usa o <xref:System.Windows.DataObject.GetDataPresent%28System.Type%29> sobrecarga para consultar a presença de um formato específico de dados por tipo.</span><span class="sxs-lookup"><span data-stu-id="e479d-110">The following example code uses the <xref:System.Windows.DataObject.GetDataPresent%28System.Type%29> overload to query for the presence of a particular data format by type.</span></span>  
  
### <a name="code"></a><span data-ttu-id="e479d-111">Código</span><span class="sxs-lookup"><span data-stu-id="e479d-111">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_QueryDataFormats_Type](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_querydataformats_type)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_QueryDataFormats_Type](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_querydataformats_type)]  
  
## <a name="example"></a><span data-ttu-id="e479d-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e479d-112">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="e479d-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="e479d-113">Description</span></span>  
 <span data-ttu-id="e479d-114">O código de exemplo a seguir usa o <xref:System.Windows.DataObject.GetDataPresent%28System.String%2CSystem.Boolean%29> sobrecarga para consultar dados por cadeia de caracteres de descritor e especificando como tratar formatos de dados auto conversíveis.</span><span class="sxs-lookup"><span data-stu-id="e479d-114">The following example code uses the <xref:System.Windows.DataObject.GetDataPresent%28System.String%2CSystem.Boolean%29> overload to query for data by descriptor string, and specifying how to treat auto-convertible data formats.</span></span>  
  
### <a name="code"></a><span data-ttu-id="e479d-115">Código</span><span class="sxs-lookup"><span data-stu-id="e479d-115">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_QueryDataFormats_Autoconvert](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_querydataformats_autoconvert)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_QueryDataFormats_Autoconvert](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_querydataformats_autoconvert)]  
  
## <a name="see-also"></a><span data-ttu-id="e479d-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e479d-116">See Also</span></span>  
 <xref:System.Windows.IDataObject>
