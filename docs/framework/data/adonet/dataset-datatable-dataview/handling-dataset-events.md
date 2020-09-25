---
title: Manipular eventos do DataSet
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 54edefe0-bc38-419b-b486-3d8a0c356f13
ms.openlocfilehash: cc425f3217409a154fd319acb8b1555895cbda54
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91183358"
---
# <a name="handling-dataset-events"></a><span data-ttu-id="25ce3-102">Manipular eventos do DataSet</span><span class="sxs-lookup"><span data-stu-id="25ce3-102">Handling DataSet Events</span></span>

<span data-ttu-id="25ce3-103">O <xref:System.Data.DataSet> objeto fornece três eventos: <xref:System.ComponentModel.MarshalByValueComponent.Disposed> , <xref:System.Data.DataSet.Initialized> e <xref:System.Data.DataSet.MergeFailed> .</span><span class="sxs-lookup"><span data-stu-id="25ce3-103">The <xref:System.Data.DataSet> object provides three events: <xref:System.ComponentModel.MarshalByValueComponent.Disposed>, <xref:System.Data.DataSet.Initialized>, and <xref:System.Data.DataSet.MergeFailed>.</span></span>  
  
## <a name="the-mergefailed-event"></a><span data-ttu-id="25ce3-104">O evento MergeFailed</span><span class="sxs-lookup"><span data-stu-id="25ce3-104">The MergeFailed Event</span></span>  

 <span data-ttu-id="25ce3-105">O evento mais comumente usado do `DataSet` objeto é `MergeFailed` , que é gerado quando o esquema dos `DataSet` objetos que estão sendo mesclados está em conflito.</span><span class="sxs-lookup"><span data-stu-id="25ce3-105">The most commonly used event of the `DataSet` object is `MergeFailed`, which is raised when the schema of the `DataSet` objects being merged are in conflict.</span></span> <span data-ttu-id="25ce3-106">Isso ocorre quando um destino e origem <xref:System.Data.DataRow> têm o mesmo valor de chave primária e a <xref:System.Data.DataSet.EnforceConstraints%2A> propriedade é definida como `true` .</span><span class="sxs-lookup"><span data-stu-id="25ce3-106">This occurs when a target and source <xref:System.Data.DataRow> have the same primary key value, and the <xref:System.Data.DataSet.EnforceConstraints%2A> property is set to `true`.</span></span> <span data-ttu-id="25ce3-107">Por exemplo, se as colunas de chave primária de uma tabela que está sendo mesclada forem as mesmas entre as tabelas nos dois `DataSet` objetos, uma exceção será gerada e o `MergeFailed` evento será gerado.</span><span class="sxs-lookup"><span data-stu-id="25ce3-107">For example, if the primary key columns of a table being merged are the same between the tables in the two `DataSet` objects, an exception is thrown and the `MergeFailed` event is raised.</span></span> <span data-ttu-id="25ce3-108">O <xref:System.Data.MergeFailedEventArgs> objeto passado para o `MergeFailed` evento tem uma <xref:System.Data.MergeFailedEventArgs.Conflict%2A> propriedade que identifica o conflito no esquema entre os dois `DataSet` objetos e uma <xref:System.Data.MergeFailedEventArgs.Table%2A> propriedade que identifica o nome da tabela em conflito.</span><span class="sxs-lookup"><span data-stu-id="25ce3-108">The <xref:System.Data.MergeFailedEventArgs> object passed to the `MergeFailed` event have a <xref:System.Data.MergeFailedEventArgs.Conflict%2A> property that identifies the conflict in schema between the two `DataSet` objects, and a <xref:System.Data.MergeFailedEventArgs.Table%2A> property that identifies the name of the table in conflict.</span></span>  
  
 <span data-ttu-id="25ce3-109">O fragmento de código a seguir demonstra como adicionar um manipulador de eventos para o `MergeFailed` evento.</span><span class="sxs-lookup"><span data-stu-id="25ce3-109">The following code fragment demonstrates how to add an event handler for the `MergeFailed` event.</span></span>  
  
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
  
## <a name="the-initialized-event"></a><span data-ttu-id="25ce3-110">O evento initialized</span><span class="sxs-lookup"><span data-stu-id="25ce3-110">The Initialized Event</span></span>  

 <span data-ttu-id="25ce3-111">O <xref:System.Data.DataSet.Initialized> evento ocorre depois que o `DataSet` Construtor Inicializa uma nova instância do `DataSet` .</span><span class="sxs-lookup"><span data-stu-id="25ce3-111">The <xref:System.Data.DataSet.Initialized> event occurs after the `DataSet` constructor initializes a new instance of the `DataSet`.</span></span>  
  
 <span data-ttu-id="25ce3-112">A <xref:System.Data.DataSet.IsInitialized%2A> propriedade retornará `true` se o `DataSet` tiver concluído a inicialização; caso contrário, retornará `false` .</span><span class="sxs-lookup"><span data-stu-id="25ce3-112">The <xref:System.Data.DataSet.IsInitialized%2A> property returns `true` if the `DataSet` has completed initialization; otherwise it returns `false`.</span></span> <span data-ttu-id="25ce3-113">O <xref:System.Data.DataSet.BeginInit%2A> método, que começa a inicialização de um `DataSet` , define <xref:System.Data.DataSet.IsInitialized%2A> como `false` .</span><span class="sxs-lookup"><span data-stu-id="25ce3-113">The <xref:System.Data.DataSet.BeginInit%2A> method, which begins the initialization of a `DataSet`, sets <xref:System.Data.DataSet.IsInitialized%2A> to `false`.</span></span> <span data-ttu-id="25ce3-114">O <xref:System.Data.DataSet.EndInit%2A> método, que termina a inicialização do `DataSet` , o define como `true` .</span><span class="sxs-lookup"><span data-stu-id="25ce3-114">The <xref:System.Data.DataSet.EndInit%2A> method, which ends the initialization of the `DataSet`, sets it to `true`.</span></span> <span data-ttu-id="25ce3-115">Esses métodos são usados pelo ambiente de design do Visual Studio para inicializar um `DataSet` que está sendo usado por outro componente.</span><span class="sxs-lookup"><span data-stu-id="25ce3-115">These methods are used by the Visual Studio design environment to initialize a `DataSet` that is being used by another component.</span></span> <span data-ttu-id="25ce3-116">Normalmente, você não os usará em seu código.</span><span class="sxs-lookup"><span data-stu-id="25ce3-116">You will not commonly use them in your code.</span></span>  
  
## <a name="the-disposed-event"></a><span data-ttu-id="25ce3-117">O evento Descartado</span><span class="sxs-lookup"><span data-stu-id="25ce3-117">The Disposed Event</span></span>  

 <span data-ttu-id="25ce3-118">`DataSet` é derivado da <xref:System.ComponentModel.MarshalByValueComponent> classe, que expõe o <xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A> método e o <xref:System.ComponentModel.MarshalByValueComponent.Disposed> evento.</span><span class="sxs-lookup"><span data-stu-id="25ce3-118">`DataSet` is derived from the <xref:System.ComponentModel.MarshalByValueComponent> class, which exposes both the <xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A> method and the <xref:System.ComponentModel.MarshalByValueComponent.Disposed> event.</span></span> <span data-ttu-id="25ce3-119">O <xref:System.ComponentModel.MarshalByValueComponent.Disposed> evento adiciona um manipulador de eventos para escutar o evento Descartado no componente.</span><span class="sxs-lookup"><span data-stu-id="25ce3-119">The <xref:System.ComponentModel.MarshalByValueComponent.Disposed> event adds an event handler to listen to the disposed event on the component.</span></span> <span data-ttu-id="25ce3-120">Você pode usar o <xref:System.ComponentModel.MarshalByValueComponent.Disposed> evento de um `DataSet` se quiser executar código quando o <xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A> método for chamado.</span><span class="sxs-lookup"><span data-stu-id="25ce3-120">You can use the <xref:System.ComponentModel.MarshalByValueComponent.Disposed> event of a `DataSet` if you want to execute code when the <xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A> method is called.</span></span> <span data-ttu-id="25ce3-121"><xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A> Libera os recursos usados pelo <xref:System.ComponentModel.MarshalByValueComponent> .</span><span class="sxs-lookup"><span data-stu-id="25ce3-121"><xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A> releases the resources used by the <xref:System.ComponentModel.MarshalByValueComponent>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="25ce3-122">Os `DataSet` `DataTable` objetos e herdam de <xref:System.ComponentModel.MarshalByValueComponent> e dão suporte à <xref:System.Runtime.Serialization.ISerializable> interface para comunicação remota.</span><span class="sxs-lookup"><span data-stu-id="25ce3-122">The `DataSet` and `DataTable` objects inherit from <xref:System.ComponentModel.MarshalByValueComponent> and support the <xref:System.Runtime.Serialization.ISerializable> interface for remoting.</span></span> <span data-ttu-id="25ce3-123">Esses são os únicos objetos ADO.NET que podem ser remotos.</span><span class="sxs-lookup"><span data-stu-id="25ce3-123">These are the only ADO.NET objects that can be remoted.</span></span> <span data-ttu-id="25ce3-124">Para obter mais informações, consulte [comunicação remota do .net](/previous-versions/dotnet/netframework-4.0/72x4h507(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="25ce3-124">For more information, see [.NET Remoting](/previous-versions/dotnet/netframework-4.0/72x4h507(v=vs.100)).</span></span>  
  
 <span data-ttu-id="25ce3-125">Para obter informações sobre outros eventos disponíveis ao trabalhar com um `DataSet` , consulte [manipulando eventos de DataTable](handling-datatable-events.md) e [manipulando eventos de DataAdapter](../handling-dataadapter-events.md).</span><span class="sxs-lookup"><span data-stu-id="25ce3-125">For information about other events available when working with a `DataSet`, see [Handling DataTable Events](handling-datatable-events.md) and [Handling DataAdapter Events](../handling-dataadapter-events.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25ce3-126">Veja também</span><span class="sxs-lookup"><span data-stu-id="25ce3-126">See also</span></span>

- [<span data-ttu-id="25ce3-127">DataSets, DataTables e DataViews</span><span class="sxs-lookup"><span data-stu-id="25ce3-127">DataSets, DataTables, and DataViews</span></span>](index.md)
- <span data-ttu-id="25ce3-128">[Validando dados](/previous-versions/visualstudio/visual-studio-2013/t3b36awf(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="25ce3-128">[Validating Data](/previous-versions/visualstudio/visual-studio-2013/t3b36awf(v=vs.120))</span></span>
- [<span data-ttu-id="25ce3-129">Recuperando e modificando dados no ADO.NET</span><span class="sxs-lookup"><span data-stu-id="25ce3-129">Retrieving and Modifying Data in ADO.NET</span></span>](../retrieving-and-modifying-data.md)
- [<span data-ttu-id="25ce3-130">Visão geral do ADO.NET</span><span class="sxs-lookup"><span data-stu-id="25ce3-130">ADO.NET Overview</span></span>](../ado-net-overview.md)
