---
title: Como listar os formatos de dados em um objeto de dados
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- drag-and-drop [WPF], listing data formats
- DataFormats class [WPF]
- data formats [WPF], listing
ms.assetid: 18e7ba4b-ccef-4815-ae2d-3a32891010c0
ms.openlocfilehash: c0e5917d52d9253737a56307beed69bc0255807c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33543475"
---
# <a name="how-to-list-the-data-formats-in-a-data-object"></a>Como listar os formatos de dados em um objeto de dados
Os exemplos a seguir mostram como usar o <xref:System.Windows.DataObject.GetFormats%2A> sobrecargas do método obtém uma matriz de cadeias de caracteres indicando cada formato de dados que está disponível em um objeto de dados.  
  
## <a name="example"></a>Exemplo  
  
### <a name="description"></a>Descrição  
 O código de exemplo a seguir usa o <xref:System.Windows.DataObject.GetFormats%2A> sobrecarga para obter uma matriz de cadeias de caracteres que indica todos os formatos de dados disponíveis em um objeto de dados (nativo e auto conversíveis).  
  
### <a name="code"></a>Código  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetAllDataFormats](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getalldataformats)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetAllDataFormats](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getalldataformats)]  
  
## <a name="example"></a>Exemplo  
  
### <a name="description"></a>Descrição  
 O código de exemplo a seguir usa o <xref:System.Windows.DataObject.GetFormats%2A> sobrecarga para obter uma matriz de cadeias de caracteres indicando somente formatos de dados disponíveis em um objeto de dados (auto conversíveis formatos de dados são filtrados).  
  
### <a name="code"></a>Código  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetAllDataFormats_NativeOnly](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getalldataformats_nativeonly)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetAllDataFormats_NativeOnly](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getalldataformats_nativeonly)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.IDataObject>  
 [Visão geral de arrastar e soltar](../../../../docs/framework/wpf/advanced/drag-and-drop-overview.md)
