---
title: Arquitetura do ADO.NET
ms.date: 03/30/2017
ms.assetid: fcd45b99-ae8f-45ab-8b97-d887beda734e
ms.openlocfilehash: 4c2299951202794112ea66c1f20025777c68e356
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44097441"
---
# <a name="adonet-architecture"></a>Arquitetura do ADO.NET
Antigamente, o processamento de dados dependia basicamente de um modelo de duas camadas baseado em conexão. Como o processamento de dados usa cada vez mais arquiteturas de várias camadas, os programadores estão adotando uma abordagem desconectada para fornecer melhor escalabilidade a seus aplicativos.  
  
## <a name="adonet-components"></a>Componentes do ADO.NET  
 Os dois componentes principais do [!INCLUDE[ado_orcas_long](../../../../includes/ado-orcas-long-md.md)] para acessar e manipular dados são os provedores de dados do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] e o <xref:System.Data.DataSet>.  
  
### <a name="net-framework-data-providers"></a>Provedores de dados .NET Framework  
 Os Provedores de Dados .NET Framework são componentes que foram criados explicitamente para manipulação de dados, e o rápido acesso a dados apenas de encaminhamento e somente leitura. O objeto `Connection` fornece conectividade a uma fonte de dados. O objeto `Command` permite o acesso aos comandos de banco de dados para retornar dados, modificar dados, executar procedimentos armazenados, e enviar ou recuperar informações de parâmetro. O `DataReader` fornece um fluxo de dados de alto desempenho da fonte de dados. Por fim, o `DataAdapter` faz a ponte entre o objeto `DataSet` e a fonte de dados. O `DataAdapter` usa os objetos `Command` para executar comandos SQL na fonte de dados a fim de carregar o `DataSet` com dados e reconciliar as alterações que foram feitas nos dados no `DataSet` com a fonte de dados. Para obter mais informações, consulte [provedores de dados do .NET Framework](../../../../docs/framework/data/adonet/data-providers.md) e [recuperando e modificando dados no ADO.NET](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md).  
  
### <a name="the-dataset"></a>O DataSet  
 O `DataSet` do ADO.NET é criado explicitamente para o acesso independente aos dados de qualquer fonte de dados. Consequentemente, ele pode ser usado com várias fontes de dados diferentes, usado com dados XML ou usado para gerenciar o local dos dados no aplicativo. O `DataSet` contém uma coleção de um ou mais objetos <xref:System.Data.DataTable> que consiste em linhas e em colunas de dados, e também em chave primária, chave estrangeira, restrição e informações de relação sobre os dados nos objetos `DataTable`. Para obter mais informações, consulte [DataSets, DataTables e DataViews](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md).  
  
 O diagrama a seguir ilustra a relação entre um provedor de dados do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] e um `DataSet`.  
  
 ![ADO.Net graphic](../../../../docs/framework/data/adonet/media/ado-1-bpuedev11.png "ado_1_bpuedev11")  
Arquitetura do ADO.NET  
  
### <a name="choosing-a-datareader-or-a-dataset"></a>Escolhendo um DataReader ou um DataSet  
 Quando você decidir se seu aplicativo deve usar um `DataReader` (consulte [recuperando dados usando um DataReader](../../../../docs/framework/data/adonet/retrieving-data-using-a-datareader.md)) ou uma `DataSet` (consulte [DataSets, DataTables e DataViews](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)), considere o tipo de funcionalidade de que seu aplicativo requer. Use um `DataSet` para fazer o seguinte:  
  
-   Armazenar dados em cache localmente no aplicativo para que você possa manipulá-lo. Se você precisar ler somente os resultados de uma consulta, o `DataReader` será a melhor opção.  
  
-   Estabelecer a comunicação remota dos dados entre camadas ou em um serviço Web XML.  
  
-   Interagir com os dados dinamicamente, por exemplo, fazendo a associação a um controle do Windows Forms ou combinando e relacionando dados de várias fontes.  
  
-   Executar um processamento extensivo nos dados sem precisar de uma conexão aberta com a fonte de dados, o que libera a conexão a ser usada por outros clientes.  
  
 Se você não precisar da funcionalidade fornecida pelo `DataSet`, poderá melhorar o desempenho do aplicativo usando o `DataReader` para retornar os dados apenas para encaminhamento e somente leitura. Embora o `DataAdapter` usa o `DataReader` para preencher o conteúdo de um `DataSet` (consulte [populando um DataSet a partir de um DataAdapter](../../../../docs/framework/data/adonet/populating-a-dataset-from-a-dataadapter.md)), usando o `DataReader`, você pode melhorar o desempenho porque economizará a memória que poderia ser consumido pela `DataSet`e evitar o processamento que é necessário para criar e preencher o conteúdo do `DataSet`.  
  
## <a name="linq-to-dataset"></a>LINQ to DataSet  
 O LINQ to DataSet fornece recursos de consulta e verificação de tipo em tempo de compilação nos dados armazenados em cache em um objeto DataSet. Ele permite que você grave consultas em uma das linguagens de desenvolvimento do .NET Framework, como C# ou Visual Basic. Para obter mais informações, consulte [LINQ to DataSet](../../../../docs/framework/data/adonet/linq-to-dataset.md).  
  
## <a name="linq-to-sql"></a>LINQ to SQL  
 O LINQ to SQL oferece suporte a consultas em um modelo de objeto que é mapeado para as estruturas de dados de um banco de dados relacional sem usar um modelo conceitual intermediário. Cada tabela é representada por uma classe separada, acoplando com segurança o modelo de objeto ao esquema do banco de dados relacional. O LINQ to SQL converte consultas integradas à linguagem no modelo de objeto na Transact-SQL e as envia ao banco de dados para execução. Quando o banco de dados retorna os resultados, o LINQ to SQL converte os resultados novamente em objetos. Para obter mais informações, consulte [LINQ to SQL](../../../../docs/framework/data/adonet/sql/linq/index.md).  
  
## <a name="adonet-entity-framework"></a>ADO.NET Entity Framework  
 O ADO.NET Entity Framework foi criado para permitir que os desenvolvedores criem aplicativos de acesso a dados programando em um modelo de aplicativo conceitual, em vez de programar diretamente em um esquema de armazenamento relacional. O objetivo é diminuir a quantidade de código e de manutenção necessários a aplicativos orientados a dados. Para obter mais informações, consulte [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md).  
  
## <a name="wcf-data-services"></a>WCF Data Services  
 O [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] é usado para implantar serviços de dados na Web ou em uma intranet. Os dados são estruturados como entidades e relações de acordo com as especificações do Modelo de Dados de Entidade. Os dados implantados nesse modelo são endereçáveis pelo protocolo HTTP padrão. Para obter mais informações, consulte [WCF Data Services 4.5](../../../../docs/framework/data/wcf/index.md).  
  
## <a name="xml-and-adonet"></a>XML e ADO.NET  
 O [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] aproveita a capacidade do XML para fornecer acesso desconectado a dados. O [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] foi criado em conjunto com as classes XML do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]; ambos são componentes de uma única arquitetura.  
  
 O [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] e as classes XML do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] convergem para o objeto `DataSet`. O `DataSet` pode ser preenchido com dados de uma fonte XML, quer ele seja um arquivo ou um fluxo XML. O `DataSet` pode ser gravado como XML compatível com World-Wide Web Consortium (W3C) que inclui seu esquema como a linguagem de definição de esquema XML (XSD), independentemente da fonte dos dados no `DataSet`. Como o formato nativo de serialização do `DataSet` é XML, ele é um meio excelente para mover os dados entre as camadas, tornando o `DataSet` uma opção ideal para a comunicação remota dos dados e do contexto de esquema para e de um serviço Web XML. Para obter mais informações, consulte [Documentos e dados XML](../../../../docs/standard/data/xml/index.md).  
  
## <a name="see-also"></a>Consulte também  
 [ADO.NET Overview](../../../../docs/framework/data/adonet/ado-net-overview.md) (Visão geral do ADO.NET)  
 [ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
