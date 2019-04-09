---
title: 'Como: Listar os formatos de dados em um objeto de dados'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- drag-and-drop [WPF], listing data formats
- DataFormats class [WPF]
- data formats [WPF], listing
ms.assetid: 18e7ba4b-ccef-4815-ae2d-3a32891010c0
ms.openlocfilehash: f8230eac33a18a0d99cc757d54c2b901c1afe977
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59077739"
---
# <a name="how-to-list-the-data-formats-in-a-data-object"></a><span data-ttu-id="16e3c-102">Como: Listar os formatos de dados em um objeto de dados</span><span class="sxs-lookup"><span data-stu-id="16e3c-102">How to: List the Data Formats in a Data Object</span></span>
<span data-ttu-id="16e3c-103">Os exemplos a seguir mostram como usar o <xref:System.Windows.DataObject.GetFormats%2A> sobrecargas do método obtém uma matriz de cadeias de caracteres indicando cada formato de dados que está disponível em um objeto de dados.</span><span class="sxs-lookup"><span data-stu-id="16e3c-103">The following examples show how to use the <xref:System.Windows.DataObject.GetFormats%2A> method overloads get an array of strings denoting each data format that is available in a data object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="16e3c-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="16e3c-104">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="16e3c-105">Descrição</span><span class="sxs-lookup"><span data-stu-id="16e3c-105">Description</span></span>  
 <span data-ttu-id="16e3c-106">O código de exemplo a seguir usa o <xref:System.Windows.DataObject.GetFormats%2A> sobrecarga para obter uma matriz de cadeias de caracteres indicando todos os formatos de dados disponíveis em um objeto de dados (nativo e automaticamente).</span><span class="sxs-lookup"><span data-stu-id="16e3c-106">The following example code uses the <xref:System.Windows.DataObject.GetFormats%2A> overload to get an array of strings denoting all data formats available in a data object (both native and auto-convertible).</span></span>  
  
### <a name="code"></a><span data-ttu-id="16e3c-107">Código</span><span class="sxs-lookup"><span data-stu-id="16e3c-107">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetAllDataFormats](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getalldataformats)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetAllDataFormats](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getalldataformats)]  
  
## <a name="example"></a><span data-ttu-id="16e3c-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="16e3c-108">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="16e3c-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="16e3c-109">Description</span></span>  
 <span data-ttu-id="16e3c-110">O código de exemplo a seguir usa o <xref:System.Windows.DataObject.GetFormats%2A> sobrecarga para obter uma matriz de cadeias de caracteres indicando somente formatos de dados disponíveis em um objeto de dados (automática podem ser convertidas em formatos de dados são filtrados).</span><span class="sxs-lookup"><span data-stu-id="16e3c-110">The following example code uses the <xref:System.Windows.DataObject.GetFormats%2A> overload to get an array of strings denoting only data formats available in a data object (auto-convertible data formats are filtered).</span></span>  
  
### <a name="code"></a><span data-ttu-id="16e3c-111">Código</span><span class="sxs-lookup"><span data-stu-id="16e3c-111">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetAllDataFormats_NativeOnly](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getalldataformats_nativeonly)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetAllDataFormats_NativeOnly](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getalldataformats_nativeonly)]  
  
## <a name="see-also"></a><span data-ttu-id="16e3c-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="16e3c-112">See also</span></span>

- <xref:System.Windows.IDataObject>
- [<span data-ttu-id="16e3c-113">Visão geral de arrastar e soltar</span><span class="sxs-lookup"><span data-stu-id="16e3c-113">Drag and Drop Overview</span></span>](drag-and-drop-overview.md)
