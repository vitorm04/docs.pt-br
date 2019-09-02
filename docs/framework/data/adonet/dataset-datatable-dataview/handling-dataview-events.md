---
title: Manipulação de eventos de DataView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e5675663-fc91-4e0d-87a9-481b25b64c0f
ms.openlocfilehash: b3a1077bff9bf457b4aef0b05357d4a9260f8973
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70204816"
---
# <a name="handling-dataview-events"></a>Manipulação de eventos de DataView
Você pode usar o <xref:System.Data.DataView.ListChanged> evento <xref:System.Data.DataView> do para determinar se um modo de exibição foi atualizado. As atualizações que geram o evento incluem adicionar, excluir ou modificar uma linha na tabela subjacente; adicionando ou excluindo uma coluna para o esquema da tabela subjacente; e uma alteração em uma relação pai ou filho. O evento **ListChanged** também notifica se a lista de linhas que você está exibindo mudou significativamente devido ao aplicativo de uma nova ordem de classificação ou de um filtro.  
  
 O evento **ListChanged** implementa o <xref:System.ComponentModel> delegado ListChangedEventHandler do namespace e usa como entrada um <xref:System.ComponentModel.ListChangedEventArgs> objeto. Você pode determinar que tipo de alteração ocorreu usando o <xref:System.ComponentModel.ListChangedType> valor de enumeração na propriedade **ListChangedType** do objeto **ListChangedEventArgs** . Para alterações que envolvem adicionar, excluir ou mover linhas, o novo índice da linha adicionada ou movida e o índice anterior da linha excluída podem ser acessados usando a propriedade **NewIndex** do objeto **ListChangedEventArgs** . No caso de uma linha movida, o índice anterior da linha movida pode ser acessado usando a propriedade **OldIndex** do objeto **ListChangedEventArgs** .  
  
 O **DataViewManager** também expõe um evento **ListChanged** para notificá-lo se uma tabela tiver sido adicionada ou removida, ou se uma alteração tiver sido feita na coleção **Relations** do **DataSet**subjacente.  
  
 O exemplo de código a seguir mostra como adicionar um manipulador de eventos **ListChanged** .  
  
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
  
## <a name="see-also"></a>Consulte também

- <xref:System.Data.DataView>
- <xref:System.ComponentModel.ListChangedEventHandler>
- [DataViews](dataviews.md)
- [ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
