---
title: 'Como: Determinar se um formato de dados está presente em um objeto de dados'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataFormats class [WPF]
- drag-and-drop [WPF], data formats present
- data formats [WPF], determining if present
ms.assetid: e487a454-c9fc-4e53-aeaa-c458d059ad4c
ms.openlocfilehash: 4cec733490e2a9dc5d54b3b253ac38a5090ac885
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59207962"
---
# <a name="how-to-determine-if-a-data-format-is-present-in-a-data-object"></a><span data-ttu-id="dfa73-102">Como: Determinar se um formato de dados está presente em um objeto de dados</span><span class="sxs-lookup"><span data-stu-id="dfa73-102">How to: Determine if a Data Format is Present in a Data Object</span></span>
<span data-ttu-id="dfa73-103">Os exemplos a seguir mostram como usar os vários <xref:System.Windows.DataObject.GetDataPresent%2A> sobrecargas do método para consultar se um formato específico de dados está presente em um objeto de dados.</span><span class="sxs-lookup"><span data-stu-id="dfa73-103">The following examples show how to use the various <xref:System.Windows.DataObject.GetDataPresent%2A> method overloads to query whether a particular data format is present in a data object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dfa73-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="dfa73-104">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="dfa73-105">Descrição</span><span class="sxs-lookup"><span data-stu-id="dfa73-105">Description</span></span>  
 <span data-ttu-id="dfa73-106">O código de exemplo a seguir usa o <xref:System.Windows.DataObject.GetDataPresent%28System.String%29> sobrecarga da consulta a presença de um formato específico de dados pela cadeia de caracteres do descritor.</span><span class="sxs-lookup"><span data-stu-id="dfa73-106">The following example code uses the <xref:System.Windows.DataObject.GetDataPresent%28System.String%29> overload to query for the presence of a particular data format by descriptor string.</span></span>  
  
### <a name="code"></a><span data-ttu-id="dfa73-107">Código</span><span class="sxs-lookup"><span data-stu-id="dfa73-107">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_QueryDataFormats_String](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_querydataformats_string)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_QueryDataFormats_String](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_querydataformats_string)]  
  
## <a name="example"></a><span data-ttu-id="dfa73-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="dfa73-108">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="dfa73-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="dfa73-109">Description</span></span>  
 <span data-ttu-id="dfa73-110">O código de exemplo a seguir usa o <xref:System.Windows.DataObject.GetDataPresent%28System.Type%29> sobrecarga da consulta a presença de um formato específico de dados por tipo.</span><span class="sxs-lookup"><span data-stu-id="dfa73-110">The following example code uses the <xref:System.Windows.DataObject.GetDataPresent%28System.Type%29> overload to query for the presence of a particular data format by type.</span></span>  
  
### <a name="code"></a><span data-ttu-id="dfa73-111">Código</span><span class="sxs-lookup"><span data-stu-id="dfa73-111">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_QueryDataFormats_Type](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_querydataformats_type)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_QueryDataFormats_Type](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_querydataformats_type)]  
  
## <a name="example"></a><span data-ttu-id="dfa73-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="dfa73-112">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="dfa73-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="dfa73-113">Description</span></span>  
 <span data-ttu-id="dfa73-114">O código de exemplo a seguir usa o <xref:System.Windows.DataObject.GetDataPresent%28System.String%2CSystem.Boolean%29> pela cadeia de caracteres do descritor de sobrecarga para consultar dados e especificando como tratar formatos de dados automática.</span><span class="sxs-lookup"><span data-stu-id="dfa73-114">The following example code uses the <xref:System.Windows.DataObject.GetDataPresent%28System.String%2CSystem.Boolean%29> overload to query for data by descriptor string, and specifying how to treat auto-convertible data formats.</span></span>  
  
### <a name="code"></a><span data-ttu-id="dfa73-115">Código</span><span class="sxs-lookup"><span data-stu-id="dfa73-115">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_QueryDataFormats_Autoconvert](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_querydataformats_autoconvert)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_QueryDataFormats_Autoconvert](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_querydataformats_autoconvert)]  
  
## <a name="see-also"></a><span data-ttu-id="dfa73-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dfa73-116">See also</span></span>

- <xref:System.Windows.IDataObject>
