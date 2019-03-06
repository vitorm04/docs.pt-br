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
ms.openlocfilehash: c8e9f24a0e991fa44ddd3f4d778cc7ba640ae9c3
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57370170"
---
# <a name="how-to-list-the-data-formats-in-a-data-object"></a><span data-ttu-id="7cd8a-102">Como: Listar os formatos de dados em um objeto de dados</span><span class="sxs-lookup"><span data-stu-id="7cd8a-102">How to: List the Data Formats in a Data Object</span></span>
<span data-ttu-id="7cd8a-103">Os exemplos a seguir mostram como usar o <xref:System.Windows.DataObject.GetFormats%2A> sobrecargas do método obtém uma matriz de cadeias de caracteres indicando cada formato de dados que está disponível em um objeto de dados.</span><span class="sxs-lookup"><span data-stu-id="7cd8a-103">The following examples show how to use the <xref:System.Windows.DataObject.GetFormats%2A> method overloads get an array of strings denoting each data format that is available in a data object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7cd8a-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="7cd8a-104">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="7cd8a-105">Descrição</span><span class="sxs-lookup"><span data-stu-id="7cd8a-105">Description</span></span>  
 <span data-ttu-id="7cd8a-106">O código de exemplo a seguir usa o <xref:System.Windows.DataObject.GetFormats%2A> sobrecarga para obter uma matriz de cadeias de caracteres indicando todos os formatos de dados disponíveis em um objeto de dados (nativo e automaticamente).</span><span class="sxs-lookup"><span data-stu-id="7cd8a-106">The following example code uses the <xref:System.Windows.DataObject.GetFormats%2A> overload to get an array of strings denoting all data formats available in a data object (both native and auto-convertible).</span></span>  
  
### <a name="code"></a><span data-ttu-id="7cd8a-107">Código</span><span class="sxs-lookup"><span data-stu-id="7cd8a-107">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetAllDataFormats](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getalldataformats)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetAllDataFormats](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getalldataformats)]  
  
## <a name="example"></a><span data-ttu-id="7cd8a-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="7cd8a-108">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="7cd8a-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="7cd8a-109">Description</span></span>  
 <span data-ttu-id="7cd8a-110">O código de exemplo a seguir usa o <xref:System.Windows.DataObject.GetFormats%2A> sobrecarga para obter uma matriz de cadeias de caracteres indicando somente formatos de dados disponíveis em um objeto de dados (automática podem ser convertidas em formatos de dados são filtrados).</span><span class="sxs-lookup"><span data-stu-id="7cd8a-110">The following example code uses the <xref:System.Windows.DataObject.GetFormats%2A> overload to get an array of strings denoting only data formats available in a data object (auto-convertible data formats are filtered).</span></span>  
  
### <a name="code"></a><span data-ttu-id="7cd8a-111">Código</span><span class="sxs-lookup"><span data-stu-id="7cd8a-111">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetAllDataFormats_NativeOnly](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getalldataformats_nativeonly)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetAllDataFormats_NativeOnly](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getalldataformats_nativeonly)]  
  
## <a name="see-also"></a><span data-ttu-id="7cd8a-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7cd8a-112">See also</span></span>
- <xref:System.Windows.IDataObject>
- [<span data-ttu-id="7cd8a-113">Visão geral de arrastar e soltar</span><span class="sxs-lookup"><span data-stu-id="7cd8a-113">Drag and Drop Overview</span></span>](drag-and-drop-overview.md)
