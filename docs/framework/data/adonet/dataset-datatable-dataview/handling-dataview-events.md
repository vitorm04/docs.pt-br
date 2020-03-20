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
# <a name="handling-dataview-events"></a><span data-ttu-id="fd804-102">Manipulação de eventos de DataView</span><span class="sxs-lookup"><span data-stu-id="fd804-102">Handling DataView Events</span></span>
<span data-ttu-id="fd804-103">Você pode <xref:System.Data.DataView.ListChanged> usar o <xref:System.Data.DataView> evento do para determinar se uma exibição foi atualizada.</span><span class="sxs-lookup"><span data-stu-id="fd804-103">You can use the <xref:System.Data.DataView.ListChanged> event of the <xref:System.Data.DataView> to determine if a view has been updated.</span></span> <span data-ttu-id="fd804-104">As atualizações que levantam o evento incluem a adição, exclusão ou modificação de uma linha na tabela subjacente; adicionando ou excluindo uma coluna ao esquema da tabela subjacente; e uma mudança na relação entre pais e filhos.</span><span class="sxs-lookup"><span data-stu-id="fd804-104">Updates that raise the event include adding, deleting, or modifying a row in the underlying table; adding or deleting a column to the schema of the underlying table; and a change in a parent or child relationship.</span></span> <span data-ttu-id="fd804-105">O evento **ListChanged** também notifica se a lista de linhas que você está visualizando foi alterada significativamente devido à aplicação de uma nova ordem de classificação ou um filtro.</span><span class="sxs-lookup"><span data-stu-id="fd804-105">The **ListChanged** event also notifies you if the list of rows you are viewing has changed significantly due to the application of a new sort order or a filter.</span></span>  
  
 <span data-ttu-id="fd804-106">O evento **ListChanged** implementa o delegado <xref:System.ComponentModel> **ListChangedEventHandler** do <xref:System.ComponentModel.ListChangedEventArgs> namespace e toma como entrada um objeto.</span><span class="sxs-lookup"><span data-stu-id="fd804-106">The **ListChanged** event implements the **ListChangedEventHandler** delegate of the <xref:System.ComponentModel> namespace and takes as input a <xref:System.ComponentModel.ListChangedEventArgs> object.</span></span> <span data-ttu-id="fd804-107">Você pode determinar que tipo de <xref:System.ComponentModel.ListChangedType> alteração ocorreu usando o valor de enumeração na propriedade **ListChangedType** do objeto **ListChangedEventArgs.**</span><span class="sxs-lookup"><span data-stu-id="fd804-107">You can determine what type of change has occurred using the <xref:System.ComponentModel.ListChangedType> enumeration value in the **ListChangedType** property of the **ListChangedEventArgs** object.</span></span> <span data-ttu-id="fd804-108">Para alterações que envolvam adicionar, excluir ou mover linhas, o novo índice da linha adicionada ou movida e o índice anterior da linha excluída podem ser acessados usando a propriedade **NewIndex** do objeto **ListChangedEventArgs.**</span><span class="sxs-lookup"><span data-stu-id="fd804-108">For changes that involve adding, deleting, or moving rows, the new index of the added or moved row and the previous index of the deleted row can be accessed using the **NewIndex** property of the **ListChangedEventArgs** object.</span></span> <span data-ttu-id="fd804-109">No caso de uma linha movida, o índice anterior da linha movida pode ser acessado usando a propriedade **OldIndex** do objeto **ListChangedEventArgs.**</span><span class="sxs-lookup"><span data-stu-id="fd804-109">In the case of a moved row, the previous index of the moved row can be accessed using the **OldIndex** property of the **ListChangedEventArgs** object.</span></span>  
  
 <span data-ttu-id="fd804-110">O **DataViewManager** também expõe um evento ListChanged para notificá-lo se uma tabela foi adicionada ou removida, ou se uma alteração foi feita na coleção **ListChanged** **Relações** do Conjunto de **Dados**subjacente .</span><span class="sxs-lookup"><span data-stu-id="fd804-110">The **DataViewManager** also exposes a **ListChanged** event to notify you if a table has been added or removed, or if a change has been made to the **Relations** collection of the underlying **DataSet**.</span></span>  
  
 <span data-ttu-id="fd804-111">O exemplo de código a seguir mostra como adicionar um manipulador de eventos **ListChanged.**</span><span class="sxs-lookup"><span data-stu-id="fd804-111">The following code example shows how to add a **ListChanged** event handler.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="fd804-112">Confira também</span><span class="sxs-lookup"><span data-stu-id="fd804-112">See also</span></span>

- <xref:System.Data.DataView>
- <xref:System.ComponentModel.ListChangedEventHandler>
- [<span data-ttu-id="fd804-113">DataViews</span><span class="sxs-lookup"><span data-stu-id="fd804-113">DataViews</span></span>](dataviews.md)
- [<span data-ttu-id="fd804-114">Visão geral do ADO.NET</span><span class="sxs-lookup"><span data-stu-id="fd804-114">ADO.NET Overview</span></span>](../ado-net-overview.md)
