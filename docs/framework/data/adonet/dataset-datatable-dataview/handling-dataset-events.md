---
title: Manipular eventos do DataSet
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 54edefe0-bc38-419b-b486-3d8a0c356f13
ms.openlocfilehash: 5e1de3effcae5700aa25f5dbb84f2dec3a0b20f1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59195274"
---
# <a name="handling-dataset-events"></a>Manipular eventos do DataSet
O <xref:System.Data.DataSet> objeto fornece três eventos: <xref:System.ComponentModel.MarshalByValueComponent.Disposed>, <xref:System.Data.DataSet.Initialized>, e <xref:System.Data.DataSet.MergeFailed>.  
  
## <a name="the-mergefailed-event"></a>O evento MergeFailed  
 Usado com mais frequência eventos do `DataSet` objeto é `MergeFailed`, que é gerado quando o esquema do `DataSet` objetos sendo mesclados estão em conflito. Isso ocorre quando uma origem e destino <xref:System.Data.DataRow> têm o mesmo valor de chave primário e o <xref:System.Data.DataSet.EnforceConstraints%2A> estiver definida como `true`. Por exemplo, se as colunas de chave primárias de uma tabela que está sendo mesclada são as mesmas entre as tabelas nas duas `DataSet` objetos, uma exceção é lançada e o `MergeFailed` é gerado. O <xref:System.Data.MergeFailedEventArgs> objeto passado para o `MergeFailed` evento tem um <xref:System.Data.MergeFailedEventArgs.Conflict%2A> propriedade que identifica o conflito de esquema entre os dois `DataSet` objetos e um <xref:System.Data.MergeFailedEventArgs.Table%2A> propriedade que identifica o nome da tabela em conflito.  
  
 O fragmento de código a seguir demonstra como adicionar um manipulador de eventos para o `MergeFailed` eventos.  
  
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
  
## <a name="the-initialized-event"></a>O evento inicializado  
 O <xref:System.Data.DataSet.Initialized> evento ocorre após o `DataSet` construtor inicializa uma nova instância do `DataSet`.  
  
 O <xref:System.Data.DataSet.IsInitialized%2A> propriedade retorna `true` se o `DataSet` concluiu a inicialização; caso contrário, retornará `false`. O <xref:System.Data.DataSet.BeginInit%2A> método, que começa a inicialização de um `DataSet`, define <xref:System.Data.DataSet.IsInitialized%2A> para `false`. O <xref:System.Data.DataSet.EndInit%2A> método, que encerra a inicialização do `DataSet`, define como `true`. Esses métodos são usados pelo ambiente de design do Visual Studio para inicializar um `DataSet` que está sendo usado por outro componente. Você não usará comumente-los em seu código.  
  
## <a name="the-disposed-event"></a>O evento descartado  
 `DataSet` é derivado do <xref:System.ComponentModel.MarshalByValueComponent> classe, que expõe ambas as <xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A> método e o <xref:System.ComponentModel.MarshalByValueComponent.Disposed> eventos. O <xref:System.ComponentModel.MarshalByValueComponent.Disposed> evento adiciona um manipulador de eventos para escutar o evento descartado no componente. Você pode usar o <xref:System.ComponentModel.MarshalByValueComponent.Disposed> eventos de um `DataSet` se você quiser executar código quando o <xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A> método é chamado. <xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A> Libera os recursos usados pelo <xref:System.ComponentModel.MarshalByValueComponent>.  
  
> [!NOTE]
>  O `DataSet` e `DataTable` objetos herdam <xref:System.ComponentModel.MarshalByValueComponent> e suporte a <xref:System.Runtime.Serialization.ISerializable> interface para comunicação remota. Esses são os únicos objetos ADO.NET que podem ser remotos. Para obter mais informações, consulte [comunicação remota do .NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/72x4h507(v=vs.100)).  
  
 Para obter informações sobre outros eventos estão disponíveis ao trabalhar com um `DataSet`, consulte [manipulação de eventos de DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-datatable-events.md) e [manipulação de eventos DataAdapter](../../../../../docs/framework/data/adonet/handling-dataadapter-events.md).  
  
## <a name="see-also"></a>Consulte também

- [DataSets, DataTables e DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [Validando dados](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/t3b36awf(v=vs.120))
- [Recuperando e modificando dados no ADO.NET](../../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)
- [Central de desenvolvedores de provedores gerenciados ADO.NET e DataSet](https://go.microsoft.com/fwlink/?LinkId=217917)
