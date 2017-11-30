---
title: "Controle de versão de serviço"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 37575ead-d820-4a67-8059-da11a2ab48e2
caps.latest.revision: "19"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: bcfb6476d6ae1e9c01458c7ec12dc0cd3c34e995
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="service-versioning"></a>Controle de versão de serviço
Após a implantação inicial e potencialmente várias vezes durante a vida útil, serviços (e os pontos de extremidade expõem) podem precisar ser alterada para uma variedade de motivos, como alterar as necessidades de negócios, requisitos de tecnologia da informação, ou aborda outros problemas. Cada alteração introduz uma nova versão do serviço. Este tópico explica como considerar o controle de versão no [!INCLUDE[indigo1](../../../includes/indigo1-md.md)].  
  
## <a name="four-categories-of-service-changes"></a>Quatro categorias de alterações de serviço  
 As alterações aos serviços que podem ser necessárias podem ser classificadas em quatro categorias:  
  
-   Alterações de contrato: por exemplo, pode ser adicionada a uma operação ou um elemento de dados em uma mensagem pode ser adicionado ou alterado.  
  
-   Alterações de endereço: por exemplo, um serviço move para um local diferente em que os pontos de extremidade têm novos endereços.  
  
-   Alterações de associação: por exemplo, alterações de um mecanismo de segurança ou alterar suas configurações.  
  
-   Alterações de implementação: por exemplo, quando uma implementação de método interno é alterado.  
  
 Algumas dessas alterações são chamadas de "quebra" e outros são "incondicional". Uma alteração é *incondicional* se todas as mensagens que seriam foram processadas com êxito na versão anterior são processadas com êxito na nova versão. Qualquer alteração que não atende esse critério é um *quebra* alterar.  
  
## <a name="service-orientation-and-versioning"></a>Controle de versão e a orientação de serviço  
 Um dos princípios da orientação de serviço é que clientes e serviços são autônomos (independente). Entre outras coisas, isso significa que os desenvolvedores de serviço não podem assumir que controlam ou até mesmo saber sobre todos os clientes de serviço. Isso elimina a opção de recompilar e reimplantar todos os clientes quando uma versões de alterações de serviço. Este tópico pressupõe que o serviço segue esse princípio e, portanto, deve ser alterado ou "versão" independentemente de seus clientes.  
  
 Em casos em que uma alteração significativa é inesperado e não pode ser evitada, um aplicativo pode optar por ignorar esse princípio e exigem que os clientes seja reconstruídos e redistribuídos com uma nova versão do serviço.  
  
## <a name="contract-versioning"></a>Controle de versão do contrato  
 Contratos usados por um cliente não precisam ser o mesmo contrato usado pelo serviço; eles só precisam ser compatíveis.  
  
 Para contratos de serviço, compatibilidade significa novas operações expostas pelo serviço podem ser adicionadas, mas as operações existentes não podem ser removidas ou alteradas semanticamente.  
  
 Para contratos de dados, compatibilidade significa novo tipo de esquema definições podem ser adicionadas, mas as definições de tipo de esquema existente não podem ser alteradas em maneiras de quebra. Alterações recentes podem incluir remover membros de dados ou alterar o tipo de dados incompatíveis. Esse recurso permite que o serviço alguns latitude na alteração da versão de seus contratos sem interromper os clientes. As duas próximas seções explicam incondicional e alterações significativas que podem ser feitas para [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] contratos de serviço e de dados.  
  
## <a name="data-contract-versioning"></a>Controle de versão de contrato de dados  
 Esta seção lida com controle de versão de dados ao usar o <xref:System.Runtime.Serialization.DataContractSerializer> e <xref:System.Runtime.Serialization.DataContractAttribute> classes.  
  
### <a name="strict-versioning"></a>Controle de versão estrito  
 Em muitos cenários quando a alteração da versão é um problema, o desenvolvedor de serviço não tem controle sobre os clientes e, portanto, não é possível fazer suposições sobre como eles seriam reagir a alterações na mensagem XML ou esquema. Nesses casos, você deve assegurar que as novas mensagens serão validado em relação ao esquema antigo, por dois motivos:  
  
-   Os clientes antigos foram desenvolvidos com a suposição de que o esquema não será alterada. Eles podem falhar ao processar mensagens que nunca foram projetados.  
  
-   Os clientes antigos podem realizar a validação de esquema real em relação ao esquema antigo antes de tentar processar as mensagens até mesmo.  
  
 A abordagem recomendada nesses cenários é tratar os contratos de dados existente como imutável e criar novos com XML exclusivo nomes qualificados. O desenvolvedor do serviço será, em seguida, adicione novos métodos para um contrato de serviço existente ou criar um novo contrato de serviço com métodos que usam o novo contrato de dados.  
  
 Geralmente é o caso em que um desenvolvedor de serviço precisa gravar alguma lógica de negócios que deve ser executado em todas as versões de um contrato de dados mais código específico da versão comercial para cada versão do contrato de dados. Os apêndices no final deste tópico explica como interfaces podem ser usadas para atender a essa necessidade.  
  
### <a name="lax-versioning"></a>Controle de versão incerta  
 Em muitos cenários, o desenvolvedor de serviço pode assumir que a adição de um novo membro opcional para o contrato de dados não afetarão os clientes existentes. Isso exige que o desenvolvedor de serviço investigar se os clientes existentes não estão executando a validação de esquema e que eles ignoram a membros de dados desconhecido. Nesses cenários, é possível tirar proveito dos recursos de contrato de dados para adicionar novos membros de forma incondicional. O desenvolvedor de serviço pode fazer essa suposição com confiança se os recursos de contrato de dados para controle de versão já foram usados para a primeira versão do serviço.  
  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)], Serviços Web ASP.NET e muitos outros suporte de pilhas de serviço Web *versão lax*: ou seja, elas não lançam exceções para novos membros de dados desconhecido em dados recebidos.  
  
 É fácil por engano acredita que adicionar um novo membro não será interrompido clientes existentes. Se você não tiver certeza de que todos os clientes podem tratar incerta controle de versão, a recomendação é usar as diretrizes rígidas de controle de versão e tratar os dados contratos como imutável.  
  
 Para obter diretrizes detalhadas para controle de versão incerta e estrita de contratos de dados, consulte [práticas recomendadas: controle de versão de contrato de dados](../../../docs/framework/wcf/best-practices-data-contract-versioning.md).  
  
### <a name="distinguishing-between-data-contract-and-net-types"></a>Fazer distinção entre o contrato de dados e tipos do .NET  
 Uma classe ou estrutura .NET pode ser projetada como um contrato de dados, aplicando o <xref:System.Runtime.Serialization.DataContractAttribute> para a classe de atributo. O tipo de .NET e suas projeções de contrato de dados são dois assuntos distintos. É possível ter vários tipos de .NET com a mesma projeção de contrato de dados. Essa distinção é especialmente útil em permitir que você altere o tipo de .NET, mantendo o contrato de dados projetada, mantendo a compatibilidade com os clientes existentes, mesmo no sentido estrito do word. Há duas coisas que você sempre deve fazer para manter essa distinção entre o contrato de dados e tipo do .NET:  
  
-   Especifique um <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A> e <xref:System.Runtime.Serialization.DataContractAttribute.Namespace%2A>. Você sempre deve especificar o nome e o namespace do seu contrato de dados para impedir que o nome do tipo de .NET e o namespace sejam expostas no contrato. Dessa forma, se você decidir posteriormente alterar o namespace .NET ou digite o nome, o contrato de dados permanecerá o mesmo.  
  
-   Especifique <xref:System.Runtime.Serialization.DataMemberAttribute.Name%2A>. Você sempre deve especificar o nome de seus membros de dados para impedir que o nome do membro .NET expostas no contrato. Dessa forma, se você decidir posteriormente alterar o nome do .NET do membro, o contrato de dados permanecerá o mesmo.  
  
### <a name="changing-or-removing-members"></a>Alterar ou remover membros  
 Alterando o nome ou tipo de dados de um membro ou removendo membros de dados é uma alteração significativa, mesmo se o controle de versão incerta é permitido. Se isso for necessário, crie um novo contrato de dados.  
  
 Se a compatibilidade de serviço é de alta prioridade, talvez considere ignorando membros de dados não utilizados no seu código e deixá-los no local. Se você estiver dividindo um membro de dados em vários membros, você pode considerar deixar o membro existente no local como uma propriedade que pode executar a nova agregação e divisão necessária para clientes de nível inferior (clientes que não são atualizados para a versão mais recente).  
  
 Da mesma forma, as alterações para o namespace ou nome de contrato de dados são as alterações recentes.  
  
### <a name="round-trips-of-unknown-data"></a>Ida e volta de dados desconhecidos  
 Em alguns cenários, é necessário para dados desconhecido "ida e volta" que vêm de membros adicionados em uma nova versão. Por exemplo, um serviço de "versionNew" envia dados com alguns membro adicionado recentemente a um cliente de "versionOld". O cliente ignora os membros recém-adicionados ao processar a mensagem, mas reenvia esses mesmos dados, incluindo os membros recém-adicionados, volta para o serviço versionNew. O cenário típico para isso é atualizações de dados onde os dados são recuperados do serviço de, alterados e retornados.  
  
 Para habilitar o ciclo de um determinado tipo, o tipo deve implementar o <xref:System.Runtime.Serialization.IExtensibleDataObject> interface. A interface contém uma propriedade, <xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A> que retorna o <xref:System.Runtime.Serialization.ExtensionDataObject> tipo. A propriedade é usada para armazenar os dados das versões futuras do contrato de dados é desconhecido para a versão atual. Esses dados serão opaco ao cliente, mas quando a instância é serializada, o conteúdo do <xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A> propriedade foi escrita com o restante dos dados dos membros de contrato de dados.  
  
 É recomendável que todos os tipos de implementam essa interface para acomodar novos e desconhecidos membros futuras.  
  
### <a name="data-contract-libraries"></a>Bibliotecas de contrato de dados  
 Pode haver bibliotecas de contratos de dados onde um contrato é publicado em um repositório central e implementadores de serviço e tipo de implementarem e expõem os contratos de dados do que o repositório. Nesse caso, quando você publica um contrato de dados para o repositório, você não têm controle sobre quem cria tipos de implementação-la. Portanto, você não pode modificar o contrato quando ela for publicada, renderizá-lo efetivamente imutável.  
  
### <a name="when-using-the-xmlserializer"></a>Ao usar o XmlSerializer  
 Os mesmos princípios de controle de versão se aplicam ao usar o <xref:System.Xml.Serialization.XmlSerializer> classe. Quando estrito controle de versão é necessária, trate os contratos de dados como imutável e criar novos contratos de dados com nomes exclusivos e qualificados para as novas versões. Quando tiver certeza de que versão incerta pode ser usado, você pode adicionar novos membros serializáveis em novas versões, mas não alterar ou remover membros existentes.  
  
> [!NOTE]
>  O <xref:System.Xml.Serialization.XmlSerializer> usa o <xref:System.Xml.Serialization.XmlAnyElementAttribute> e <xref:System.Xml.Serialization.XmlAnyAttributeAttribute> atributos para dar suporte ao ciclo de dados desconhecido.  
  
## <a name="message-contract-versioning"></a>Controle de versão de contrato de mensagem  
 As diretrizes de controle de versão de contrato de mensagem são muito semelhantes aos contratos de dados de controle de versão. Se estrito versão for necessária, você deve não altere o corpo da mensagem, mas em vez disso, crie um novo contrato de mensagem com um nome qualificado exclusivo. Se você souber que você pode usar o controle de versão incerta, você pode adicionar novas partes de corpo de mensagem, mas não alterar ou remover as existentes. Este guia se aplica ao bare e encapsulado contratos de mensagem.  
  
 Cabeçalhos de mensagem sempre podem ser adicionados, mesmo se o controle de versão estrito está em uso. O sinalizador MustUnderstand pode afetar o controle de versão. Em geral, o controle de versão de modelo para cabeçalhos no [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] é conforme descrito na especificação de SOAP.  
  
## <a name="service-contract-versioning"></a>Controle de versão de contrato de serviço  
 Semelhante ao controle de versão de contrato de dados, controle de versão de contrato de serviço também envolve adicionando, alterando e removendo operações.  
  
### <a name="specifying-name-namespace-and-action"></a>Especificar o nome, Namespace e ação  
 Por padrão, o nome do contrato de serviço é o nome da interface. Seu namespace padrão é "http://tempuri.org", e a ação de cada operação é "http://tempuri.org/contractname/methodname". É recomendável que você especifique um nome e o namespace do contrato de serviço e uma ação para cada operação para evitar o uso de "http://tempuri.org" e para impedir que os nomes de interface e método seja exposto no contrato de serviço.  
  
### <a name="adding-parameters-and-operations"></a>Adicionando parâmetros e operações  
 Adicionando expostas pelo serviço de operações de serviço é uma alteração incondicional porque os clientes existentes não precisam se preocupar sobre essas novas operações.  
  
> [!NOTE]
>  Adicionando operações a um contrato de retorno de chamada dúplex é uma alteração significativa.  
  
### <a name="changing-operation-parameter-or-return-types"></a>Alterando tipos de retorno ou parâmetro de operação  
 Alterar os tipos de parâmetro ou retornado geralmente é uma alteração significativa, a menos que o novo tipo implementa o contrato de dados mesmo implementado pelo tipo antigo. Para fazer essa alteração, adicionar uma nova operação ao contrato de serviço ou definir um novo contrato de serviço.  
  
### <a name="removing-operations"></a>Removendo operações  
 Remover operações também é uma alteração significativa. Para fazer essa alteração, defina um novo contrato de serviço e expô-lo em um novo ponto de extremidade.  
  
### <a name="fault-contracts"></a>Contratos de falha  
 O <xref:System.ServiceModel.FaultContractAttribute> atributo permite que um desenvolvedor de contrato de serviço especificar informações sobre falhas que podem ser retornadas de operações do contrato.  
  
 Na lista de falhas descrito no contrato de serviço não é exaustiva. A qualquer momento, uma operação pode retornar falhas que não são descritas no seu contrato. Alterando, portanto, o conjunto de falhas descrita no contrato não é considerado recentes. Por exemplo, adicionando uma nova falha para o contrato usando o <xref:System.ServiceModel.FaultContractAttribute> ou remoção de uma falha existente do contrato.  
  
### <a name="service-contract-libraries"></a>Bibliotecas de contrato de serviço  
 As organizações podem ter bibliotecas de contratos onde um contrato é publicado em um repositório central e implementadores de serviço implementam contratos desse repositório. Nesse caso, quando você publica um contrato de serviço para o repositório é não têm controle sobre quem cria serviços que implementação-la. Portanto, você não pode modificar o contrato de serviço, uma vez publicado, renderizá-lo efetivamente imutável. [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]oferece suporte ao contrato de herança, que pode ser usada para criar um novo contrato que estende os contratos existentes. Para usar esse recurso, defina uma nova interface de contrato de serviço que herda da interface de contrato de serviço antiga e adicionar métodos para a nova interface. Você, em seguida, alterar o serviço que implementa o contrato antigo para implementar o novo contrato e altere a definição de ponto de extremidade de "versionOld" para usar o novo contrato. Para clientes de "versionOld", que o ponto de extremidade continuarão a aparecer como expondo o contrato de "versionOld"; para clientes de "versionNew", o ponto de extremidade será exibido para expor o contrato "versionNew".  
  
## <a name="address-and-binding-versioning"></a>Endereço e associação de controle de versão  
 As alterações para o endereço de ponto de extremidade e associação são as alterações recentes, a menos que os clientes são capazes de descobrir dinamicamente o novo endereço de ponto de extremidade ou associação. É um mecanismo para implementar essa funcionalidade usando um registro de descrição de descoberta Universal e integração (UDDI) e o padrão de invocação UDDI onde um cliente tenta se comunicar com um ponto de extremidade e, em caso de falha, consulta um UDDI conhecido Registro para os metadados do ponto de extremidade atual. O cliente usa o endereço e associação de metadados para se comunicar com o ponto de extremidade. Se essa comunicação for bem-sucedida, o cliente armazena em cache as informações de endereço e associação para uso futuro.  
  
## <a name="routing-service-and-versioning"></a>Controle de versão e o serviço de roteamento  
 Se as alterações feitas a um serviço são as recentes alterações e você precisa ter duas ou mais versões diferentes de um serviço em execução simultaneamente você pode usar o serviço de roteamento do WCF para rotear mensagens para a instância de serviço apropriado. O serviço de roteamento do WCF usa roteamento baseado em conteúdo, em outras palavras, ele usa informações dentro da mensagem para determinar onde rotear a mensagem. [!INCLUDE[crabout](../../../includes/crabout-md.md)]Consulte o serviço de roteamento de WCF [serviço de roteamento](../../../docs/framework/wcf/feature-details/routing-service.md). Para obter um exemplo de como usar o serviço de roteamento do WCF para controle de versão de serviço, consulte [como: controle de versão do serviço](../../../docs/framework/wcf/feature-details/how-to-service-versioning.md).  
  
## <a name="appendix"></a>Anexo  
 As diretrizes de controle de versão do contrato dados gerais quando for necessário estrito controle de versão são tratar os contratos de dados como imutável e criar novos quando são necessárias alterações. Uma nova classe precisa ser criado para cada novo contrato de dados, portanto, um mecanismo é necessária para evitar ter de levar o código existente que foi escrito em termos de dados antigos de contrato de classe e reescrevê-la em termos da nova classe de contrato de dados.  
  
 Um esse mecanismo é usar interfaces para definir os membros de cada contrato de dados e gravar o código de implementação interna em termos de interfaces, em vez de classes de contrato de dados que implementam as interfaces. O código a seguir para a versão 1 de um serviço mostra uma `IPurchaseOrderV1` interface e um `PurchaseOrderV1`:  
  
```  
public interface IPurchaseOrderV1  
{  
    string OrderId { get; set; }  
    string CustomerId { get; set; }  
}  
  
[DataContract(  
Name = "PurchaseOrder",  
Namespace = "http://examples.microsoft.com/WCF/2005/10/PurchaseOrder")]  
public class PurchaseOrderV1 : IPurchaseOrderV1  
{  
    [DataMember(...)]  
    public string OrderId {...}  
    [DataMember(...)]  
    public string CustomerId {...}  
}  
```  
  
 Enquanto as operações do contrato de serviço serão gravadas em termos de `PurchaseOrderV1`, a lógica de negócios reais seria em termos de `IPurchaseOrderV1`. Em seguida, na versão 2, haverá uma nova `IPurchaseOrderV2` interface e um novo `PurchaseOrderV2` classe conforme mostrado no código a seguir:  
  
```  
public interface IPurchaseOrderV2  
{  
    DateTime OrderDate { get; set; }  
}  
[DataContract(   
Name = "PurchaseOrder ",  
Namespace = "http://examples.microsoft.com/WCF/2006/02/PurchaseOrder")]  
public class PurchaseOrderV2 : IPurchaseOrderV1, IPurchaseOrderV2  
{  
    [DataMember(...)]  
    public DateTime OrderId {...}  
    [DataMember(...)]  
    public string CustomerId {...}  
    [DataMember(...)]  
    public DateTime OrderDate { ... }  
}  
```  
  
 O contrato de serviço será atualizado para incluir novas operações que são escritas em termos de `PurchaseOrderV2`. Lógica de negócios existentes gravada em termos de `IPurchaseOrderV1` continuará a funcionar para `PurchaseOrderV2` e nova lógica de negócios que precisa de `OrderDate` propriedade será gravada em termos de `IPurchaseOrderV2`.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 <xref:System.Runtime.Serialization.DataContractAttribute>  
 <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A>  
 <xref:System.Runtime.Serialization.DataContractAttribute.Namespace%2A>  
 <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A>  
 <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A>  
 <xref:System.Runtime.Serialization.IExtensibleDataObject>  
 <xref:System.Runtime.Serialization.ExtensionDataObject>  
 <xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A>  
 <xref:System.Xml.Serialization.XmlSerializer>  
 [Equivalência de contrato de dados](../../../docs/framework/wcf/feature-details/data-contract-equivalence.md)  
 [Retornos de chamada de serialização tolerantes à versão](../../../docs/framework/wcf/feature-details/version-tolerant-serialization-callbacks.md)
