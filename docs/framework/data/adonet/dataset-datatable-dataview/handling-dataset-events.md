---
title: Manipulação de eventos do conjunto de dados
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 54edefe0-bc38-419b-b486-3d8a0c356f13
ms.openlocfilehash: 486f38e2900eb85dbffbb4f9a9d0e6753267e32b
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32758315"
---
# <a name="handling-dataset-events"></a><span data-ttu-id="2f945-102">Manipulação de eventos do conjunto de dados</span><span class="sxs-lookup"><span data-stu-id="2f945-102">Handling DataSet Events</span></span>
<span data-ttu-id="2f945-103">O <xref:System.Data.DataSet> objeto fornece três eventos: <xref:System.ComponentModel.MarshalByValueComponent.Disposed>, <xref:System.Data.DataSet.Initialized>, e <xref:System.Data.DataSet.MergeFailed>.</span><span class="sxs-lookup"><span data-stu-id="2f945-103">The <xref:System.Data.DataSet> object provides three events: <xref:System.ComponentModel.MarshalByValueComponent.Disposed>, <xref:System.Data.DataSet.Initialized>, and <xref:System.Data.DataSet.MergeFailed>.</span></span>  
  
## <a name="the-mergefailed-event"></a><span data-ttu-id="2f945-104">O evento MergeFailed</span><span class="sxs-lookup"><span data-stu-id="2f945-104">The MergeFailed Event</span></span>  
 <span data-ttu-id="2f945-105">Evento mais usados o `DataSet` objeto é `MergeFailed`, que é gerado quando o esquema do `DataSet` objetos sendo mesclados estão em conflito.</span><span class="sxs-lookup"><span data-stu-id="2f945-105">The most commonly used event of the `DataSet` object is `MergeFailed`, which is raised when the schema of the `DataSet` objects being merged are in conflict.</span></span> <span data-ttu-id="2f945-106">Isso ocorre quando uma origem e destino <xref:System.Data.DataRow> têm o mesmo valor de chave primário e o <xref:System.Data.DataSet.EnforceConstraints%2A> está definida como `true`.</span><span class="sxs-lookup"><span data-stu-id="2f945-106">This occurs when a target and source <xref:System.Data.DataRow> have the same primary key value, and the <xref:System.Data.DataSet.EnforceConstraints%2A> property is set to `true`.</span></span> <span data-ttu-id="2f945-107">Por exemplo, se as colunas de chave primária de uma tabela que está sendo mesclado são os mesmos entre as tabelas nas duas `DataSet` objetos, uma exceção será lançada e a `MergeFailed` é gerado.</span><span class="sxs-lookup"><span data-stu-id="2f945-107">For example, if the primary key columns of a table being merged are the same between the tables in the two `DataSet` objects, an exception is thrown and the `MergeFailed` event is raised.</span></span> <span data-ttu-id="2f945-108">O <xref:System.Data.MergeFailedEventArgs> objeto passado para o `MergeFailed` evento tem um <xref:System.Data.MergeFailedEventArgs.Conflict%2A> propriedade que identifica o conflito no esquema entre os dois `DataSet` objetos e um <xref:System.Data.MergeFailedEventArgs.Table%2A> propriedade que identifica o nome da tabela em conflito.</span><span class="sxs-lookup"><span data-stu-id="2f945-108">The <xref:System.Data.MergeFailedEventArgs> object passed to the `MergeFailed` event have a <xref:System.Data.MergeFailedEventArgs.Conflict%2A> property that identifies the conflict in schema between the two `DataSet` objects, and a <xref:System.Data.MergeFailedEventArgs.Table%2A> property that identifies the name of the table in conflict.</span></span>  
  
 <span data-ttu-id="2f945-109">O fragmento de código a seguir demonstra como adicionar um manipulador de eventos para o `MergeFailed` evento.</span><span class="sxs-lookup"><span data-stu-id="2f945-109">The following code fragment demonstrates how to add an event handler for the `MergeFailed` event.</span></span>  
  
```vb  
AddHandler workDS.MergeFailed, New MergeFailedEventHandler( _  
  AddressOf DataSetMergeFailed)  
  
Private Shared Sub DataSetMergeFailed(  _  
  sender As Object,args As MergeFailedEventArgs)  
  Console.WriteLine("Merge failed for table " & args.Table.TableName)  
  Console.WriteLine("Conflict = " & args.Conflict)  
End Sub  
```  
  
```csharp  
workDS.MergeFailed += new MergeFailedEventHandler(DataSetMergeFailed);  
  
private static void DataSetMergeFailed(  
  object sender, MergeFailedEventArgs args)  
{  
  Console.WriteLine("Merge failed for table " + args.Table.TableName);  
  Console.WriteLine("Conflict = " + args.Conflict);  
}  
```  
  
## <a name="the-initialized-event"></a><span data-ttu-id="2f945-110">O evento inicializado</span><span class="sxs-lookup"><span data-stu-id="2f945-110">The Initialized Event</span></span>  
 <span data-ttu-id="2f945-111">O <xref:System.Data.DataSet.Initialized> evento ocorre após o `DataSet` construtor inicializa uma nova instância do `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="2f945-111">The <xref:System.Data.DataSet.Initialized> event occurs after the `DataSet` constructor initializes a new instance of the `DataSet`.</span></span>  
  
 <span data-ttu-id="2f945-112">O <xref:System.Data.DataSet.IsInitialized%2A> propriedade retorna `true` se o `DataSet` concluiu a inicialização; caso contrário, ele retorna `false`.</span><span class="sxs-lookup"><span data-stu-id="2f945-112">The <xref:System.Data.DataSet.IsInitialized%2A> property returns `true` if the `DataSet` has completed initialization; otherwise it returns `false`.</span></span> <span data-ttu-id="2f945-113">O <xref:System.Data.DataSet.BeginInit%2A> método, que inicia a inicialização de um `DataSet`, define <xref:System.Data.DataSet.IsInitialized%2A> para `false`.</span><span class="sxs-lookup"><span data-stu-id="2f945-113">The <xref:System.Data.DataSet.BeginInit%2A> method, which begins the initialization of a `DataSet`, sets <xref:System.Data.DataSet.IsInitialized%2A> to `false`.</span></span> <span data-ttu-id="2f945-114">O <xref:System.Data.DataSet.EndInit%2A> método, que termina a inicialização do `DataSet`, define-o como `true`.</span><span class="sxs-lookup"><span data-stu-id="2f945-114">The <xref:System.Data.DataSet.EndInit%2A> method, which ends the initialization of the `DataSet`, sets it to `true`.</span></span> <span data-ttu-id="2f945-115">Esses métodos são usados pelo ambiente de design do Visual Studio para inicializar um `DataSet` que está sendo usado por outro componente.</span><span class="sxs-lookup"><span data-stu-id="2f945-115">These methods are used by the Visual Studio design environment to initialize a `DataSet` that is being used by another component.</span></span> <span data-ttu-id="2f945-116">Você não usará frequência-los em seu código.</span><span class="sxs-lookup"><span data-stu-id="2f945-116">You will not commonly use them in your code.</span></span>  
  
## <a name="the-disposed-event"></a><span data-ttu-id="2f945-117">O evento descartado</span><span class="sxs-lookup"><span data-stu-id="2f945-117">The Disposed Event</span></span>  
 <span data-ttu-id="2f945-118">`DataSet` é derivado do <xref:System.ComponentModel.MarshalByValueComponent> classe que expõe ambos o <xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A> método e o <xref:System.ComponentModel.MarshalByValueComponent.Disposed> evento.</span><span class="sxs-lookup"><span data-stu-id="2f945-118">`DataSet` is derived from the <xref:System.ComponentModel.MarshalByValueComponent> class, which exposes both the <xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A> method and the <xref:System.ComponentModel.MarshalByValueComponent.Disposed> event.</span></span> <span data-ttu-id="2f945-119">O <xref:System.ComponentModel.MarshalByValueComponent.Disposed> evento adiciona um manipulador de eventos para escutar o evento descartado no componente.</span><span class="sxs-lookup"><span data-stu-id="2f945-119">The <xref:System.ComponentModel.MarshalByValueComponent.Disposed> event adds an event handler to listen to the disposed event on the component.</span></span> <span data-ttu-id="2f945-120">Você pode usar o <xref:System.ComponentModel.MarshalByValueComponent.Disposed> eventos de um `DataSet` se você quiser executar código quando o <xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A> método é chamado.</span><span class="sxs-lookup"><span data-stu-id="2f945-120">You can use the <xref:System.ComponentModel.MarshalByValueComponent.Disposed> event of a `DataSet` if you want to execute code when the <xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A> method is called.</span></span> <span data-ttu-id="2f945-121"><xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A> libera os recursos usados pelo <xref:System.ComponentModel.MarshalByValueComponent>.</span><span class="sxs-lookup"><span data-stu-id="2f945-121"><xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A> releases the resources used by the <xref:System.ComponentModel.MarshalByValueComponent>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2f945-122">O `DataSet` e `DataTable` objetos herdam <xref:System.ComponentModel.MarshalByValueComponent> e suporte a <xref:System.Runtime.Serialization.ISerializable> interface de comunicação remota.</span><span class="sxs-lookup"><span data-stu-id="2f945-122">The `DataSet` and `DataTable` objects inherit from <xref:System.ComponentModel.MarshalByValueComponent> and support the <xref:System.Runtime.Serialization.ISerializable> interface for remoting.</span></span> <span data-ttu-id="2f945-123">Esses são os únicos objetos ADO.NET que podem ser remotos.</span><span class="sxs-lookup"><span data-stu-id="2f945-123">These are the only ADO.NET objects that can be remoted.</span></span> <span data-ttu-id="2f945-124">Para obter mais informações, consulte [objetos remotos](http://msdn.microsoft.com/library/515686e6-0a8d-42f7-8188-73abede57c58).</span><span class="sxs-lookup"><span data-stu-id="2f945-124">For more information, see [Remote Objects](http://msdn.microsoft.com/library/515686e6-0a8d-42f7-8188-73abede57c58).</span></span>  
  
 <span data-ttu-id="2f945-125">Para obter informações sobre outros eventos disponíveis ao trabalhar com um `DataSet`, consulte [manipulando eventos de DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-datatable-events.md) e [manipulando eventos de DataAdapter](../../../../../docs/framework/data/adonet/handling-dataadapter-events.md).</span><span class="sxs-lookup"><span data-stu-id="2f945-125">For information about other events available when working with a `DataSet`, see [Handling DataTable Events](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-datatable-events.md) and [Handling DataAdapter Events](../../../../../docs/framework/data/adonet/handling-dataadapter-events.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f945-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2f945-126">See Also</span></span>  
 <span data-ttu-id="2f945-127">[DataSets, DataTables, and DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md) (DataSets, DataTables e DataViews)</span><span class="sxs-lookup"><span data-stu-id="2f945-127">[DataSets, DataTables, and DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)</span></span>  
 [<span data-ttu-id="2f945-128">Validando dados</span><span class="sxs-lookup"><span data-stu-id="2f945-128">Validating Data</span></span>](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)  
 <span data-ttu-id="2f945-129">[Retrieving and Modifying Data in ADO.NET](../../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md) (Recuperando e modificando dados no ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="2f945-129">[Retrieving and Modifying Data in ADO.NET](../../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)</span></span>  
 <span data-ttu-id="2f945-130">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="2f945-130">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917)</span></span>
