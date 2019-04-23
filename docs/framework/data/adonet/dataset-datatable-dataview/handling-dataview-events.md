---
title: Manipulação de eventos de DataView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e5675663-fc91-4e0d-87a9-481b25b64c0f
ms.openlocfilehash: 6c2e554b7e6bde3e82190f70723f272b0d39a18a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59152406"
---
# <a name="handling-dataview-events"></a>Manipulação de eventos de DataView
Você pode usar o <xref:System.Data.DataView.ListChanged> eventos do <xref:System.Data.DataView> para determinar se um modo de exibição foi atualizado. As atualizações que acionar o evento incluem adição, exclusão ou modificação de uma linha da tabela subjacente. Adicionar ou excluir uma coluna para o esquema da tabela subjacente; e uma alteração em uma relação de pai ou filho. O **ListChanged** evento também notifica se a lista de linhas que você está exibindo mudou significativamente devido ao aplicativo de uma nova ordem de classificação ou um filtro.  
  
 O **ListChanged** evento implementa o **ListChangedEventHandler** delegar da <xref:System.ComponentModel> namespace e o utiliza como entrada um <xref:System.ComponentModel.ListChangedEventArgs> objeto. Você pode determinar o tipo de alteração ocorreu usando o <xref:System.ComponentModel.ListChangedType> valor de enumeração na **ListChangedType** propriedade do **ListChangedEventArgs** objeto. Para que as alterações que envolvem a adição, exclusão ou movimentação de linhas, o novo índice da linha adicionado ou movido e o índice anterior da linha excluída podem ser acessados usando o **atualizado** propriedade do **ListChangedEventArgs** objeto. No caso de uma linha movida, o índice anterior da linha movida pode ser acessado usando o **OldIndex** propriedade da **ListChangedEventArgs** objeto.  
  
 O **DataViewManager** também expõe uma **ListChanged** eventos para notificá-lo se uma tabela foi adicionada ou removida, ou se uma alteração foi feita para o **relações** coleção da subjacente **conjunto de dados**.  
  
 O exemplo de código a seguir mostra como adicionar um **ListChanged** manipulador de eventos.  
  
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
- [DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)
- [ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
