---
title: Controle de versão de serviço
ms.date: 03/30/2017
ms.assetid: 37575ead-d820-4a67-8059-da11a2ab48e2
ms.openlocfilehash: 27d54cdf6f49bd9433f43290c97706af81d98b6b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61949780"
---
# <a name="service-versioning"></a>Controle de versão de serviço
Após a implantação inicial e possivelmente várias vezes durante a vida, serviços (e os pontos de extremidade que expõem) podem precisar ser alterada para uma variedade de motivos, como a alteração de requisitos de tecnologia da informação, as necessidades de negócio ou aborda outros problemas. Cada alteração introduz uma nova versão do serviço. Este tópico explica como considerar o controle de versão no Windows Communication Foundation (WCF).  
  
## <a name="four-categories-of-service-changes"></a>Quatro categorias das alterações de serviço  
 As alterações aos serviços que podem ser necessárias podem ser classificadas em quatro categorias:  
  
- Alterações de contrato: Por exemplo, uma operação pode ser adicionada ou um elemento de dados em uma mensagem pode ser adicionado ou alterado.  
  
- Alterações de endereço: Por exemplo, um serviço se move para um local diferente em que os pontos de extremidade têm novos endereços.  
  
- Alterações de associação: Por exemplo, alterações de um mecanismo de segurança ou alterarem suas configurações.  
  
- Alterações de implementação: Por exemplo, quando uma implementação de método interno é alterado.  
  
 Algumas dessas alterações são chamadas de "quebra" e outros são "incondicional". É uma alteração *incondicional* se todas as mensagens que seriam foram processadas com êxito na versão anterior são processadas com êxito na nova versão. Qualquer alteração que não atenda a esse critério é um *significativas* alterar.  
  
## <a name="service-orientation-and-versioning"></a>Controle de versão e a orientação de serviço  
 Um dos princípios de orientação de serviço é que clientes e serviços são autônomos (ou independente). Entre outras coisas, isso implica que os desenvolvedores de serviço não podem presumir que eles controlam ou até mesmo sabem sobre todos os clientes de serviço. Isso elimina a opção de recompilar e reimplantar todos os clientes quando uma versões de alterações de serviço. Este tópico pressupõe que o serviço adere a essa filosofia e, portanto, deve ser alterado ou "controle de versão" independentes de seus clientes.  
  
 Em casos em que uma alteração significativa é inesperado e não pode ser evitada, um aplicativo pode optar por ignorar essa filosofia e exigem que os clientes ser recompilados e reimplantados com uma nova versão do serviço.  
  
## <a name="contract-versioning"></a>Controle de versão do contrato  
 Contratos usados por um cliente não precisa ser o mesmo que o contrato usado pelo serviço; eles só precisam ser compatível.  
  
 Para contratos de serviço, significa que novas operações expostas pelo serviço podem ser adicionadas de compatibilidade, mas as operações existentes não podem ser removidas ou alteradas semanticamente.  
  
 Para contratos de dados, compatibilidade significa que o novo tipo de esquema definições podem ser adicionadas, mas definições de tipo de esquema existente não podem ser alteradas no maneiras de interrupção. Alterações significativas podem incluir a remoção de membros de dados ou alterar seu tipo de dados incompatíveis. Esse recurso permite que o serviço alguns latitude em como alterar a versão de seus contratos sem interromper os clientes. As duas próximas seções explicam incondicionais e alterações significativas que podem ser feitas nos dados do WCF e contratos de serviço.  
  
## <a name="data-contract-versioning"></a>Controle de versão de contrato de dados  
 Esta seção lida com controle de versão de dados ao usar o <xref:System.Runtime.Serialization.DataContractSerializer> e <xref:System.Runtime.Serialization.DataContractAttribute> classes.  
  
### <a name="strict-versioning"></a>Controle de versão estrito  
 Em muitos cenários quando alterar as versões é um problema, o desenvolvedor de serviço não tem controle sobre os clientes e, portanto, não é possível fazer suposições sobre como eles seriam reagir às alterações na mensagem XML ou esquema. Nesses casos, você deve garantir que as novas mensagens irá validar no esquema antigo, por dois motivos:  
  
- Os clientes antigos foram desenvolvidos com a suposição de que o esquema não será alterado. Eles podem falhar ao processar as mensagens que nunca foram projetados para.  
  
- Os clientes antigos podem executar a validação de esquema real no esquema antigo antes de tentar até mesmo processar as mensagens.  
  
 A abordagem recomendada em tais cenários é tratar os contratos de dados existente como imutável e criar novos com XML exclusivo nomes qualificados. O desenvolvedor de serviço seria, em seguida, adicione novos métodos para um contrato de serviço existente ou criar um novo contrato de serviço com métodos que usam o novo contrato de dados.  
  
 Ele geralmente será o caso em que um desenvolvedor de serviço precisa para escrever a lógica de negócios que deve ser executado em todas as versões de um contrato de dados mais o código específico da versão comercial para cada versão do contrato de dados. O apêndice no final deste tópico explica como as interfaces podem ser usadas para atender a essa necessidade.  
  
### <a name="lax-versioning"></a>Controle de versão incerto  
 Em muitos cenários, o desenvolvedor de serviço pode tornar a suposição de que a adição de um novo membro opcional ao contrato de dados não interromperá os clientes existentes. Isso exige que o desenvolvedor de serviço investigar se os clientes existentes não estão executando a validação de esquema e que eles ignoram membros de dados desconhecido. Nesses cenários, é possível tirar proveito dos recursos de contrato de dados para adicionar novos membros de forma incondicional. O desenvolvedor de serviço pode fazer essa suposição com confiança se os recursos de contrato de dados para controle de versão já foram usados para a primeira versão do serviço.  
  
 Suporte a pilhas de serviço WCF, serviços Web do ASP.NET e muitas outras Web *controle de versão lax*: ou seja, elas não geram exceções para novos membros de dados desconhecido em dados recebidos.  
  
 É fácil erroneamente acreditar que adicionar um novo membro não interromperá a clientes existentes. Se você não tiver certeza de que todos os clientes podem lidar com controle de versão incerta, a recomendação é usar as diretrizes de controle de versão estrito e tratar os dados contratos como imutáveis.  
  
 Para obter diretrizes detalhadas para controle de versão incerta e estrita de contratos de dados, consulte [práticas recomendadas: Controle de versão de contrato de dados](../../../docs/framework/wcf/best-practices-data-contract-versioning.md).  
  
### <a name="distinguishing-between-data-contract-and-net-types"></a>Fazer a distinção entre tipos .NET e o contrato de dados  
 Uma classe ou estrutura .NET pode ser projetada como um contrato de dados, aplicando o <xref:System.Runtime.Serialization.DataContractAttribute> à classe de atributo. O tipo .NET e suas projeções de contrato de dados são dois assuntos distintos. É possível ter vários tipos de .NET com a mesma projeção de contrato de dados. Essa distinção é especialmente útil ao permitir que você altere o tipo .NET, mantendo o contrato de dados projetados, mantendo a compatibilidade com clientes existentes até mesmo no sentido estrito da palavra. Há duas coisas que você sempre deve fazer para manter essa distinção entre o contrato de dados e o tipo de .NET:  
  
- Especifique um <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A> e <xref:System.Runtime.Serialization.DataContractAttribute.Namespace%2A>. Você sempre deve especificar o nome e o namespace do seu contrato de dados para impedir que o nome do tipo de .NET e o namespace sejam expostas no contrato. Dessa forma, se você decidir posteriormente alterar o namespace do .NET ou digite o nome, seu contrato de dados permanece o mesmo.  
  
- Especifique <xref:System.Runtime.Serialization.DataMemberAttribute.Name%2A>. Você sempre deve especificar o nome de seus membros de dados para impedir que seu nome de membro do .NET que está sendo exposto no contrato. Dessa forma, se você decidir posteriormente alterar o nome do .NET do membro, seu contrato de dados permanece o mesmo.  
  
### <a name="changing-or-removing-members"></a>A alteração ou remoção de membros  
 Alterando o nome ou tipo de dados de um membro ou removendo membros de dados é uma alteração significativa, mesmo se o controle de versão incerta é permitida. Se isso for necessário, crie um novo contrato de dados.  
  
 Se a compatibilidade de serviço é de importância alta, talvez considere ignorando os membros de dados não utilizados em seu código e deixá-los em vigor. Caso você esteja dividindo-se um membro de dados em vários membros, você pode considerar deixar o membro existente no local como uma propriedade que pode executar a divisão necessária e a nova agregação para clientes de nível inferior (clientes que não são atualizados para a versão mais recente).  
  
 Da mesma forma, as alterações para o namespace ou nome do contrato de dados são as alterações recentes.  
  
### <a name="round-trips-of-unknown-data"></a>Viagens de ida e volta de dados desconhecidos  
 Em alguns cenários, é necessário para "ida e volta" dados desconhecidos que vêm de membros adicionados em uma nova versão. Por exemplo, um serviço de "versionNew" envia dados com alguns membros adicionaram recentemente para um cliente "versionOld". O cliente ignora os membros recém-adicionados ao processar a mensagem, mas ele reenvia esses mesmos dados, incluindo os membros recém-adicionados, volta para o serviço versionNew. O cenário típico para isso é que as atualizações de dados onde os dados são recuperados do serviço de, alterados e retornados.  
  
 Para habilitar o ciclo completo de um determinado tipo, o tipo deve implementar o <xref:System.Runtime.Serialization.IExtensibleDataObject> interface. A interface contém uma propriedade, <xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A> que retorna o <xref:System.Runtime.Serialization.ExtensionDataObject> tipo. A propriedade é usada para armazenar quaisquer dados das versões futuras do contrato de dados é desconhecido para a versão atual. Esses dados são opaco ao cliente, mas quando a instância é serializada, o conteúdo do <xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A> propriedade foi escrita com o resto dos dados dos membros de contrato de dados.  
  
 É recomendável que todos os tipos de implementam essa interface para acomodar os futuros membros novos e desconhecidos.  
  
### <a name="data-contract-libraries"></a>Bibliotecas de contrato de dados  
 Pode haver bibliotecas de contratos de dados onde um contrato é publicado em um repositório central, e os implementadores de serviço e tipo de implementarem e expõem os contratos de dados a partir desse repositório. Nesse caso, quando você publica um contrato de dados para o repositório, você não tem controle sobre quem cria tipos que implementam a ele. Assim, você não pode modificar o contrato quando ela for publicada, renderizá-lo efetivamente imutável.  
  
### <a name="when-using-the-xmlserializer"></a>Ao usar o XmlSerializer  
 Os mesmos princípios de controle de versão se aplicam ao usar o <xref:System.Xml.Serialization.XmlSerializer> classe. Quando o controle de versão estrito for necessária, trate os contratos de dados como imutável e criar novos contratos de dados com nomes exclusivos e qualificados para as novas versões. Quando tiver certeza de que lax controle de versão pode ser usado, você pode adicionar novos membros serializáveis em novas versões, mas não alterar ou remover membros existentes.  
  
> [!NOTE]
>  O <xref:System.Xml.Serialization.XmlSerializer> usa o <xref:System.Xml.Serialization.XmlAnyElementAttribute> e <xref:System.Xml.Serialization.XmlAnyAttributeAttribute> atributos para dar suporte ao ciclo completo de dados desconhecidos.  
  
## <a name="message-contract-versioning"></a>Controle de versão de contrato de mensagem  
 As diretrizes para controle de versão de contrato de mensagem são muito semelhantes aos contratos de dados de controle de versão. Se o controle de versão estrito for necessária, você deve não altere o corpo da mensagem, mas em vez disso, crie um novo contrato de mensagem com um nome qualificado exclusivo. Se você souber que você pode usar o controle de versão incerto, você pode adicionar novas partes de corpo de mensagem, mas não alterar ou remover as existentes. Este guia se aplica à bare e encapsulado contratos de mensagem.  
  
 Cabeçalhos de mensagem sempre podem ser adicionados, mesmo se o controle de versão estrito está em uso. O sinalizador MustUnderstand pode afetar o controle de versão. Em geral, o modelo de controle de versão para os cabeçalhos no WCF é conforme descrito na especificação de SOAP.  
  
## <a name="service-contract-versioning"></a>Controle de versão de contrato de serviço  
 Semelhante ao controle de versão de contrato de dados, controle de versão de contrato de serviço também envolve adicionando, alterando e removendo operações.  
  
### <a name="specifying-name-namespace-and-action"></a>Especificando o nome, Namespace e ação  
 Por padrão, o nome de um contrato de serviço é o nome da interface. Seu namespace padrão é "http://tempuri.org", e ação da cada operação é "http://tempuri.org/contractname/methodname". É recomendável que você especifique explicitamente um nome e namespace do contrato de serviço e uma ação para cada operação evitar o uso de "http://tempuri.org" e para impedir que os nomes de interface e método sejam expostas no contrato de serviço.  
  
### <a name="adding-parameters-and-operations"></a>Adicionar operações e parâmetros  
 Adicionar operações de serviço expostas pelo serviço é uma alteração não separável porque os clientes existentes não precisam se preocupar sobre essas novas operações.  
  
> [!NOTE]
>  Adicionar operações a um contrato de retorno de chamada duplex é uma alteração significativa.  
  
### <a name="changing-operation-parameter-or-return-types"></a>Alterando o parâmetro de operação ou tipos de retorno  
 Alterar os tipos de parâmetro ou retornado geralmente é uma alteração significativa, a menos que o novo tipo implementa o mesmo contrato de dados implementado pelo tipo antigo. Para fazer essa alteração, adicione uma nova operação ao contrato de serviço ou definir um novo contrato de serviço.  
  
### <a name="removing-operations"></a>Removendo operações  
 Remover operações também é uma alteração significativa. Para fazer essa alteração, defina um novo contrato de serviço e expô-lo em um novo ponto de extremidade.  
  
### <a name="fault-contracts"></a>Contratos de falha  
 O <xref:System.ServiceModel.FaultContractAttribute> atributo permite que um desenvolvedor de contrato de serviço especificar informações sobre falhas que podem ser retornadas de operações do contrato.  
  
 Na lista de falhas, descrito no contrato de um serviço não é exaustiva. A qualquer momento, uma operação pode retornar falhas que não são descritas em seu contrato. Alterar, portanto, o conjunto de falhas descrita no contrato não é considerado significativas. Por exemplo, adicionando uma nova falha para o contrato usando o <xref:System.ServiceModel.FaultContractAttribute> ou remoção de uma falha de existente do contrato.  
  
### <a name="service-contract-libraries"></a>Bibliotecas de contrato de serviço  
 As organizações podem ter as bibliotecas de contratos em um contrato é publicado para um repositório central e implementadores de serviço implementam contratos de meio desse repositório. Nesse caso, quando você publica um contrato de serviço para o repositório não tiver nenhum controle sobre quem cria serviços que implementação-lo. Portanto, você não pode modificar o contrato de serviço depois de publicado, renderizá-lo efetivamente imutável. O WCF oferece suporte a herança de contrato, que pode ser usada para criar um novo contrato que se estende de contratos existentes. Para usar esse recurso, defina uma nova interface de contrato de serviço que herda da interface do contrato de serviço antiga, em seguida, adicione métodos para a nova interface. Você, em seguida, altere o serviço que implementa o antigo contrato para implementar o novo contrato e altere a definição de ponto de extremidade de "versionOld" para usar o novo contrato. Para clientes de "versionOld", que o ponto de extremidade continuarão a aparecer como expor o contrato de "versionOld"; para clientes de "versionNew", o ponto de extremidade será exibido para expor o contrato de "versionNew".  
  
## <a name="address-and-binding-versioning"></a>Endereço e associação de controle de versão  
 As alterações para o endereço do ponto de extremidade e associação são as alterações recentes, a menos que os clientes são capazes de detectar dinamicamente o novo endereço de ponto de extremidade ou a associação. Um mecanismo para implementar essa funcionalidade é usando um registro Universal Description Discovery UDDI (and Integration) e o padrão de invocação de UDDI em que um cliente tenta se comunicar com um ponto de extremidade e, em caso de falha, consulta um UDDI bem conhecido Registro para os metadados do ponto de extremidade atual. O cliente usa o endereço e associação de metadados para se comunicar com o ponto de extremidade. Se essa comunicação for bem-sucedida, o cliente armazena em cache as informações de endereço e a associação para uso futuro.  
  
## <a name="routing-service-and-versioning"></a>Controle de versão e o serviço de roteamento  
 Se as alterações feitas em um serviço são as alterações significativas e você precisa ter duas ou mais versões diferentes de um serviço em execução ao mesmo tempo você pode usar o serviço de roteamento do WCF para rotear mensagens para a instância de serviço apropriado. O serviço de roteamento do WCF usa roteamento baseado em conteúdo, em outras palavras, ele usa informações dentro da mensagem para determinar onde rotear a mensagem. Para obter mais informações sobre o serviço de roteamento do WCF, consulte [serviço de roteamento](../../../docs/framework/wcf/feature-details/routing-service.md). Para obter um exemplo de como usar o serviço de roteamento do WCF para controle de versão de serviço, consulte [How To: Controle de versão de serviço](../../../docs/framework/wcf/feature-details/how-to-service-versioning.md).  
  
## <a name="appendix"></a>Anexo  
 As diretrizes de controle de versão de contrato de dados gerais ao controle de versão estrito é necessária é tratar a contratos de dados como imutável e criar novos quando alterações são necessárias. Uma nova classe precisa ser criada para cada novo contrato de dados, portanto, é necessário um mecanismo para evitar ter que usar o código existente que foi escrito em termos dos dados antigos de contrato de classe e reescrevê-lo em termos da nova classe de contrato de dados.  
  
 Um desses mecanismos é usar interfaces para definir os membros de cada contrato de dados e gravar o código de implementação interna em termos de interfaces em vez de classes de contrato de dados que implementam as interfaces. Mostra o código a seguir para a versão 1 de um serviço de um `IPurchaseOrderV1` interface e um `PurchaseOrderV1`:  
  
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
  
 Embora seriam escritas em termos de operações do contrato de serviço `PurchaseOrderV1`, a lógica de negócios real seria em termos de `IPurchaseOrderV1`. Em seguida, na versão 2, haveria uma nova `IPurchaseOrderV2` interface e um novo `PurchaseOrderV2` classe conforme mostrado no código a seguir:  
  
```  
public interface IPurchaseOrderV2  
{  
    DateTime OrderDate { get; set; }  
}

[DataContract(   
Name = "PurchaseOrder",  
Namespace = "http://examples.microsoft.com/WCF/2006/02/PurchaseOrder")]  
public class PurchaseOrderV2 : IPurchaseOrderV1, IPurchaseOrderV2  
{  
    [DataMember(...)]  
    public string OrderId {...}  
    [DataMember(...)]  
    public string CustomerId {...}  
    [DataMember(...)]  
    public DateTime OrderDate { ... }  
}  
```  
  
 O contrato de serviço seria atualizado para incluir novas operações que são escritas em termos de `PurchaseOrderV2`. Lógica de negócios existente, escrita em termos de `IPurchaseOrderV1` continuará a funcionar para `PurchaseOrderV2` e a nova lógica de negócios que precisa de `OrderDate` propriedade seria escrita em termos de `IPurchaseOrderV2`.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A>
- <xref:System.Runtime.Serialization.DataContractAttribute.Namespace%2A>
- <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A>
- <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A>
- <xref:System.Runtime.Serialization.IExtensibleDataObject>
- <xref:System.Runtime.Serialization.ExtensionDataObject>
- <xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A>
- <xref:System.Xml.Serialization.XmlSerializer>
- [Equivalência de contrato de dados](../../../docs/framework/wcf/feature-details/data-contract-equivalence.md)
- [Retornos de chamada de serialização tolerantes à versão](../../../docs/framework/wcf/feature-details/version-tolerant-serialization-callbacks.md)
