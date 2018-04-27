---
title: Manipulação de eventos do conjunto de dados
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 54edefe0-bc38-419b-b486-3d8a0c356f13
caps.latest.revision: 4
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: aea9fc2caae675b77a8aad730869adb00f593baf
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/27/2018
---
# <a name="handling-dataset-events"></a>Manipulação de eventos do conjunto de dados
O <xref:System.Data.DataSet> objeto fornece três eventos: <xref:System.ComponentModel.MarshalByValueComponent.Disposed>, <xref:System.Data.DataSet.Initialized>, e <xref:System.Data.DataSet.MergeFailed>.  
  
## <a name="the-mergefailed-event"></a>O evento MergeFailed  
 Evento mais usados o `DataSet` objeto é `MergeFailed`, que é gerado quando o esquema do `DataSet` objetos sendo mesclados estão em conflito. Isso ocorre quando uma origem e destino <xref:System.Data.DataRow> têm o mesmo valor de chave primário e o <xref:System.Data.DataSet.EnforceConstraints%2A> está definida como `true`. Por exemplo, se as colunas de chave primária de uma tabela que está sendo mesclado são os mesmos entre as tabelas nas duas `DataSet` objetos, uma exceção será lançada e a `MergeFailed` é gerado. O <xref:System.Data.MergeFailedEventArgs> objeto passado para o `MergeFailed` evento tem um <xref:System.Data.MergeFailedEventArgs.Conflict%2A> propriedade que identifica o conflito no esquema entre os dois `DataSet` objetos e um <xref:System.Data.MergeFailedEventArgs.Table%2A> propriedade que identifica o nome da tabela em conflito.  
  
 O fragmento de código a seguir demonstra como adicionar um manipulador de eventos para o `MergeFailed` evento.  
  
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
  
 O <xref:System.Data.DataSet.IsInitialized%2A> propriedade retorna `true` se o `DataSet` concluiu a inicialização; caso contrário, ele retorna `false`. O <xref:System.Data.DataSet.BeginInit%2A> método, que inicia a inicialização de um `DataSet`, define <xref:System.Data.DataSet.IsInitialized%2A> para `false`. O <xref:System.Data.DataSet.EndInit%2A> método, que termina a inicialização do `DataSet`, define-o como `true`. Esses métodos são usados pelo ambiente de design do Visual Studio para inicializar um `DataSet` que está sendo usado por outro componente. Você não usará frequência-los em seu código.  
  
## <a name="the-disposed-event"></a>O evento descartado  
 `DataSet` é derivado do <xref:System.ComponentModel.MarshalByValueComponent> classe que expõe ambos o <xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A> método e o <xref:System.ComponentModel.MarshalByValueComponent.Disposed> evento. O <xref:System.ComponentModel.MarshalByValueComponent.Disposed> evento adiciona um manipulador de eventos para escutar o evento descartado no componente. Você pode usar o <xref:System.ComponentModel.MarshalByValueComponent.Disposed> eventos de um `DataSet` se você quiser executar código quando o <xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A> método é chamado. <xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A> libera os recursos usados pelo <xref:System.ComponentModel.MarshalByValueComponent>.  
  
> [!NOTE]
>  O `DataSet` e `DataTable` objetos herdam <xref:System.ComponentModel.MarshalByValueComponent> e suporte a <xref:System.Runtime.Serialization.ISerializable> interface de comunicação remota. Esses são os únicos objetos ADO.NET que podem ser remotos. Para obter mais informações, consulte [objetos remotos](http://msdn.microsoft.com/library/515686e6-0a8d-42f7-8188-73abede57c58).  
  
 Para obter informações sobre outros eventos disponíveis ao trabalhar com um `DataSet`, consulte [manipulando eventos de DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-datatable-events.md) e [manipulando eventos de DataAdapter](../../../../../docs/framework/data/adonet/handling-dataadapter-events.md).  
  
## <a name="see-also"></a>Consulte também  
 [DataSets, DataTables, and DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md) (DataSets, DataTables e DataViews)  
 [Validando dados](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)  
 [Retrieving and Modifying Data in ADO.NET](../../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md) (Recuperando e modificando dados no ADO.NET)  
 [ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
