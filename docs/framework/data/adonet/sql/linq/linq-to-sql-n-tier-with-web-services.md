---
title: LINQ to SQL de n camadas com serviços da Web
ms.date: 03/30/2017
ms.assetid: 9cb10eb8-957f-4beb-a271-5f682016fed2
ms.openlocfilehash: 4fafaa60dd75def98b486e18faa5bd3ecd1d6315
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67743044"
---
# <a name="linq-to-sql-n-tier-with-web-services"></a>LINQ to SQL de n camadas com serviços da Web
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] é projetado principalmente para uso na camada intermediária em uma camada de acesso de dados flexível (DAL) como um serviço Web. Se a camada de apresentação é uma página da Web ASP.NET, então você usa o controle de servidor Web de <xref:System.Web.UI.WebControls.LinqDataSource> para gerenciar a transferência de dados entre a interface do usuário e [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] na camada intermediária. Se a camada de apresentação não é uma página ASP.NET, então a camada intermediária e a camada de apresentação devem fazer qualquer trabalho adicional para gerenciar serialização e desserialização de dados.  
  
## <a name="setting-up-linq-to-sql-on-the-middle-tier"></a>Foundation LINQ to SQL na camada intermediária  
 Em um serviço Web ou em um aplicativo de n camadas, a camada intermediária contém o contexto de dados e classes de entidade. Você pode criar essas classes manualmente ou usando SQLMetal.exe ou o Object Relational Designer conforme descrito em outro lugar na documentação. Em tempo de design, você tem a opção fazer as classes de entidade serializável. Para obter mais informações, confira [Como: Tornar entidades serializáveis](../../../../../../docs/framework/data/adonet/sql/linq/how-to-make-entities-serializable.md). Outra opção é criar um conjunto separado de classes que encapsulam os dados a ser serializados, e em projetos nesses tipos serializados quando você retorna dados nas consultas de [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] .  
  
 Você então define a interface com métodos que os clientes chamarão para recuperar, inserir e atualizar dados. Os métodos de interface envolvem as consultas de [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] . Você pode usar qualquer tipo de mecanismo de serialização para manipular chamadas remotos do método e serialização de dados. O único requisito é que se você tiver relações cíclicas ou bidirecionais no seu modelo de objeto, tal como aquela entre clientes e pedidos no modelo de objeto padrão do Northwind, então você deve usar um serializador que ofereça. O Windows Communication Foundation (WCF) <xref:System.Runtime.Serialization.DataContractSerializer> dá suporte a relações de bi-direcional, mas o XmlSerializer que é usado com os serviços não WCF Web não faz isso. Se você optar por usar o XmlSerializer, em seguida, certifique-se de que seu modelo de objeto não tem nenhuma relação cíclica.  
  
 Para obter mais informações sobre o Windows Communication Foundation, consulte [serviços do Windows Communication Foundation e WCF Data Services no Visual Studio](/visualstudio/data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio).  
  
 Implemente suas regras comerciais ou outra lógica específica de domínio usando as classes e métodos parciais em <xref:System.Data.Linq.DataContext> e classes de entidade para ligar em eventos em tempo de execução de [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] . Para obter mais informações, consulte [implementando lógica de negócios de N camadas](../../../../../../docs/framework/data/adonet/sql/linq/implementing-business-logic-linq-to-sql.md).  
  
## <a name="defining-the-serializable-types"></a>Definindo tipos Serializable  
 O cliente ou a camada de apresentação devem ter definições de tipo para as classes que será recebendo de camada intermediária. Esses tipos podem ser a entidade classificam-se, ou classes especiais que envolvem apenas determinados campos de entidade classe remoting. Em qualquer caso, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] é completamente indiferente sobre como a camada de apresentação obtém essas definições de tipo. Por exemplo, a camada de apresentação pode usar WCF para gerar automaticamente os tipos, ou pode ter uma cópia de uma DLL em que esses tipos são definidos, ou pode apenas definir suas próprias versões de tipos.  
  
## <a name="retrieving-and-inserting-data"></a>Recuperando e inserindo dados  
 A camada intermediária define uma interface que especifica como a camada de apresentação acessa os dados. Por exemplo `GetProductByID(int productID)`, ou `GetCustomers()`. Na camada intermediária, o corpo do método normalmente cria uma nova instância de <xref:System.Data.Linq.DataContext>, executa uma consulta em uma ou mais da tabela. A camada intermediária então retorna o resultado como <xref:System.Collections.Generic.IEnumerable%601>, onde `T` é uma classe de entidade ou outro tipo que é usado para serialização. A camada de apresentação nunca envia ou recebe variáveis de consulta diretamente ou da camada intermediária. Os dois valores de troca de camadas, objetos, e coleções de dados concretos. Depois que recebeu uma coleção, a camada de apresentação pode usar [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] a objetos para ver se necessário.  
  
 Para inserir dados, a camada de apresentação pode criar um novo objeto e enviá-lo para a camada intermediária, ou pode fazer com que a camada intermediária criar o objeto com base nos valores que fornece. Em geral, recuperar e inserir dados em aplicativos n-tier não difere do processo muito 2 em aplicativos de camada. Para obter mais informações, consulte [consulta o banco de dados](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md) e [tomada e enviando alterações de dados](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md).  
  
## <a name="tracking-changes-for-updates-and-deletes"></a>Controlar alterações para atualizações e exclusões  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] suporta concorrência otimista com base nos carimbos de data/hora (também chamados RowVersions) e valores originais. Se as tabelas de base de dados têm carimbos de data/hora, então atualizações e exclusões exigem vez trabalho adicional na camada intermediária na camada de apresentação. Entretanto, se você deve usar valores originais para verificação de simultaneidade otimista, então a camada de apresentação é responsável para controlar os valores e enviá-los novamente quando fazer atualizações. Isso ocorre porque as alterações que foram feitas às entidades na camada de apresentação não são controladas na camada intermediária. De fato, a recuperação original de uma entidade, e a atualização feita a eventual ele normalmente são executadas por duas instâncias separadas de <xref:System.Data.Linq.DataContext>completamente.  
  
 Maior o número de alterações que a camada de apresentação isso, ele fica mais complexa para controlar as alterações e para empacotar-las de volta para a camada intermediária. A implementação de um mecanismo para alterações de comunicação é completamente até o aplicativo. O único requisito é que [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] deve ser fornecido os valores originais que são necessários para verificação de simultaneidade otimista.  
  
 Para obter mais informações, consulte [recuperação de dados e operações de CUD em aplicativos de N camadas (LINQ to SQL)](../../../../../../docs/framework/data/adonet/sql/linq/data-retrieval-and-cud-operations-in-n-tier-applications.md).  
  
## <a name="see-also"></a>Consulte também

- [Aplicativos de N camadas e remotos com o LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/n-tier-and-remote-applications-with-linq-to-sql.md)
- [Visão geral do controle de servidor Web LinqDataSource](https://docs.microsoft.com/previous-versions/aspnet/bb547113(v=vs.100))
