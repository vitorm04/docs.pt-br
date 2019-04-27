---
title: Atualizando o serviço de dados (WCF Data Services)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, changing data
- WCF Data Services, client library
ms.assetid: 00d993be-ffed-4dea-baf7-6eea982cdb54
ms.openlocfilehash: 42980aa4691d8ecb9868336ecb270c9ad937b5a3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61876103"
---
# <a name="updating-the-data-service-wcf-data-services"></a>Atualizando o serviço de dados (WCF Data Services)
Quando você usa o [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] biblioteca de cliente para consumir um [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] feed, a biblioteca converte as entradas no feed em instâncias de classes de serviço de dados do cliente. Essas classes de serviço de dados são rastreados, usando o <xref:System.Data.Services.Client.DataServiceContext> ao qual o <xref:System.Data.Services.Client.DataServiceQuery%601> pertence. O cliente controla as alterações para entidades que relatam usando métodos em <xref:System.Data.Services.Client.DataServiceContext>. Esses métodos permitem que o cliente rastrear entidades adicionadas e excluídas e também as alterações feitas aos valores de propriedade ou relações entre instâncias de entidade. Essas alterações controladas são enviadas para o serviço de dados como operações baseadas em REST, quando você chama o <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> método.  
  
> [!NOTE]
>  Quando você usa uma instância do <xref:System.Data.Services.Client.DataServiceCollection%601> para associar dados a controles, as alterações feitas aos dados no controle associado são automaticamente relatadas para o <xref:System.Data.Services.Client.DataServiceContext>. Para obter mais informações, consulte [associando dados a controles](../../../../docs/framework/data/wcf/binding-data-to-controls-wcf-data-services.md).  
  
## <a name="adding-modifying-and-changing-entities"></a>Adicionando, modificando e alteração de entidades  
 Quando você usa o **adicionar referência de serviço** caixa de diálogo no Visual Studio para adicionar uma referência a um [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feed, as cliente dados serviço classes resultantes cada ter um estático *criar* que usa um método parâmetro para cada propriedade da entidade não anuláveis. Você pode usar esse método para criar instâncias da entidade de classes de tipo, como no exemplo a seguir:  
  
 [!code-csharp[Astoria Northwind Client#CreateNewProduct](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#createnewproduct)]
 [!code-vb[Astoria Northwind Client#CreateNewProduct](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#createnewproduct)]  
  
 Para adicionar uma instância de entidade, chame o *AdicionarPara* método o <xref:System.Data.Services.Client.DataServiceContext> classe gerada pelo **Add Service Reference** caixa de diálogo, como no exemplo a seguir:  
  
 [!code-csharp[Astoria Northwind Client#AddProductSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#addproductspecific)]
 [!code-vb[Astoria Northwind Client#AddProductSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#addproductspecific)]  
  
 Isso adiciona o objeto ao contexto e no conjunto de entidades correto. Você também pode chamar <xref:System.Data.Services.Client.DataServiceContext.AddObject%2A>, mas em vez disso, você deve fornecer o nome do conjunto de entidade. Se a entidade adicionada tem uma ou mais relações a outras entidades, você pode usar o <xref:System.Data.Services.Client.DataServiceContext.AddRelatedObject%2A> método ou use um dos métodos anteriores e definir explicitamente esses links. Essas operações são discutidas neste tópico.  
  
 Para modificar uma instância de entidade existente, a primeira consulta para essa entidade, faça as alterações desejadas para suas propriedades e, em seguida, chame o <xref:System.Data.Services.Client.DataServiceContext.UpdateObject%2A> método no <xref:System.Data.Services.Client.DataServiceContext> para indicar para a biblioteca de cliente que ele precisa para enviar uma atualização para o objeto, como mostrado na o exemplo a seguir:  
  
 [!code-csharp[Astoria Northwind Client#ModifyCustomerSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#modifycustomerspecific)]
 [!code-vb[Astoria Northwind Client#ModifyCustomerSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#modifycustomerspecific)]  
  
 Para excluir uma instância de entidade, chame o <xref:System.Data.Services.Client.DataServiceContext.DeleteObject%2A> método no <xref:System.Data.Services.Client.DataServiceContext>, conforme mostrado no exemplo a seguir:  
  
 [!code-csharp[Astoria Northwind Client#DeleteProductSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#deleteproductspecific)]
 [!code-vb[Astoria Northwind Client#DeleteProductSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#deleteproductspecific)]  
  
 Para obter mais informações, confira [Como: Adicionar, modificar e excluir entidades](../../../../docs/framework/data/wcf/how-to-add-modify-and-delete-entities-wcf-data-services.md).  
  
## <a name="attaching-entities"></a>Anexar entidades  
 A biblioteca de cliente permite que você salve as atualizações feitas a uma entidade sem primeiro executar uma consulta para carregar a entidade para o <xref:System.Data.Services.Client.DataServiceContext>. Use o <xref:System.Data.Services.Client.DataServiceContext.AttachTo%2A> método para anexar um objeto existente a uma entidade específica definida <xref:System.Data.Services.Client.DataServiceContext>. Em seguida, você pode modificar o objeto e salvar as alterações para o serviço de dados. No exemplo a seguir, um objeto de cliente que foi alterado é anexado ao contexto e, em seguida <xref:System.Data.Services.Client.DataServiceContext.UpdateObject%2A> é chamado para marcar o objeto anexado como <xref:System.Data.Services.Client.EntityStates.Modified> antes de <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> é chamado:  
  
 [!code-csharp[Astoria Northwind Client#AttachObjectSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#attachobjectspecific)]
 [!code-vb[Astoria Northwind Client#AttachObjectSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#attachobjectspecific)]  
  
 As seguintes considerações se aplicam ao anexar objetos:  
  
-   Um objeto está anexado a <xref:System.Data.Services.Client.EntityStates.Unchanged> estado.  
  
-   Quando um objeto é anexado, objetos que estão relacionados ao objeto anexado também não serão anexados.  
  
-   Não pode ser anexado a um objeto se a entidade já está sendo acompanhada pelo contexto.  
  
-   O <xref:System.Data.Services.Client.DataServiceContext.AttachTo%28System.String%2CSystem.Object%2CSystem.String%29> sobrecarga de método que usa um `etag` parâmetro é usado quando você anexa um objeto de entidade que foi recebido, juntamente com um valor de eTag. Esse valor de eTag, em seguida, é usado para verificar a simultaneidade quando as alterações no objeto anexado são salvos.  
  
 Para obter mais informações, confira [Como: Anexar uma entidade existente ao DataServiceContext](../../../../docs/framework/data/wcf/attach-an-existing-entity-to-dc-wcf-data.md).  
  
## <a name="creating-and-modifying-relationship-links"></a>Criando e modificando os Links do relacionamento  
 Quando você adiciona uma nova entidade usando o a <xref:System.Data.Services.Client.DataServiceContext.AddObject%2A> método ou apropriado *AdicionarPara* método da <xref:System.Data.Services.Client.DataServiceContext> classe que o **Add Service Reference** gera a caixa de diálogo, todas as relações entre a nova entidade e entidades relacionadas não são automaticamente definidas.  
  
 Você pode criar e alterar relações entre instâncias de entidade e que a biblioteca cliente reflita essas alterações no serviço de dados. Relações entre entidades são definidas como associações no modelo e o <xref:System.Data.Services.Client.DataServiceContext> controla cada relação como um objeto de link no contexto. [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] fornece os métodos a seguir sobre o <xref:System.Data.Services.Client.DataServiceContext> classe para criar, modificar e excluir esses links:  
  
|Método|Descrição|  
|------------|-----------------|  
|<xref:System.Data.Services.Client.DataServiceContext.AddRelatedObject%2A>|Cria um novo link entre dois objetos de entidade relacionada. Chamar esse método é equivalente a chamar <xref:System.Data.Services.Client.DataServiceContext.AddObject%2A> e <xref:System.Data.Services.Client.DataServiceContext.AddLink%2A> para criar o novo objeto e definir a relação a um objeto existente.|  
|<xref:System.Data.Services.Client.DataServiceContext.AddLink%2A>|Cria um novo link entre dois objetos de entidade relacionada.|  
|<xref:System.Data.Services.Client.DataServiceContext.SetLink%2A>|Atualiza um link existente entre dois objetos de entidade relacionada. <xref:System.Data.Services.Client.DataServiceContext.SetLink%2A> também é usado para excluir links com uma cardinalidade de zero-ou-um-para-um (`0..1:1`) e um para um (`1:1`). Você pode fazer isso definindo o objeto relacionado `null`.|  
|<xref:System.Data.Services.Client.DataServiceContext.DeleteLink%2A>|Marca um link que o contexto está rastreamento para exclusão quando o <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> método é chamado. Use esse método quando você exclui um objeto relacionado ou alterar uma relação, primeiro excluir o link para um objeto existente e, em seguida, adicionar um link para o novo objeto relacionado.|  
|<xref:System.Data.Services.Client.DataServiceContext.AttachLink%2A>|Notifica o contexto de um link existente entre dois objetos de entidade. O contexto supõe que essa relação já existe no serviço de dados e não tentará criar o link quando você chama o <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> método. Use este método quando você anexar objetos a um contexto e precisará também anexar o link entre os dois. Se você estiver definindo uma nova relação, você deve usar <xref:System.Data.Services.Client.DataServiceContext.AddLink%2A>.|  
|<xref:System.Data.Services.Client.DataServiceContext.DetachLink%2A>|Interrompe o link especificado no contexto de acompanhamento. Esse método é usado para excluir um-para-muitos (`*:*`) relações. Para obter links de relacionamento com uma cardinalidade de um, você deve usar <xref:System.Data.Services.Client.DataServiceContext.SetLink%2A>.|  
  
 O exemplo a seguir mostra como usar o <xref:System.Data.Services.Client.DataServiceContext.AddRelatedObject%2A> método para adicionar uma nova `Order_Detail` que está relacionado a um existente `Orders` entidade. Porque o novo `Order_Details` objeto agora é controlado pela <xref:System.Data.Services.Client.DataServiceContext>, a relação de adicionado `Order_Details` objeto existente `Products` entidade é definida chamando o <xref:System.Data.Services.Client.DataServiceContext.AddLink%2A> método:  
  
 [!code-csharp[Astoria Northwind Client#AddOrderDetailToOrderSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#addorderdetailtoorderspecific)]
 [!code-vb[Astoria Northwind Client#AddOrderDetailToOrderSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#addorderdetailtoorderspecific)]  
  
 Enquanto o <xref:System.Data.Services.Client.DataServiceContext.AddLink%2A> método define links que deve ser criado no serviço de dados, para que esses links refletidas em objetos que estão no contexto, você também deve definir as propriedades de navegação nos objetos em si. No exemplo anterior, você deve definir as propriedades de navegação da seguinte maneira:  
  
 [!code-csharp[Astoria Northwind Client#SetNavProps](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#setnavprops)]
 [!code-vb[Astoria Northwind Client#SetNavProps](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#setnavprops)]  
  
 Para obter mais informações, confira [Como: Definir relações entre entidades](../../../../docs/framework/data/wcf/how-to-define-entity-relationships-wcf-data-services.md).  
  
## <a name="saving-changes"></a>Salvando alterações  
 As alterações são rastreadas no <xref:System.Data.Services.Client.DataServiceContext> da instância, mas não são enviadas para o servidor imediatamente. Depois que você tiver concluído as alterações necessárias para uma atividade especificada, chame <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> para enviar todas as alterações ao serviço de dados. Para obter mais informações, consulte [Gerenciando o contexto do serviço de dados](../../../../docs/framework/data/wcf/managing-the-data-service-context-wcf-data-services.md). Você também pode salvar alterações de forma assíncrona usando o <xref:System.Data.Services.Client.DataServiceContext.BeginSaveChanges%2A> e <xref:System.Data.Services.Client.DataServiceContext.EndSaveChanges%2A> métodos. Para obter mais informações, consulte [operações assíncronas](../../../../docs/framework/data/wcf/asynchronous-operations-wcf-data-services.md).  
  
## <a name="see-also"></a>Consulte também

- [WCF Data Services Client Library](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md) (Biblioteca de clientes do WCF Data Services)
- [Querying the Data Service](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md) (Consultando o serviço de dados)
- [Operações assíncronas](../../../../docs/framework/data/wcf/asynchronous-operations-wcf-data-services.md)
- [Operações de envio em lote](../../../../docs/framework/data/wcf/batching-operations-wcf-data-services.md)
- [Materialização de objetos](../../../../docs/framework/data/wcf/object-materialization-wcf-data-services.md)
- [Gerenciando o contexto do serviço de dados](../../../../docs/framework/data/wcf/managing-the-data-service-context-wcf-data-services.md)
