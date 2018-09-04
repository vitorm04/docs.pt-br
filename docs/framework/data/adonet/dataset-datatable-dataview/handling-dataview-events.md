---
title: Manipulação de eventos de DataView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e5675663-fc91-4e0d-87a9-481b25b64c0f
ms.openlocfilehash: 2f30a578c5233e8b86a165dd220efd45348c5042
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43541088"
---
# <a name="handling-dataview-events"></a><span data-ttu-id="64684-102">Manipulação de eventos de DataView</span><span class="sxs-lookup"><span data-stu-id="64684-102">Handling DataView Events</span></span>
<span data-ttu-id="64684-103">Você pode usar o <xref:System.Data.DataView.ListChanged> eventos do <xref:System.Data.DataView> para determinar se um modo de exibição foi atualizado.</span><span class="sxs-lookup"><span data-stu-id="64684-103">You can use the <xref:System.Data.DataView.ListChanged> event of the <xref:System.Data.DataView> to determine if a view has been updated.</span></span> <span data-ttu-id="64684-104">As atualizações que acionar o evento incluem adição, exclusão ou modificação de uma linha da tabela subjacente. Adicionar ou excluir uma coluna para o esquema da tabela subjacente; e uma alteração em uma relação de pai ou filho.</span><span class="sxs-lookup"><span data-stu-id="64684-104">Updates that raise the event include adding, deleting, or modifying a row in the underlying table; adding or deleting a column to the schema of the underlying table; and a change in a parent or child relationship.</span></span> <span data-ttu-id="64684-105">O **ListChanged** evento também notifica se a lista de linhas que você está exibindo mudou significativamente devido ao aplicativo de uma nova ordem de classificação ou um filtro.</span><span class="sxs-lookup"><span data-stu-id="64684-105">The **ListChanged** event also notifies you if the list of rows you are viewing has changed significantly due to the application of a new sort order or a filter.</span></span>  
  
 <span data-ttu-id="64684-106">O **ListChanged** evento implementa o **ListChangedEventHandler** delegar da <xref:System.ComponentModel> namespace e o utiliza como entrada um <xref:System.ComponentModel.ListChangedEventArgs> objeto.</span><span class="sxs-lookup"><span data-stu-id="64684-106">The **ListChanged** event implements the **ListChangedEventHandler** delegate of the <xref:System.ComponentModel> namespace and takes as input a <xref:System.ComponentModel.ListChangedEventArgs> object.</span></span> <span data-ttu-id="64684-107">Você pode determinar o tipo de alteração ocorreu usando o <xref:System.ComponentModel.ListChangedType> valor de enumeração na **ListChangedType** propriedade do **ListChangedEventArgs** objeto.</span><span class="sxs-lookup"><span data-stu-id="64684-107">You can determine what type of change has occurred using the <xref:System.ComponentModel.ListChangedType> enumeration value in the **ListChangedType** property of the **ListChangedEventArgs** object.</span></span> <span data-ttu-id="64684-108">Para que as alterações que envolvem a adição, exclusão ou movimentação de linhas, o novo índice da linha adicionado ou movido e o índice anterior da linha excluída podem ser acessados usando o **atualizado** propriedade do **ListChangedEventArgs** objeto.</span><span class="sxs-lookup"><span data-stu-id="64684-108">For changes that involve adding, deleting, or moving rows, the new index of the added or moved row and the previous index of the deleted row can be accessed using the **NewIndex** property of the **ListChangedEventArgs** object.</span></span> <span data-ttu-id="64684-109">No caso de uma linha movida, o índice anterior da linha movida pode ser acessado usando o **OldIndex** propriedade da **ListChangedEventArgs** objeto.</span><span class="sxs-lookup"><span data-stu-id="64684-109">In the case of a moved row, the previous index of the moved row can be accessed using the **OldIndex** property of the **ListChangedEventArgs** object.</span></span>  
  
 <span data-ttu-id="64684-110">O **DataViewManager** também expõe uma **ListChanged** eventos para notificá-lo se uma tabela foi adicionada ou removida, ou se uma alteração foi feita para o **relações** coleção da subjacente **conjunto de dados**.</span><span class="sxs-lookup"><span data-stu-id="64684-110">The **DataViewManager** also exposes a **ListChanged** event to notify you if a table has been added or removed, or if a change has been made to the **Relations** collection of the underlying **DataSet**.</span></span>  
  
 <span data-ttu-id="64684-111">O exemplo de código a seguir mostra como adicionar um **ListChanged** manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="64684-111">The following code example shows how to add a **ListChanged** event handler.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="64684-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="64684-112">See Also</span></span>  
 <xref:System.Data.DataView>  
 <xref:System.ComponentModel.ListChangedEventHandler>  
 [<span data-ttu-id="64684-113">DataViews</span><span class="sxs-lookup"><span data-stu-id="64684-113">DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)  
 <span data-ttu-id="64684-114">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="64684-114">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917)</span></span>
