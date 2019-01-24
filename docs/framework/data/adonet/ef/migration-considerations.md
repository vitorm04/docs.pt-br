---
title: Considerações sobre migração (Entity Framework)
ms.date: 03/30/2017
ms.assetid: c85b6fe8-cc32-4642-8f0a-dc0e5a695936
ms.openlocfilehash: 14f71de4a05c821ec21bf018fe2e2383d747c41b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54575613"
---
# <a name="migration-considerations-entity-framework"></a>Considerações sobre migração (Entity Framework)
O [!INCLUDE[vstecado](../../../../../includes/vstecado-md.md)] Entity Framework fornece vários benefícios para um aplicativo existente. Um dos mais importantes desses benefícios é a capacidade de usar um modelo conceitual para separar as estruturas de dados usadas pelo aplicativo no esquema da fonte de dados. Isso permite que você faça alterações futuras facilmente no modelo de armazenamento ou na própria fonte de dados sem fazer alterações de compensação no aplicativo. Para obter mais informações sobre os benefícios de usar o [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], consulte [visão geral do Entity Framework](../../../../../docs/framework/data/adonet/ef/overview.md) e [modelo de dados de entidade](../../../../../docs/framework/data/adonet/entity-data-model.md).  
  
 Para tirar proveito dos benefícios do [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], você pode migrar um aplicativo existente para o [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]. Algumas tarefas são comuns a todos os aplicativos migrados. Essas tarefas comuns incluem a atualização do aplicativo para usar o [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] começando com a versão 3.5 Service Pack 1 (SP1), definindo modelos e mapeamento e configurando o Entity Framework. Quando você migra um aplicativo para o [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], há considerações adicionais que se aplicam. Essas considerações dependem do tipo do aplicativo que está sendo migrado e da funcionalidade específica do aplicativo. Este tópico fornece informações para ajudá-lo a escolher a melhor abordagem a ser utilizada ao atualizar um aplicativo existente.  
  
## <a name="general-migration-considerations"></a>Considerações gerais sobre migração  
 As seguintes condições se aplicam quando você migra qualquer aplicativo para o [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]:  
  
-   Qualquer aplicativo que usa o [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] começando com a versão 3.5 SP1 pode ser migrado para o Entity Framework, desde que o provedor de dados da fonte de dados que é usado pelo aplicativo oferece suporte a Entity Framework.  
  
-   O Entity Framework não dá suporte a toda a funcionalidade de um provedor de fonte de dados, mesmo que o provedor dê suporte ao Entity Framework.  
  
-   Para um aplicativo grande ou complexo, não é necessário migrar todo o aplicativo para o Entity Framework de uma vez. No entanto, qualquer parte do aplicativo que não use o Entity Framework ainda deve ser alterada quando a fonte de dados for alterada.  
  
-   A conexão do provedor de dados usado pelo Entity Framework pode ser compartilhada com outras partes de seu aplicativo porque o [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] usa provedores de dados do [!INCLUDE[vstecado](../../../../../includes/vstecado-md.md)] para acessar a fonte de dados. Por exemplo, o provedor SqlClient é usado pelo Entity Framework para acessar um banco de dados SQL Server. Para obter mais informações, consulte [provedor EntityClient para Entity Framework](../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md).  
  
## <a name="common-migration-tasks"></a>Tarefas de migração comuns  
 O caminho para migração de um aplicativo existente para o [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] depende do tipo do aplicativo e da estratégia de acesso dos dados existentes. No entanto, você sempre deve executar as seguintes tarefas ao migrar um aplicativo existente para o [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].  
  
> [!NOTE]
>  Todas essas tarefas são executadas automaticamente quando você usar as ferramentas de modelo de dados de entidade a partir do Visual Studio 2008. Para obter mais informações, confira [Como: Use o Assistente de modelo de dados de entidade](https://msdn.microsoft.com/library/dadb058a-c5d9-4c5c-8b01-28044112231d).  
  
1.  Atualizar o aplicativo.  
  
     Um projeto criado usando uma versão anterior do Visual Studio e o [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] deve ser atualizado para usar o Visual Studio 2008 SP1 e o [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] começando com a versão 3.5 SP1.  
  
2.  Definir os modelos e o mapeamento.  
  
     O modelo e os arquivos de mapeamento definem entidades no modelo conceitual; estruturas na fonte de dados, como tabelas, procedimentos armazenados e modos de exibição; e o mapeamento entre as entidades e estruturas da fonte de dados. Para obter mais informações, confira [Como: Definir o modelo e arquivos de mapeamento manualmente](https://msdn.microsoft.com/library/d4fd6864-f2a1-48f0-aa32-1e318775a99a).  
  
     Os tipos definidos no modelo de armazenamento devem corresponder ao nome dos objetos na fonte de dados. Se o aplicativo existente expuser dados como objetos, você deverá garantir que as entidades e as propriedades definidas no modelo conceitual correspondam aos nomes dessas classes e propriedades de dados existentes. Para obter mais informações, confira [Como: Personalizar a modelagem e arquivos de mapeamento para trabalhar com objetos personalizados](https://msdn.microsoft.com/library/bb40c4db-0121-4e45-a167-8fb06707a708).  
  
    > [!NOTE]
    >  O Designer de Modelo de Dados de Entidade pode ser usado para renomear entidades no modelo conceitual para que correspondam aos objetos existentes. Para obter mais informações, consulte [Entity Data Model Designer](https://msdn.microsoft.com/library/4ccd7ad6-b934-4f7c-82a0-cfd2d4a95faf).  
  
3.  Definir a cadeia de conexão.  
  
     O [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] usa uma cadeia de conexão especialmente formatada ao executar consultas em um modelo conceitual. Essa cadeia de conexão encapsula informações sobre o modelo e arquivos de mapeamento e a conexão com a fonte de dados. Para obter mais informações, confira [Como: Definir a cadeia de caracteres de Conexão](../../../../../docs/framework/data/adonet/ef/how-to-define-the-connection-string.md).  
  
4.  Configure o projeto do Visual Studio.  
  
     As referências a [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] assemblies e o modelo e mapeamento de arquivos devem ser adicionados ao projeto do Visual Studio. Você pode adicionar esses arquivos de mapeamento ao projeto para garantir que sejam implantados com o aplicativo no local indicado na cadeia de conexão. Para obter mais informações, confira [Como: Configurar manualmente um projeto do Entity Framework](https://msdn.microsoft.com/library/73f6ae1d-b3b2-4577-aebd-ad5a75954e9e).  
  
## <a name="considerations-for-applications-with-existing-objects"></a>Considerações para aplicativos com objetos existentes  
 A partir do [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] 4, o [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] dá suporte a POCO (objetos CLR “básicos”), também chamados de objetos com ignorância de persistência. Na maioria dos casos, os objetos existentes podem trabalhar com o [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] fazendo alterações secundárias. Para obter mais informações, consulte [trabalhando com entidades POCO](https://msdn.microsoft.com/library/5e0fb82a-b6d1-41a1-b37b-c12db61629d3). Também é possível migrar um aplicativo para o [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] e usar as classes de dados que são geradas pelas ferramentas do Entity Framework. Para obter mais informações, confira [Como: Use o Assistente de modelo de dados de entidade](https://msdn.microsoft.com/library/dadb058a-c5d9-4c5c-8b01-28044112231d).  
  
## <a name="considerations-for-applications-that-use-adonet-providers"></a>Considerações para aplicativos que usam provedores ADO.NET  
 [!INCLUDE[vstecado](../../../../../includes/vstecado-md.md)] provedores, como o SqlClient, permitem que você consultar uma fonte de dados para retornar dados tabulares. Dados também podem ser carregados em um [!INCLUDE[vstecado](../../../../../includes/vstecado-md.md)] conjunto de dados. A lista a seguir descreve as considerações para a atualização de um aplicativo que usa um provedor [!INCLUDE[vstecado](../../../../../includes/vstecado-md.md)] existente:  
  
 Exibindo dados tabulares usando um leitor de dados.  
 Você pode considerar a execução de um [!INCLUDE[esql](../../../../../includes/esql-md.md)] consultar usando o provedor EntityClient e enumerando retornado <xref:System.Data.EntityClient.EntityDataReader> objeto. Faça isso somente se seu aplicativo exibe dados tabulares usando um leitor de dados e não requer que os recursos fornecidos pelo [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] para materializar dados em objetos, controle de alterações e fazer atualizações. Você pode continuar a usar o código de acesso de dados existente que faz atualizações à fonte de dados, mas você pode usar a conexão existente acessada a partir de <xref:System.Data.EntityClient.EntityConnection.StoreConnection%2A> propriedade de <xref:System.Data.EntityClient.EntityConnection>. Para obter mais informações, consulte [provedor EntityClient para Entity Framework](../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md).  
  
 Trabalhando com DataSets.  
 O [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] fornece muitas das mesmas funcionalidades fornecidas pelo conjunto de dados, incluindo persistência na memória, controle de alterações, vinculação de dados e serialização de objetos como dados XML. Para obter mais informações, consulte [trabalhando com objetos](../../../../../docs/framework/data/adonet/ef/working-with-objects.md).  
  
 Se o [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] não fornece a funcionalidade do conjunto de dados necessitado para seu aplicativo, você ainda pode tirar proveito dos benefícios de consultas LINQ usando [!INCLUDE[linq_dataset](../../../../../includes/linq-dataset-md.md)]. Para obter mais informações, consulte [LINQ to DataSet](../../../../../docs/framework/data/adonet/linq-to-dataset.md).  
  
## <a name="considerations-for-applications-that-bind-data-to-controls"></a>Considerações para aplicativos que associam dados a controles  
 O [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] permite encapsular dados em uma fonte de dados, como um conjunto de dados ou um [!INCLUDE[vstecasp](../../../../../includes/vstecasp-md.md)] controle de fonte de dados e, em seguida, associar elementos da interface do usuário a esses controles de dados. A lista a seguir descreve as considerações para associar controles aos dados do Entity Framework.  
  
 Associando dados a controles  
 Quando você consulta o modelo conceitual, o [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] retorna os dados como objetos que são instâncias de tipos de entidade. Esses objetos podem ser associados diretamente a controles, e essa associação dá suporte a atualizações. Isso significa que as alterações aos dados em um controle, como uma linha em uma <xref:System.Windows.Forms.DataGridView>, são automaticamente salvo no banco de dados quando o <xref:System.Data.Objects.ObjectContext.SaveChanges%2A> método é chamado.  
  
 Se seu aplicativo enumerar os resultados de uma consulta para exibir dados em um <xref:System.Windows.Forms.DataGridView> ou em outro tipo de controle que dê suporte a vinculação de dados, você poderá alterar seu aplicativo para associar o controle ao resultado de um <xref:System.Data.Objects.ObjectQuery%601>.  
  
 Para obter mais informações, consulte [objetos de associação aos controles](https://msdn.microsoft.com/library/2fd34855-929b-4303-a91e-4bb69d958f2b).  
  
 Controles de fonte de dados do [!INCLUDE[vstecasp](../../../../../includes/vstecasp-md.md)].  
 O [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] inclui um controle de fonte de dados projetado para simplificar a vinculação de dados em [!INCLUDE[vstecasp](../../../../../includes/vstecasp-md.md)] aplicativos da Web. Para obter mais informações, consulte [controle de fonte de dados do Entity Framework](https://msdn.microsoft.com/library/1f09af00-9578-4744-a029-765710a3c83f).  
  
## <a name="other-considerations"></a>Outras considerações  
 A seguir estão as considerações que podem se aplicar quando você migra tipos específicos de aplicativos para o Entity Framework.  
  
 Aplicativos que expõem serviços de dados.  
 Os serviços e aplicativos Web baseados no WCF (Windows Communication Foundation) expõem dados de uma fonte de dados subjacente usando um formato de mensagem XML de solicitação/resposta. O [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] dá suporte à serialização de objetos de entidade usando serialização binária, XML ou de contrato de dados WCF. A serialização binária e do WCF dão suporte à serialização completa de gráficos de objetos. Para obter mais informações, consulte [criando aplicativos de N camadas](https://msdn.microsoft.com/library/9439d2ba-6b5f-44e8-be65-8a442d922cbb).  
  
 Aplicativos que usam dados XML.  
 A serialização de objetos permite que você crie serviços de dados do [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]. Esses serviços fornecem dados a aplicativos que consomem dados XML, como aplicativos de Internet baseados em AJAX. Nesses casos, considere usar o [!INCLUDE[ssAstoria](../../../../../includes/ssastoria-md.md)]. Esses serviços de dados são baseados no modelo de dados de entidade e fornecem acesso dinâmico para dados de entidade usando ações de REST Representational State Transfer () HTTP padrão, como GET, PUT e POSTAM. Para obter mais informações, consulte [WCF Data Services 4.5](../../../../../docs/framework/data/wcf/index.md).  
  
 O [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] não dá suporte a um tipo de dados XML nativo. Isso significa que quando uma entidade é mapeada para uma tabela com uma coluna XML, a propriedade equivalente da entidade para a coluna XML é uma cadeia de caracteres. Os objetos podem ser desconectados e serializados como XML. Para obter mais informações, consulte [serializar objetos](https://msdn.microsoft.com/library/06c77f9b-5b2e-4c78-b3e3-8c148ba0ea99).  
  
 Se seu aplicativo exigir a capacidade de consultar dados XML, você ainda poderá tirar proveito dos benefícios de consultas LINQ usando o LINQ to XML. Para obter mais informações, consulte [LINQ to XML](https://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13).  
  
 Aplicativos que mantêm o estado.  
 [!INCLUDE[vstecasp](../../../../../includes/vstecasp-md.md)] Aplicativos Web com frequência devem manter o estado de uma página da Web ou de uma sessão de usuário. Objetos em um <xref:System.Data.Objects.ObjectContext> instância pode ser armazenada no estado de exibição do cliente ou no estado de sessão no servidor, e posteriormente recuperada e anexados novamente a um novo contexto de objeto. Para obter mais informações, consulte [anexando e desanexando objetos](https://msdn.microsoft.com/library/41d5c1ef-1b78-4502-aa10-7e1438d62d23).  
  
## <a name="see-also"></a>Consulte também
- [Considerações de implantação](../../../../../docs/framework/data/adonet/ef/deployment-considerations.md)
- [Terminologia do Entity Framework](../../../../../docs/framework/data/adonet/ef/terminology.md)
