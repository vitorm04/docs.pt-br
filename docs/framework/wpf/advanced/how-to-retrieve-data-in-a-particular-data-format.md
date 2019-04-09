---
title: 'Como: Recuperar dados em um formato de dados específico'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- drag-and-drop [WPF], retrieving data
- DataFormats class [WPF], retrieving data
- DataObject class [WPF], retrieving data
ms.assetid: a625acf3-1144-44cd-add7-456aefc3859f
ms.openlocfilehash: b3ec1b8fa873fd449956912e9e77e98b0362cb0e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59080014"
---
# <a name="how-to-retrieve-data-in-a-particular-data-format"></a>Como: Recuperar dados em um formato de dados específico
Os exemplos a seguir mostram como recuperar dados de um objeto de dados em um formato especificado.  
  
## <a name="example"></a>Exemplo  
  
### <a name="description"></a>Descrição  
 O código de exemplo a seguir usa o <xref:System.Windows.DataObject.GetDataPresent%28System.String%29> sobrecarga para primeiro verificar se um dado especificado formato está disponível (modo nativo ou por conversão automática); se o formato especificado estiver disponível, o exemplo recupera os dados usando o <xref:System.Windows.DataObject.GetData%28System.String%29> método.  
  
### <a name="code"></a>Código  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getspecificdataformat)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getspecificdataformat)]  
  
## <a name="example"></a>Exemplo  
  
### <a name="description"></a>Descrição  
 O código de exemplo a seguir usa o <xref:System.Windows.DataObject.GetDataPresent%28System.String%2CSystem.Boolean%29> sobrecarga para primeiro verificar se um formato de dados especificado está disponível nativamente (formatos de dados automática são filtrados); se o formato especificado estiver disponível, o exemplo recupera os dados usando o <xref:System.Windows.DataObject.GetData%28System.String%29>método.  
  
### <a name="code"></a>Código  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat_Native](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getspecificdataformat_native)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat_Native](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getspecificdataformat_native)]  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.IDataObject>
- [Visão geral de arrastar e soltar](drag-and-drop-overview.md)
