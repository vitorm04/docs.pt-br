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
ms.openlocfilehash: 603ecf8945e461f281a49b430de8342c41203463
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54546905"
---
# <a name="how-to-determine-if-a-data-format-is-present-in-a-data-object"></a>Como: Determinar se um formato de dados está presente em um objeto de dados
Os exemplos a seguir mostram como usar os vários <xref:System.Windows.DataObject.GetDataPresent%2A> sobrecargas do método para consultar se um formato específico de dados está presente em um objeto de dados.  
  
## <a name="example"></a>Exemplo  
  
### <a name="description"></a>Descrição  
 O código de exemplo a seguir usa o <xref:System.Windows.DataObject.GetDataPresent%28System.String%29> sobrecarga da consulta a presença de um formato específico de dados pela cadeia de caracteres do descritor.  
  
### <a name="code"></a>Código  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_QueryDataFormats_String](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_querydataformats_string)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_QueryDataFormats_String](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_querydataformats_string)]  
  
## <a name="example"></a>Exemplo  
  
### <a name="description"></a>Descrição  
 O código de exemplo a seguir usa o <xref:System.Windows.DataObject.GetDataPresent%28System.Type%29> sobrecarga da consulta a presença de um formato específico de dados por tipo.  
  
### <a name="code"></a>Código  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_QueryDataFormats_Type](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_querydataformats_type)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_QueryDataFormats_Type](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_querydataformats_type)]  
  
## <a name="example"></a>Exemplo  
  
### <a name="description"></a>Descrição  
 O código de exemplo a seguir usa o <xref:System.Windows.DataObject.GetDataPresent%28System.String%2CSystem.Boolean%29> pela cadeia de caracteres do descritor de sobrecarga para consultar dados e especificando como tratar formatos de dados automática.  
  
### <a name="code"></a>Código  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_QueryDataFormats_Autoconvert](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_querydataformats_autoconvert)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_QueryDataFormats_Autoconvert](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_querydataformats_autoconvert)]  
  
## <a name="see-also"></a>Consulte também
- <xref:System.Windows.IDataObject>
