---
title: Controle de versão de serviço
ms.date: 03/30/2017
ms.assetid: 37575ead-d820-4a67-8059-da11a2ab48e2
ms.openlocfilehash: ea5e80e33d1b29e01e6d1867c50bb3bb973b01c3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183117"
---
# <a name="service-versioning"></a>Controle de versão de serviço
Após a implantação inicial, e potencialmente várias vezes durante sua vida, os serviços (e os pontos finais que eles expõem) podem precisar ser alterados por uma variedade de razões, como mudanças nas necessidades dos negócios, requisitos de tecnologia da informação ou para atender a outros Questões. Cada alteração introduz uma nova versão do serviço. Este tópico explica como considerar a versão na Windows Communication Foundation (WCF).  
  
## <a name="four-categories-of-service-changes"></a>Quatro categorias de mudanças de serviço  
 As alterações nos serviços que podem ser necessários podem ser classificadas em quatro categorias:  
  
- Alterações de contrato: Por exemplo, uma operação pode ser adicionada ou um elemento de dados em uma mensagem pode ser adicionado ou alterado.  
  
- Alterações de endereço: Por exemplo, um serviço se move para um local diferente onde os pontos finais têm novos endereços.  
  
- Alterações de vinculação: Por exemplo, um mecanismo de segurança muda ou suas configurações mudam.  
  
- Alterações de implementação: Por exemplo, quando uma implementação de método interno muda.  
  
 Algumas dessas mudanças são chamadas de "quebra" e outras são "ininterruptas". Uma alteração não é *desconexa* se todas as mensagens que teriam sido processadas com sucesso na versão anterior forem processadas com sucesso na nova versão. Qualquer mudança que não atenda a esse critério é uma mudança *de ruptura.*  
  
## <a name="service-orientation-and-versioning"></a>Orientação e versão de serviço  
 Um dos princípios da orientação de serviço é que os serviços e clientes são autônomos (ou independentes). Entre outras coisas, isso implica que os desenvolvedores de serviços não podem assumir que controlam ou mesmo conhecem todos os clientes do serviço. Isso elimina a opção de reconstruir e reimplantar todos os clientes quando um serviço muda de versão. Este tópico pressupõe que o serviço adere a este princípio e, portanto, deve ser alterado ou "versionado" independente de seus clientes.  
  
 Nos casos em que uma mudança de quebra é inesperada e não pode ser evitada, um aplicativo pode optar por ignorar esse princípio e exigir que os clientes sejam reconstruídos e reimplantados com uma nova versão do serviço.  
  
## <a name="contract-versioning"></a>Versão do contrato  
 Os contratos utilizados por um cliente não precisam ser os mesmos do contrato utilizado pelo serviço; eles só precisam ser compatíveis.  
  
 Para contratos de serviço, a compatibilidade significa que novas operações expostas pelo serviço podem ser adicionadas, mas as operações existentes não podem ser removidas ou alteradas semanticamente.  
  
 Para contratos de dados, a compatibilidade significa que novas definições de tipo de esquema podem ser adicionadas, mas as definições de tipo de esquema existentes não podem ser alteradas de maneiras de separação. A quebra de alterações pode incluir a remoção de membros de dados ou a alteração incompativelmente do seu tipo de dados. Esse recurso permite ao serviço alguma latitude na alteração da versão de seus contratos sem quebrar clientes. As duas próximas seções explicam alterações ininterruptas e de quebra que podem ser feitas em dados e contratos de serviços do WCF.  
  
## <a name="data-contract-versioning"></a>Controle de versão de contrato de dados  
 Esta seção lida com a <xref:System.Runtime.Serialization.DataContractSerializer> <xref:System.Runtime.Serialization.DataContractAttribute> versão de dados ao usar as classes e.  
  
### <a name="strict-versioning"></a>Versão estrita  
 Em muitos cenários ao mudar de versões é um problema, o desenvolvedor de serviços não tem controle sobre os clientes e, portanto, não pode fazer suposições sobre como eles reagiriam a mudanças na mensagem XML ou esquema. Nestes casos, você deve garantir que as novas mensagens serão validadas contra o esquema antigo, por duas razões:  
  
- Os antigos clientes foram desenvolvidos com a suposição de que o esquema não mudará. Eles podem falhar em processar mensagens para as as que nunca foram projetadas.  
  
- Os clientes antigos podem realizar validação de esquema real contra o esquema antigo antes mesmo de tentar processar as mensagens.  
  
 A abordagem recomendada em tais cenários é tratar os contratos de dados existentes como imutáveis e criar novos com nomes qualificados XML exclusivos. O desenvolvedor de serviços adicionaria novos métodos a um contrato de serviço existente ou criaria um novo contrato de serviço com métodos que usam o novo contrato de dados.  
  
 Muitas vezes será o caso de um desenvolvedor de serviços precisar escrever alguma lógica de negócios que deve ser executada dentro de todas as versões de um contrato de dados mais código comercial específico de versão para cada versão do contrato de dados. O apêndice no final deste tópico explica como as interfaces podem ser usadas para satisfazer essa necessidade.  
  
### <a name="lax-versioning"></a>Versão lax  
 Em muitos outros cenários, o desenvolvedor de serviços pode fazer a suposição de que a adição de um novo membro opcional ao contrato de dados não quebrará os clientes existentes. Isso exige que o desenvolvedor de serviços investigue se os clientes existentes não estão realizando a validação do esquema e que eles ignoram membros de dados desconhecidos. Nesses cenários, é possível aproveitar os recursos do contrato de dados para adicionar novos membros de forma ininterrupta. O desenvolvedor de serviços pode fazer essa suposição com confiança se os recursos do contrato de dados para a versão já foram usados para a primeira versão do serviço.  
  
 O WCF, ASP.NET Web Services e muitas outras pilhas de serviços da Web suportam *a versão frouxa*: ou seja, eles não lançam exceções para novos membros de dados desconhecidos nos dados recebidos.  
  
 É fácil acreditar equivocadamente que adicionar um novo membro não quebrará os clientes existentes. Se você não tem certeza de que todos os clientes podem lidar com a versão frouxa, a recomendação é usar as rígidas diretrizes de versão e tratar os contratos de dados como imutáveis.  
  
 Para obter diretrizes detalhadas para a versão frouxa e rigorosa dos contratos de dados, consulte [Práticas Recomendadas: Versão do contrato de dados](best-practices-data-contract-versioning.md).  
  
### <a name="distinguishing-between-data-contract-and-net-types"></a>Distinção entre contrato de dados e tipos .NET  
 Uma classe ou estrutura .NET pode ser projetada como <xref:System.Runtime.Serialization.DataContractAttribute> um contrato de dados aplicando o atributo à classe. O tipo .NET e suas projeções de contrato de dados são duas questões distintas. É possível ter vários tipos .NET com a mesma projeção de contrato de dados. Essa distinção é especialmente útil para permitir que você altere o tipo .NET, mantendo o contrato de dados projetado, mantendo assim a compatibilidade com os clientes existentes mesmo no sentido estrito da palavra. Há duas coisas que você deve sempre fazer para manter essa distinção entre o tipo .NET e o contrato de dados:  
  
- Especificar <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A> <xref:System.Runtime.Serialization.DataContractAttribute.Namespace%2A>a e . Você deve sempre especificar o nome e o namespace do seu contrato de dados para evitar que o nome e o namespace do seu tipo .NET sejam expostos no contrato. Desta forma, se você decidir mais tarde alterar o namespace ou o nome do tipo .NET, seu contrato de dados permanece o mesmo.  
  
- Especifique <xref:System.Runtime.Serialization.DataMemberAttribute.Name%2A>. Você deve sempre especificar o nome de seus membros de dados para evitar que seu nome de membro .NET seja exposto no contrato. Dessa forma, se você decidir posteriormente alterar o nome .NET do membro, seu contrato de dados permanece o mesmo.  
  
### <a name="changing-or-removing-members"></a>Alterando ou removendo membros  
 Alterar o nome ou o tipo de dados de um membro ou remover membros de dados é uma mudança de ruptura, mesmo que a versão frouxa seja permitida. Se isso for necessário, crie um novo contrato de dados.  
  
 Se a compatibilidade de serviço for de alta importância, você pode considerar ignorar os membros de dados não utilizados em seu código e deixá-los no lugar. Se você estiver dividindo um membro de dados em vários membros, você pode considerar deixar o membro existente no lugar como uma propriedade que pode realizar a divisão e a agregação necessária para clientes de nível inferior (clientes que não são atualizados para a versão mais recente).  
  
 Da mesma forma, alterações no nome ou no namespace do contrato de dados estão quebrando alterações.  
  
### <a name="round-trips-of-unknown-data"></a>Ida e volta de dados desconhecidos  
 Em alguns cenários, há a necessidade de "ida e volta" dados desconhecidos que vêm de membros adicionados em uma nova versão. Por exemplo, um serviço "versionNew" envia dados com alguns membros recém-adicionados para um cliente "versionOld". O cliente ignora os membros recém-adicionados ao processar a mensagem, mas reenvia esses mesmos dados, incluindo os membros recém-adicionados, de volta ao serviço versionNew. O cenário típico para isso são as atualizações de dados onde os dados são recuperados do serviço, alterados e devolvidos.  
  
 Para habilitar o tropeço redondo para um determinado <xref:System.Runtime.Serialization.IExtensibleDataObject> tipo, o tipo deve implementar a interface. A interface contém <xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A> uma propriedade, que retorna o <xref:System.Runtime.Serialization.ExtensionDataObject> tipo. A propriedade é usada para armazenar quaisquer dados de versões futuras do contrato de dados que são desconhecidas da versão atual. Esses dados são opacos para o cliente, mas quando a <xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A> instância é serializada, o conteúdo da propriedade é escrito com o resto dos dados dos membros do contrato de dados.  
  
 Recomenda-se que todos os seus tipos implementem essa interface para acomodar novos e desconhecidos futuros membros.  
  
### <a name="data-contract-libraries"></a>Bibliotecas de contratos de dados  
 Pode haver bibliotecas de contratos de dados onde um contrato é publicado em um repositório central, e implementadores de serviços e tipos implementam e expõem contratos de dados a partir desse repositório. Nesse caso, quando você publica um contrato de dados no repositório, você não tem controle sobre quem cria tipos que o implementam. Assim, você não pode modificar o contrato uma vez que ele é publicado, tornando-o efetivamente imutável.  
  
### <a name="when-using-the-xmlserializer"></a>Ao usar o XmlSerializer  
 Os mesmos princípios de versão <xref:System.Xml.Serialization.XmlSerializer> se aplicam ao usar a classe. Quando for necessária uma versão rigorosa, trate os contratos de dados como imutáveis e crie novos contratos de dados com nomes únicos e qualificados para as novas versões. Quando você tem certeza de que a versão frouxa pode ser usada, você pode adicionar novos membros serializáveis em novas versões, mas não alterar ou remover membros existentes.  
  
> [!NOTE]
> O <xref:System.Xml.Serialization.XmlSerializer> uso <xref:System.Xml.Serialization.XmlAnyElementAttribute> <xref:System.Xml.Serialization.XmlAnyAttributeAttribute> e atributos para suportar o tropeço redondo de dados desconhecidos.  
  
## <a name="message-contract-versioning"></a>Versão do contrato de mensagem  
 As diretrizes para a versão do contrato de mensagem são muito semelhantes às versões de contratos de dados. Se for necessária uma versão rigorosa, você não deve alterar seu corpo de mensagem, mas criar um novo contrato de mensagem com um nome qualificado único. Se você sabe que pode usar uma versão frouxa, você pode adicionar novas partes do corpo da mensagem, mas não alterar ou remover as existentes. Esta orientação se aplica tanto a contratos de mensagens nuas e embrulhadas.  
  
 Cabeçalhos de mensagem sempre podem ser adicionados, mesmo que a versão estrita esteja em uso. O sinalizador MustUnderstand pode afetar a versão. Em geral, o modelo de versão para cabeçalhos em WCF é descrito na especificação SOAP.  
  
## <a name="service-contract-versioning"></a>Versão do contrato de serviço  
 Semelhante à versão de contrato de dados, a versão do contrato de serviço também envolve a adição, alteração e remoção de operações.  
  
### <a name="specifying-name-namespace-and-action"></a>Especificando nome, namespace e ação  
 Por padrão, o nome de um contrato de serviço é o nome da interface. Seu namespace padrãohttp://tempuri.orgé " ", ehttp://tempuri.org/contractname/methodnamea ação de cada operação é " ". Recomenda-se que você especifique explicitamente um nome e namespace para o contratohttp://tempuri.orgde serviço, e uma ação para cada operação para evitar o uso " " e para evitar que nomes de interface e método sejam expostos no contrato do serviço.  
  
### <a name="adding-parameters-and-operations"></a>Adicionando parâmetros e operações  
 Adicionar operações de serviço expostas pelo serviço é uma mudança ininterrupta porque os clientes existentes não precisam se preocupar com essas novas operações.  
  
> [!NOTE]
> Adicionar operações a um contrato de retorno de chamada duplex é uma mudança de ruptura.  
  
### <a name="changing-operation-parameter-or-return-types"></a>Alterando os tipos de parâmetro ou retorno da operação  
 Alterar parâmetros ou tipos de retorno geralmente é uma mudança de ruptura, a menos que o novo tipo implemente o mesmo contrato de dados implementado pelo tipo antigo. Para fazer tal alteração, adicione uma nova operação ao contrato de prestação de serviços ou defina um novo contrato de prestação de serviços.  
  
### <a name="removing-operations"></a>Remoção de operações  
 Remover operações também é uma mudança de ruptura. Para fazer tal mudança, defina um novo contrato de serviço e exponha-o em um novo ponto final.  
  
### <a name="fault-contracts"></a>Contratos de falha  
 O <xref:System.ServiceModel.FaultContractAttribute> atributo permite que um desenvolvedor de contratos de serviçoes especifique informações sobre falhas que podem ser devolvidas das operações do contrato.  
  
 A lista de falhas descritas no contrato de um serviço não é considerada exaustiva. A qualquer momento, uma operação pode devolver falhas que não estão descritas em seu contrato. Portanto, a alteração do conjunto de faltas descritas no contrato não é considerada quebra. Por exemplo, adicionar uma nova falha <xref:System.ServiceModel.FaultContractAttribute> ao contrato usando ou removendo uma falha existente do contrato.  
  
### <a name="service-contract-libraries"></a>Bibliotecas de contratos de serviço  
 As organizações podem ter bibliotecas de contratos onde um contrato é publicado em um repositório central e os implementadores de serviços implementam contratos a partir desse repositório. Neste caso, quando você publica um contrato de serviço no repositório, você não tem controle sobre quem cria serviços que o implementam. Portanto, você não pode modificar o contrato de serviço uma vez publicado, tornando-o efetivamente imutável. O WCF apoia a herança contratual, que pode ser usada para criar um novo contrato que amplia os contratos existentes. Para usar esse recurso, defina uma nova interface de contrato de serviço que herda da interface de contrato de serviço antiga e, em seguida, adicione métodos à nova interface. Em seguida, você altera o serviço que implementa o contrato antigo para implementar o novo contrato e altera a definição de ponto final "versionOld" para usar o novo contrato. Para clientes "versionOld", o ponto final continuará a aparecer como expondo o contrato "versionOld"; para clientes "versionNew", o ponto final aparecerá para expor o contrato "versionNew".  
  
## <a name="address-and-binding-versioning"></a>Versão de endereço e vinculação  
 Alterações no endereço de ponto final e na vinculação estão quebrando alterações, a menos que os clientes sejam capazes de descobrir dinamicamente o novo endereço de ponto final ou vinculação. Um mecanismo para implementar esse recurso é usando um registro de Descrição e Integração universal (UDDI) e o Padrão de Invocação UDDI onde um cliente tenta se comunicar com um ponto final e, após falha, consulta um UDDI bem conhecido registro dos metadados de ponto final atuais. Em seguida, o cliente usa o endereço e a vinculação a partir deste metadados para se comunicar com o ponto final. Se essa comunicação for bem-sucedida, o cliente armazena o endereço e as informações vinculativas para uso futuro.  
  
## <a name="routing-service-and-versioning"></a>Serviço de roteamento e versão  
 Se as alterações feitas em um serviço forem uma violação e você precisar ter duas ou mais versões diferentes de um serviço em execução simultânea, você pode usar o Serviço de Roteamento do WCF para encaminhar mensagens para a instância de serviço apropriada. O Serviço de Roteamento wcf usa roteamento baseado em conteúdo, ou seja, usa informações dentro da mensagem para determinar para onde direcionar a mensagem. Para obter mais informações sobre o Serviço de Roteamento wcf consulte [Serviço de roteamento](./feature-details/routing-service.md). Para um exemplo de como usar o Serviço de Roteamento WCF para versões de serviço, consulte [Como: Versão de serviço](./feature-details/how-to-service-versioning.md).  
  
## <a name="appendix"></a>Apêndice  
 A orientação geral de versão do contrato de dados quando a versão estrita é necessária é tratar os contratos de dados como imutáveis e criar novos quando as alterações forem necessárias. Uma nova classe precisa ser criada para cada novo contrato de dados, de modo que um mecanismo é necessário para evitar ter que pegar o código existente que foi escrito em termos da antiga classe de contrato de dados e reescrevê-lo em termos da nova classe de contrato de dados.  
  
 Um desses mecanismos é usar interfaces para definir os membros de cada contrato de dados e escrever código de implementação interna em termos das interfaces, em vez das classes de contrato de dados que implementam as interfaces. O código a seguir para a `IPurchaseOrderV1` versão `PurchaseOrderV1`1 de um serviço mostra uma interface e um:  
  
```csharp  
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
  
 Enquanto as operações do contrato de `PurchaseOrderV1`serviço seriam escritas em termos `IPurchaseOrderV1`de , a lógica real do negócio seria em termos de . Em seguida, na versão 2, `IPurchaseOrderV2` haveria uma `PurchaseOrderV2` nova interface e uma nova classe, como mostrado no seguinte código:  
  
```csharp
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
  
 O contrato de serviço seria atualizado para incluir novas `PurchaseOrderV2`operações que são escritas em termos de . A lógica empresarial existente escrita `IPurchaseOrderV1` em termos `PurchaseOrderV2` de continuaria a funcionar `OrderDate` e a nova lógica `IPurchaseOrderV2`de negócios que precisa da propriedade seria escrita em termos de .  
  
## <a name="see-also"></a>Confira também

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
- [Equivalência de contrato de dados](./feature-details/data-contract-equivalence.md)
- [Retornos de chamada de serialização tolerantes à versão](./feature-details/version-tolerant-serialization-callbacks.md)
