---
title: Manipular eventos do DataSet
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 54edefe0-bc38-419b-b486-3d8a0c356f13
ms.openlocfilehash: b2b71dac58838a826933af570934bf4bbb35e025
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70784600"
---
# <a name="handling-dataset-events"></a>Manipular eventos do DataSet
O <xref:System.Data.DataSet> objeto fornece três eventos: <xref:System.ComponentModel.MarshalByValueComponent.Disposed>, <xref:System.Data.DataSet.Initialized>e <xref:System.Data.DataSet.MergeFailed>.  
  
## <a name="the-mergefailed-event"></a>O evento MergeFailed  
 O evento mais comumente usado do `DataSet` objeto é `MergeFailed`, que é gerado `DataSet` quando o esquema dos objetos que estão sendo mesclados está em conflito. Isso ocorre quando um destino e origem <xref:System.Data.DataRow> têm o mesmo valor de chave primária e a <xref:System.Data.DataSet.EnforceConstraints%2A> propriedade é definida como `true`. Por exemplo, se as colunas de chave primária de uma tabela que está sendo mesclada forem as mesmas entre as tabelas `DataSet` nos dois objetos, uma exceção será gerada `MergeFailed` e o evento será gerado. O <xref:System.Data.MergeFailedEventArgs> objeto passado para o `MergeFailed` evento tem uma <xref:System.Data.MergeFailedEventArgs.Conflict%2A> propriedade que identifica o conflito no esquema entre os dois `DataSet` objetos e uma <xref:System.Data.MergeFailedEventArgs.Table%2A> propriedade que identifica o nome da tabela em conflito.  
  
 O fragmento de código a seguir demonstra como adicionar um manipulador de eventos `MergeFailed` para o evento.  
  
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
  
## <a name="the-initialized-event"></a>O evento initialized  
 O <xref:System.Data.DataSet.Initialized> evento ocorre depois que `DataSet` o construtor inicializa `DataSet`uma nova instância do.  
  
 A <xref:System.Data.DataSet.IsInitialized%2A> propriedade retornará `true` se o `DataSet` tiver concluído a inicialização; caso contrário `false`, retornará. O <xref:System.Data.DataSet.BeginInit%2A> método, que começa a inicialização de um `DataSet`, define <xref:System.Data.DataSet.IsInitialized%2A> como `false`. O <xref:System.Data.DataSet.EndInit%2A> método, que termina a inicialização `DataSet`do, o define como `true`. Esses métodos são usados pelo ambiente de design do Visual Studio para inicializar `DataSet` um que está sendo usado por outro componente. Normalmente, você não os usará em seu código.  
  
## <a name="the-disposed-event"></a>O evento Descartado  
 `DataSet`é derivado da <xref:System.ComponentModel.MarshalByValueComponent> classe, que expõe o <xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A> método e o <xref:System.ComponentModel.MarshalByValueComponent.Disposed> evento. O <xref:System.ComponentModel.MarshalByValueComponent.Disposed> evento adiciona um manipulador de eventos para escutar o evento Descartado no componente. Você pode usar o <xref:System.ComponentModel.MarshalByValueComponent.Disposed> evento de um `DataSet` se quiser executar código quando o <xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A> método for chamado. <xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A>Libera os recursos usados pelo <xref:System.ComponentModel.MarshalByValueComponent>.  
  
> [!NOTE]
> Os `DataSet` objetos `DataTable` e herdam <xref:System.ComponentModel.MarshalByValueComponent> de e dão <xref:System.Runtime.Serialization.ISerializable> suporte à interface para comunicação remota. Esses são os únicos objetos ADO.NET que podem ser remotos. Para obter mais informações, consulte [comunicação remota do .net](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/72x4h507(v=vs.100)).  
  
 Para obter informações sobre outros eventos disponíveis ao trabalhar com `DataSet`um, consulte [manipulando eventos de DataTable](handling-datatable-events.md) e [manipulando eventos de DataAdapter](../handling-dataadapter-events.md).  
  
## <a name="see-also"></a>Consulte também

- [DataSets, DataTables, and DataViews](index.md) (DataSets, DataTables e DataViews)
- [Validação de dados](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/t3b36awf(v=vs.120))
- [Retrieving and Modifying Data in ADO.NET](../retrieving-and-modifying-data.md) (Recuperando e modificando dados no ADO.NET)
- [ADO.NET Overview](../ado-net-overview.md) (Visão geral do ADO.NET)
