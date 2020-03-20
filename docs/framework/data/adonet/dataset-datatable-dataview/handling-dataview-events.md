---
title: Manipulação de eventos de DataView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e5675663-fc91-4e0d-87a9-481b25b64c0f
ms.openlocfilehash: b625fad846c4c6cf008843bff1f6b0eabe0e1de4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151098"
---
# <a name="handling-dataview-events"></a>Manipulação de eventos de DataView
Você pode <xref:System.Data.DataView.ListChanged> usar o <xref:System.Data.DataView> evento do para determinar se uma exibição foi atualizada. As atualizações que levantam o evento incluem a adição, exclusão ou modificação de uma linha na tabela subjacente; adicionando ou excluindo uma coluna ao esquema da tabela subjacente; e uma mudança na relação entre pais e filhos. O evento **ListChanged** também notifica se a lista de linhas que você está visualizando foi alterada significativamente devido à aplicação de uma nova ordem de classificação ou um filtro.  
  
 O evento **ListChanged** implementa o delegado <xref:System.ComponentModel> **ListChangedEventHandler** do <xref:System.ComponentModel.ListChangedEventArgs> namespace e toma como entrada um objeto. Você pode determinar que tipo de <xref:System.ComponentModel.ListChangedType> alteração ocorreu usando o valor de enumeração na propriedade **ListChangedType** do objeto **ListChangedEventArgs.** Para alterações que envolvam adicionar, excluir ou mover linhas, o novo índice da linha adicionada ou movida e o índice anterior da linha excluída podem ser acessados usando a propriedade **NewIndex** do objeto **ListChangedEventArgs.** No caso de uma linha movida, o índice anterior da linha movida pode ser acessado usando a propriedade **OldIndex** do objeto **ListChangedEventArgs.**  
  
 O **DataViewManager** também expõe um evento ListChanged para notificá-lo se uma tabela foi adicionada ou removida, ou se uma alteração foi feita na coleção **ListChanged** **Relações** do Conjunto de **Dados**subjacente .  
  
 O exemplo de código a seguir mostra como adicionar um manipulador de eventos **ListChanged.**  
  
```vb  
AddHandler custView.ListChanged, _  
  New System.ComponentModel.ListChangedEventHandler( _  
  AddressOf OnListChanged)  
  
Private Shared Sub OnListChanged( _  
  sender As Object, args As System.ComponentModel.ListChangedEventArgs)  
  Console.WriteLine("ListChanged:")  
  Console.WriteLine(vbTab & "    Type = " & _  
    System.Enum.GetName(args.ListChangedType.GetType(), _  
    args.ListChangedType))  
  Console.WriteLine(vbTab & "OldIndex = " & args.OldIndex)  
  Console.WriteLine(vbTab & "NewIndex = " & args.NewIndex)  
End Sub  
```  
  
```csharp  
custView.ListChanged  += new
  System.ComponentModel.ListChangedEventHandler(OnListChanged);  
  
protected static void OnListChanged(object sender,
  System.ComponentModel.ListChangedEventArgs args)  
{  
  Console.WriteLine("ListChanged:");  
  Console.WriteLine("\t    Type = " + args.ListChangedType);  
  Console.WriteLine("\tOldIndex = " + args.OldIndex);  
  Console.WriteLine("\tNewIndex = " + args.NewIndex);  
}  
```  
  
## <a name="see-also"></a>Confira também

- <xref:System.Data.DataView>
- <xref:System.ComponentModel.ListChangedEventHandler>
- [DataViews](dataviews.md)
- [Visão geral do ADO.NET](../ado-net-overview.md)
