---
title: "Manipulação de eventos de exibição de dados"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: e5675663-fc91-4e0d-87a9-481b25b64c0f
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 2abade8bbbf5ab8a9d2cf146271e89703ec34cb9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="handling-dataview-events"></a><span data-ttu-id="9cf4c-102">Manipulação de eventos de exibição de dados</span><span class="sxs-lookup"><span data-stu-id="9cf4c-102">Handling DataView Events</span></span>
<span data-ttu-id="9cf4c-103">Você pode usar o <xref:System.Data.DataView.ListChanged> evento o <xref:System.Data.DataView> para determinar se um modo de exibição foi atualizado.</span><span class="sxs-lookup"><span data-stu-id="9cf4c-103">You can use the <xref:System.Data.DataView.ListChanged> event of the <xref:System.Data.DataView> to determine if a view has been updated.</span></span> <span data-ttu-id="9cf4c-104">Atualizações que geram o evento incluem adicionar, excluir ou modificar uma linha da tabela subjacente. Adicionar ou excluir uma coluna para o esquema da tabela subjacente; e uma alteração em uma relação de pai ou filho.</span><span class="sxs-lookup"><span data-stu-id="9cf4c-104">Updates that raise the event include adding, deleting, or modifying a row in the underlying table; adding or deleting a column to the schema of the underlying table; and a change in a parent or child relationship.</span></span> <span data-ttu-id="9cf4c-105">O **ListChanged** evento também notifica se a lista de linhas que você está exibindo mudou significativamente devido ao aplicativo de uma nova ordem de classificação ou um filtro.</span><span class="sxs-lookup"><span data-stu-id="9cf4c-105">The **ListChanged** event also notifies you if the list of rows you are viewing has changed significantly due to the application of a new sort order or a filter.</span></span>  
  
 <span data-ttu-id="9cf4c-106">O **ListChanged** evento implementa o **ListChangedEventHandler** delegar do <xref:System.ComponentModel> namespace e toma como entrada um <xref:System.ComponentModel.ListChangedEventArgs> objeto.</span><span class="sxs-lookup"><span data-stu-id="9cf4c-106">The **ListChanged** event implements the **ListChangedEventHandler** delegate of the <xref:System.ComponentModel> namespace and takes as input a <xref:System.ComponentModel.ListChangedEventArgs> object.</span></span> <span data-ttu-id="9cf4c-107">Você pode determinar o tipo de alteração ocorreu usando o <xref:System.ComponentModel.ListChangedType> valor de enumeração no **ListChangedType** propriedade o **ListChangedEventArgs** objeto.</span><span class="sxs-lookup"><span data-stu-id="9cf4c-107">You can determine what type of change has occurred using the <xref:System.ComponentModel.ListChangedType> enumeration value in the **ListChangedType** property of the **ListChangedEventArgs** object.</span></span> <span data-ttu-id="9cf4c-108">Para alterações que envolvem a adição, exclusão ou movimentação de linhas, o novo índice da linha adicionado ou movido e o índice anterior da linha excluída podem ser acessados usando o **atualizado** propriedade o **ListChangedEventArgs** objeto.</span><span class="sxs-lookup"><span data-stu-id="9cf4c-108">For changes that involve adding, deleting, or moving rows, the new index of the added or moved row and the previous index of the deleted row can be accessed using the **NewIndex** property of the **ListChangedEventArgs** object.</span></span> <span data-ttu-id="9cf4c-109">No caso de uma linha movida, o índice anterior da linha movida pode ser acessado usando o **OldIndex** propriedade o **ListChangedEventArgs** objeto.</span><span class="sxs-lookup"><span data-stu-id="9cf4c-109">In the case of a moved row, the previous index of the moved row can be accessed using the **OldIndex** property of the **ListChangedEventArgs** object.</span></span>  
  
 <span data-ttu-id="9cf4c-110">O **DataViewManager** também expõe um **ListChanged** evento para notificá-lo se uma tabela foi adicionada ou removida, ou se uma alteração foi feita para o **relações** coleção da subjacente **conjunto de dados**.</span><span class="sxs-lookup"><span data-stu-id="9cf4c-110">The **DataViewManager** also exposes a **ListChanged** event to notify you if a table has been added or removed, or if a change has been made to the **Relations** collection of the underlying **DataSet**.</span></span>  
  
 <span data-ttu-id="9cf4c-111">O exemplo de código a seguir mostra como adicionar um **ListChanged** manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="9cf4c-111">The following code example shows how to add a **ListChanged** event handler.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9cf4c-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9cf4c-112">See Also</span></span>  
 <xref:System.Data.DataView>  
 <xref:System.ComponentModel.ListChangedEventHandler>  
 [<span data-ttu-id="9cf4c-113">DataViews</span><span class="sxs-lookup"><span data-stu-id="9cf4c-113">DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)  
 <span data-ttu-id="9cf4c-114">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="9cf4c-114">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917)</span></span>
