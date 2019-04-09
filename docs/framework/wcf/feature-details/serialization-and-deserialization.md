---
title: Serialização e desserialização
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3d71814c-bda7-424b-85b7-15084ff9377a
ms.openlocfilehash: d9afa49525f03c06f94b1b7b704fb3d9caa9e19d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59101810"
---
# <a name="serialization-and-deserialization"></a>Serialização e desserialização
Windows Communication Foundation (WCF) inclui um novo mecanismo de serialização, o <xref:System.Runtime.Serialization.DataContractSerializer>. O <xref:System.Runtime.Serialization.DataContractSerializer> converte entre objetos do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] e XML, em ambas as direções. Este tópico explica como o serializador funciona.  
  
 Ao serializar [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] objetos, o serializador compreende uma variedade de modelos de programação, incluindo o novo de serialização *contrato de dados* modelo. Para obter uma lista completa dos tipos com suporte, consulte [tipos com suporte pelo serializador de contrato de dados](../../../../docs/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer.md). Para obter uma introdução a contratos de dados, consulte [contratos de dados usando](../../../../docs/framework/wcf/feature-details/using-data-contracts.md).  
  
 Ao desserializar XML, o serializador usa as classes <xref:System.Xml.XmlReader> e <xref:System.Xml.XmlWriter>. Ele também dá suporte a <xref:System.Xml.XmlDictionaryReader> e <xref:System.Xml.XmlDictionaryWriter> classes para habilitá-lo produzir o XML otimizado em alguns casos, como quando o XML binário do WCF usando o formato.  
  
 O WCF também inclui um serializador complementar, o <xref:System.Runtime.Serialization.NetDataContractSerializer>. O <xref:System.Runtime.Serialization.NetDataContractSerializer> é semelhante a serializadores <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> e <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> porque também emite nomes de tipo do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] como parte dos dados serializados. Ele é usado quando os mesmos tipos são compartilhados nas terminações de serialização e desserialização. O <xref:System.Runtime.Serialization.DataContractSerializer> e o <xref:System.Runtime.Serialization.NetDataContractSerializer> derivam de uma classe base comum, a <xref:System.Runtime.Serialization.XmlObjectSerializer>.  
  
> [!WARNING]
>  O <xref:System.Runtime.Serialization.DataContractSerializer> serializa cadeias de caracteres que contêm caracteres de controle com um valor hexadecimal abaixo de 20 como as entidades XML. Isso pode causar um problema com um cliente não WCF ao enviar esses dados para um serviço WCF.  
  
## <a name="creating-a-datacontractserializer-instance"></a>Criando uma instância DataContractSerializer  
 Construir uma instância do <xref:System.Runtime.Serialization.DataContractSerializer> é uma etapa importante. Após a compilação, você não poderá alterar as configurações.  
  
### <a name="specifying-the-root-type"></a>Especificando o tipo da raiz  
 O *raiz do tipo* é o tipo dos quais instâncias serializadas ou desserializadas. O <xref:System.Runtime.Serialization.DataContractSerializer> tem várias sobrecargas de construtor, mas, no mínimo, um tipo de raiz deve ser fornecido usando o `type` parâmetro.  
  
 Um serializador criado para um determinado tipo de raiz não pode ser usado para serializar (ou desserializar) outro tipo, a menos que o tipo seja derivado do tipo raiz. O exemplo a seguir mostra duas classes.  
  
 [!code-csharp[c_StandaloneDataContractSerializer#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_standalonedatacontractserializer/cs/source.cs#1)]
 [!code-vb[c_StandaloneDataContractSerializer#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_standalonedatacontractserializer/vb/source.vb#1)]  
  
 Esse código cria uma instância `DataContractSerializer` que pode ser usada somente para serializar ou desserializar as instâncias da classe `Person`.  
  
 [!code-csharp[c_StandaloneDataContractSerializer#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_standalonedatacontractserializer/cs/source.cs#2)]
 [!code-vb[c_StandaloneDataContractSerializer#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_standalonedatacontractserializer/vb/source.vb#2)]  
  
### <a name="specifying-known-types"></a>Especificando tipos conhecidos  
 Se o polimorfismo estiver envolvido nos tipos que estão sendo serializados que já não estejam sendo tratados usando o atributo <xref:System.Runtime.Serialization.KnownTypeAttribute> ou algum outro mecanismo, uma lista de tipos conhecidos possíveis deve ser passada para o construtor do serializador usando o parâmetro `knownTypes`. Para obter mais informações sobre tipos conhecidos, consulte [tipos conhecidos de contrato de dados](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).  
  
 O exemplo a seguir mostra uma classe, `LibraryPatron`, que inclui uma coleção de um tipo específico, o `LibraryItem`. A segunda classe define o tipo `LibraryItem`. A terceira e a quarta classe (`Book` e `Newspaper`) herdam da classe `LibraryItem`.  
  
 [!code-csharp[c_StandaloneDataContractSerializer#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_standalonedatacontractserializer/cs/source.cs#3)]  
 [!code-vb[c_StandaloneDataContractSerializer#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_standalonedatacontractserializer/vb/source.vb#3)]  
  
 O código a seguir constrói uma instância do serializador usando o parâmetro `knownTypes`.  
  
 [!code-csharp[c_StandaloneDataContractSerializer#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_standalonedatacontractserializer/cs/source.cs#4)]
 [!code-vb[c_StandaloneDataContractSerializer#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_standalonedatacontractserializer/vb/source.vb#4)]  
  
### <a name="specifying-the-default-root-name-and-namespace"></a>Especificando o nome e o namespace de raiz padrão  
 Normalmente, quando um objeto é serializado, o nome padrão e o namespace do elemento XML mais externo são determinados de acordo com o nome e o namespace do contrato de dados. Os nomes de todos os elementos internos são determinados dos nomes de membro de dados, e seu namespace é o namespace do contrato de dados. O exemplo a seguir define os valores `Name` e `Namespace` nos construtores das classes <xref:System.Runtime.Serialization.DataContractAttribute> e <xref:System.Runtime.Serialization.DataMemberAttribute>.  
  
 [!code-csharp[c_StandaloneDataContractSerializer#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_standalonedatacontractserializer/cs/source.cs#5)]
 [!code-vb[c_StandaloneDataContractSerializer#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_standalonedatacontractserializer/vb/source.vb#5)]  
  
 Serializar uma instância da classe `Person` gera XML semelhante ao seguinte.  
  
```xml  
<PersonContract xmlns="http://schemas.contoso.com">  
  <AddressMember>  
    <StreetMember>123 Main Street</StreetMember>  
   </AddressMember>  
</PersonContract>  
```  
  
 Entretanto, você pode personalizar o nome e o namespace padrão do elemento raiz passando os valores dos parâmetros `rootName` e `rootNamespace` para o construtor <xref:System.Runtime.Serialization.DataContractSerializer>. Observe que o `rootNamespace` não afeta o namespace dos elementos contidos que correspondem aos membros de dados. Ele afeta somente o namespace do elemento mais externo.  
  
 Esses valores podem ser passados como cadeias de caracteres ou instâncias da classe <xref:System.Xml.XmlDictionaryString> para permitir a otimização usando o formato XML binário.  
  
### <a name="setting-the-maximum-objects-quota"></a>Definindo a cota máxima de objetos  
 Algumas sobrecargas do construtor `DataContractSerializer` têm um parâmetro `maxItemsInObjectGraph`. Este parâmetro determina o número máximo de objetos que o serializador serializa ou desserializa em uma única chamada de método <xref:System.Runtime.Serialization.XmlObjectSerializer.ReadObject%2A>. (O método sempre lê um objeto raiz, mas esse objeto pode ter outros objetos em seus membros de dados. Esses objetos podem ter outros objetos e assim por diante). O padrão é 65536. Observe que, ao serializar ou desserializar matrizes, cada entrada de matriz conta como um objeto separado. Além disso, observe que alguns objetos podem ter uma grande representação de memória e, portanto, essa cota apenas pode não ser suficiente para evitar um ataque de negação de serviço. Para obter mais informações, consulte [considerações sobre segurança para dados](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md). Se você precisa aumentar esta cota além do valor padrão, é importante fazer isso no lado do envio (serialização) e do recebimento (desserialização) porque isso se aplica tanto para ler e gravar dados.  
  
### <a name="round-trips"></a>Viagens de ida e volta  
 Um *ida e volta* ocorre quando um objeto é desserializado e serializado novamente em uma única operação. Portanto, ele vai de XML para uma instância de objeto e volta novamente para um fluxo XML.  
  
 Alguns `DataContractSerializer` sobrecargas de construtor tem um `ignoreExtensionDataObject` parâmetro, que é definido como `false` por padrão. Nesse modo padrão, os dados podem ser enviados em uma viagem de ida e volta de uma versão mais recente de um contrato de dados através de uma versão anterior, e de volta para a versão mais recente sem perda, contanto que o contrato de dados implemente a interface <xref:System.Runtime.Serialization.IExtensibleDataObject>. Por exemplo, suponha que a versão 1 do contrato de dados de `Person` contenha os membros de dados `Name` e `PhoneNumber`, e a versão 2 adicione um membro `Nickname`. Se `IExtensibleDataObject` estiver implementado, ao enviar informações da versão 2 para a versão 1, os dados de `Nickname` estarão armazenados e, em seguida, emitidos novamente quando os dados forem serializados novamente; portanto, nenhum dado é perdido na viagem. Para obter mais informações, consulte [contratos de dados compatíveis por encaminhamento](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md) e [controle de versão de contrato de dados](../../../../docs/framework/wcf/feature-details/data-contract-versioning.md).  
  
#### <a name="security-and-schema-validity-concerns-with-round-trips"></a>Preocupações de segurança e validade do esquema com viagens de ida e volta  
 As viagens de ida e volta podem ter implicações de segurança. Por exemplo, desserializar e armazenar grandes quantidades de dados desconhecidos podem ser um risco de segurança. Pode haver problemas de segurança sobre emitir novamente esses dados que não haja nenhuma maneira para verificar, especialmente se assinaturas digitais estiverem envolvidas. Por exemplo, no cenário anterior, o ponto de extremidade da versão 1 pode ser assinar um valor de `Nickname` que contém dados mal-intencionados. Finalmente, pode haver preocupações de validade de esquema: um ponto de extremidade pode querer sempre emitir os dados que sigam restritamente o contrato indicado e não nenhum valor extra. No exemplo anterior, o contrato do ponto de extremidade da versão 1 diz que emite somente `Name` e `PhoneNumber`, e se a validação do esquema estiver sendo usada, emitir o valor extra de `Nickname` causa falha na validação.  
  
#### <a name="enabling-and-disabling-round-trips"></a>Ativar e desativar viagens de ida e volta  
 Para desativar viagens de ida e volta, não implemente a interface <xref:System.Runtime.Serialization.IExtensibleDataObject>. Se você não tiver controle sobre os tipos, defina o parâmetro `ignoreExtensionDataObject` como `true` para alcançar o mesmo efeito.  
  
### <a name="object-graph-preservation"></a>Preservação do gráfico do objeto  
 Normalmente, o serializador não se importa com a identidade do objeto, como no código a seguir.  
  
 [!code-csharp[c_StandaloneDataContractSerializer#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_standalonedatacontractserializer/cs/source.cs#6)]
 [!code-vb[c_StandaloneDataContractSerializer#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_standalonedatacontractserializer/vb/source.vb#6)]  
  
 O código a seguir cria uma ordem de compra.  
  
 [!code-csharp[c_StandaloneDataContractSerializer#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_standalonedatacontractserializer/cs/source.cs#7)]
 [!code-vb[c_StandaloneDataContractSerializer#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_standalonedatacontractserializer/vb/source.vb#7)]  
  
 Observe que os campos `billTo` e `shipTo` são definidos para a mesma instância de objeto. No entanto, o XML gerado duplica as informações duplicadas e é semelhante ao XML a seguir.  
  
```xml  
<PurchaseOrder>  
  <billTo><street>123 Main St.</street></billTo>  
  <shipTo><street>123 Main St.</street></shipTo>  
</PurchaseOrder>  
```  
  
 No entanto, essa abordagem tem as seguintes características, que podem ser indesejáveis:  
  
-   Desempenho. Replicar dados é ineficiente.  
  
-   Referências circulares. Se os objetos se referirem a si mesmos, mesmo por meio de outros objetos, serializar por replicação resultará em um loop infinito. (O serializador gera um <xref:System.Runtime.Serialization.SerializationException> se isso acontece.)  
  
-   Semântica. Muitas vezes, é importante preservar o fato de que duas referências são para o mesmo objeto, e não para dois objetos idênticos.  
  
 Por esses motivos, algumas sobrecargas de construtor do `DataContractSerializer` têm um parâmetro `preserveObjectReferences` (o padrão é `false`). Quando esse parâmetro é definido como `true`, um método especial de codificação de referências de objeto, que compreende apenas WCF, é usado. Quando estiver definido como `true`, o exemplo de código XML agora se parecerá com o seguinte.  
  
```xml  
<PurchaseOrder ser:id="1">  
  <billTo ser:id="2"><street ser:id="3">123 Main St.</street></billTo>  
  <shipTo ser:ref="2"/>  
</PurchaseOrder>  
```  
  
 O namespace "ser" refere-se ao namespace padrão de serialização, `http://schemas.microsoft.com/2003/10/Serialization/`. Cada dado é serializada apenas uma vez e recebe um número de identificação, e os usos subsequentes resultam em uma referência a dados já serializados.  
  
> [!IMPORTANT]
>  Se os atributos “id” e “ref” estiverem presentes no `XMLElement` do contrato de dados, o atributo “ref” será aceito e o atributo “ID”, ignorado.  
  
 É importante entender as limitações desse modo:  
  
-   O XML a `DataContractSerializer` produz com `preserveObjectReferences` definido como `true` não é interoperável com nenhuma outra tecnologia e pode ser acessado somente por outra `DataContractSerializer` instância, também com `preserveObjectReferences` definido como `true`.  
  
-   Não há suporte de metadados (esquema) para esse recurso. O esquema que é gerado é válido somente para o caso em que `preserveObjectReferences` está definido como `false`.  
  
-   Esse recurso pode fazer o processo de serialização e desserialização ser executado mais lentamente. Embora os dados não precisem ser replicados, as comparações adicionais de objeto devem ser executadas nesse modo.  
  
> [!CAUTION]
>  Quando o modo `preserveObjectReferences` está ativado, ele é especialmente importante para definir o valor de `maxItemsInObjectGraph` para a cota correta. Devido à maneira como as matrizes são tratadas nesse modo, é fácil para que um invasor construir uma pequena mensagem mal-intencionada que resulta em um grande consumo de memória limitada somente pela cota de `maxItemsInObjectGraph`.  
  
### <a name="specifying-a-data-contract-surrogate"></a>Especificando um substituto para os contratos de dados  
 Algumas sobrecargas de construtor do `DataContractSerializer` têm um parâmetro `dataContractSurrogate`, que pode ser definido como `null` por padrão. Caso contrário, você pode usar para especificar uma *substituto de contrato de dados*, que é um tipo que implementa o <xref:System.Runtime.Serialization.IDataContractSurrogate> interface. Você pode, em seguida, usar a interface para personalizar o processo de serialização e desserialização. Para obter mais informações, consulte [substitutos de contrato de dados](../../../../docs/framework/wcf/extending/data-contract-surrogates.md).  
  
## <a name="serialization"></a>Serialização  
 As informações a seguir aplicam-se a qualquer classe que herda de <xref:System.Runtime.Serialization.XmlObjectSerializer>, incluindo as classes <xref:System.Runtime.Serialization.DataContractSerializer> e <xref:System.Runtime.Serialization.NetDataContractSerializer>.  
  
### <a name="simple-serialization"></a>Serialização simples  
 A maneira mais básica para serializar um objeto é passá-lo para o método <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteObject%2A>. Há três sobrecargas, cada uma para escrever em um <xref:System.IO.Stream>, <xref:System.Xml.XmlWriter> ou <xref:System.Xml.XmlDictionaryWriter>. Com a sobrecarga <xref:System.IO.Stream>, a saída é XML na codificação UTF-8. Com a sobrecarga <xref:System.Xml.XmlDictionaryWriter>, o serializador otimiza a saída para XML binário.  
  
 Ao usar o <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteObject%2A> método, o serializador usa o nome padrão e o namespace para o elemento wrapper e grava ele junto com o conteúdo (consulte a seção anterior "Especificando o padrão raiz nome e Namespace").  
  
 O exemplo a seguir demonstra a escrita com um <xref:System.Xml.XmlDictionaryWriter>.  
  
 [!code-csharp[c_StandaloneDataContractSerializer#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_standalonedatacontractserializer/cs/source.cs#8)]
 [!code-vb[c_StandaloneDataContractSerializer#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_standalonedatacontractserializer/vb/source.vb#8)]  
  
 Isso gera um XML semelhante ao seguinte.  
  
```xml  
<Person>  
  <Name>Jay Hamlin</Name>  
  <Address>123 Main St.</Address>  
</Person>  
```  
  
### <a name="step-by-step-serialization"></a>Serialização passo a passo  
 Use os métodos <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteStartObject%2A>, <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteObjectContent%2A> e <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteEndObject%2A> para gravar o elemento final, escrever o conteúdo do objeto e fechar o elemento wrapper, respectivamente.  
  
> [!NOTE]
>  Não há nenhuma sobrecarga de <xref:System.IO.Stream> desses métodos.  
  
 Essa serialização passo a passo tem dois usos comuns. Um é inserir conteúdo como atributos ou comentários entre `WriteStartObject` e `WriteObjectContent`, conforme mostrado no exemplo a seguir.  
  
 [!code-csharp[c_StandaloneDataContractSerializer#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_standalonedatacontractserializer/cs/source.cs#9)]
 [!code-vb[c_StandaloneDataContractSerializer#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_standalonedatacontractserializer/vb/source.vb#9)]  
  
 Isso gera um XML semelhante ao seguinte.  
  
```xml  
<Person serializedBy="myCode">  
  <Name>Jay Hamlin</Name>  
  <Address>123 Main St.</Address>  
</Person>  
```  
  
 Outro uso comum é evitar usar <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteStartObject%2A> e <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteEndObject%2A> totalmente, e escrever seu próprio elemento wrapper personalizado (ou até mesmo não escrever um wrapper), conforme mostrado no código a seguir.  
  
 [!code-csharp[c_StandaloneDataContractSerializer#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_standalonedatacontractserializer/cs/source.cs#10)]
 [!code-vb[c_StandaloneDataContractSerializer#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_standalonedatacontractserializer/vb/source.vb#10)]  
  
 Isso gera um XML semelhante ao seguinte.  
  
```xml  
<MyCustomWrapper>  
  <Name>Jay Hamlin</Name>  
  <Address>123 Main St.</Address>  
</MyCustomWrapper>  
```  
  
> [!NOTE]
>  Usar a serialização passo a passo pode resultar em XML de esquema inválido.  
  
## <a name="deserialization"></a>Desserialização  
 As informações a seguir aplicam-se a qualquer classe que herda de <xref:System.Runtime.Serialization.XmlObjectSerializer>, incluindo as classes <xref:System.Runtime.Serialization.DataContractSerializer> e <xref:System.Runtime.Serialization.NetDataContractSerializer>.  
  
 A maneira mais básica de desserializar um objeto é chamar uma das sobrecargas de método <xref:System.Runtime.Serialization.XmlObjectSerializer.ReadObject%2A>. Há três sobrecargas, cada uma para ler comum <xref:System.Xml.XmlDictionaryReader>, `XmlReader` ou `Stream`. Observe que a sobrecarga de `Stream` cria um <xref:System.Xml.XmlDictionaryReader> textual que não é protegido por nenhuma cota, e deve ser usada somente para ler dados confiáveis.  
  
 Observe também que o objeto que o método `ReadObject` retorna deve ser convertido para o tipo apropriado.  
  
 O código a seguir constrói uma instância <xref:System.Runtime.Serialization.DataContractSerializer> e um <xref:System.Xml.XmlDictionaryReader> e, em seguida, desserializa uma instância `Person`.  
  
 [!code-csharp[c_StandaloneDataContractSerializer#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_standalonedatacontractserializer/cs/source.cs#11)]
 [!code-vb[c_StandaloneDataContractSerializer#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_standalonedatacontractserializer/vb/source.vb#11)]  
  
 Antes de chamar o método <xref:System.Runtime.Serialization.XmlObjectSerializer.ReadObject%2A>, posicione a leitora XML no elemento wrapper ou em um nó de não conteúdo que precede o elemento wrapper. Você pode fazer isso chamando o método <xref:System.Xml.XmlReader.Read%2A> de <xref:System.Xml.XmlReader> ou sua derivação e testando o <xref:System.Xml.XmlReader.NodeType%2A>, conforme mostrado no código a seguir.  
  
 [!code-csharp[c_StandaloneDataContractSerializer#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_standalonedatacontractserializer/cs/source.cs#12)]
 [!code-vb[c_StandaloneDataContractSerializer#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_standalonedatacontractserializer/vb/source.vb#12)]  
  
 Observe que você pode ler atributos neste elemento wrapper antes de enviar o leitor para `ReadObject`.  
  
 Ao usar uma das simples `ReadObject` sobrecargas, o desserializador procura o nome padrão e o namespace no elemento wrapper (consulte a seção anterior, "Especificando o padrão raiz nome e Namespace") e gera uma exceção se ele encontrar desconhecida elemento. No exemplo anterior, o elemento wrapper `<Person>` é esperado. O método <xref:System.Runtime.Serialization.XmlObjectSerializer.IsStartObject%2A> é chamado para verificar se o leitor está localizado em um elemento que seja nomeado como esperado.  
  
 Há uma maneira de desabilitar a verificação de nome desse elemento wrapper; algumas sobrecargas do método `ReadObject` têm o parâmetro booliano `verifyObjectName`, que é definido como `true` por padrão. Quando definidas como `false`, o nome e o namespace do elemento wrapper são ignorados. Isso é útil para ler o XML que foi escrito usando o mecanismo passo a passo de serialização descrito anteriormente.  
  
## <a name="using-the-netdatacontractserializer"></a>Usando o NetDataContractSerializer  
 A principal diferença entre o `DataContractSerializer` e o <xref:System.Runtime.Serialization.NetDataContractSerializer> é que o `DataContractSerializer` usa nomes de contrato de dados, enquanto que o `NetDataContractSerializer` gera nomes de assembly e de tipo completos do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] no XML serializável. Isso significa que exatamente os mesmos tipos devem ser compartilhados entre os pontos de extremidade de serialização e desserialização. Isso significa que o mecanismo de tipos conhecidos não é necessário com o `NetDataContractSerializer` porque os tipos exatos a serem desserializados são sempre conhecidos.  
  
 No entanto, alguns problemas podem ocorrer:  
  
-   Segurança. Qualquer tipo encontrado no XML que está sendo desserializado é carregado. Isso pode ser explorado para forçar o carregamento de tipos mal-intencionados. Usando o `NetDataContractSerializer` com não-confiável de dados devem ser feitos apenas se um *associador de serialização* é usado (usando o <xref:System.Runtime.Serialization.NetDataContractSerializer.Binder%2A> parâmetro de propriedade ou construtor). O associador permite que apenas tipos seguros sejam carregados. O mecanismo Associador é idêntico ao usado pelos tipos no <xref:System.Runtime.Serialization>.  
  
-   Controle de versão. Usar nomes completos de tipo e assembly no XML restringe significativamente o controle de versão de tipos. O exemplo a seguir não pode ser modificado: nomes de tipo, namespaces, nomes de assembly e versões de assembly. Definir a propriedade <xref:System.Runtime.Serialization.NetDataContractSerializer.AssemblyFormat%2A> ou o parâmetro do construtor como <xref:System.Runtime.Serialization.Formatters.FormatterAssemblyStyle.Simple> em vez do valor padrão de <xref:System.Runtime.Serialization.Formatters.FormatterAssemblyStyle.Full> permite alterações de versão do assembly, mas não para tipos de parâmetros genéricos.  
  
-   Interoperabilidade. Como os nomes de tipo e assembly do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] estão incluídos no XML, as plataformas diferentes de [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] não podem acessar os dados resultantes.  
  
-   Desempenho. Gravar os nomes de tipo e assembly aumenta significativamente o tamanho do XML resultante.  
  
 Esse mecanismo é semelhante à serialização binária ou SOAP usada por [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] remoto (especificamente, <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> e <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>).  
  
 Usar `NetDataContractSerializer` é semelhante a usar `DataContractSerializer`, com as seguintes diferenças:  
  
-   Os construtores não exigem que você especifique um tipo de raiz. Você pode serializar qualquer tipo com a mesma instância do `NetDataContractSerializer`.  
  
-   Os construtores não aceitam uma lista de tipos conhecidos. O mecanismo de tipos conhecidos será desnecessário se os nomes de tipo forem serializados no XML.  
  
-   Os construtores não aceitam um substituto do contrato de dados. Em vez disso, aceitam um parâmetro <xref:System.Runtime.Serialization.ISurrogateSelector> chamado `surrogateSelector` (que mapeia para a propriedade <xref:System.Runtime.Serialization.NetDataContractSerializer.SurrogateSelector%2A>). Este é um mecanismo substituto herdado.  
  
-   Os construtores aceitam um parâmetro chamado `assemblyFormat` do <xref:System.Runtime.Serialization.Formatters.FormatterAssemblyStyle> que mapeia para a propriedade <xref:System.Runtime.Serialization.NetDataContractSerializer.AssemblyFormat%2A>. Conforme discutido anteriormente, isso pode ser usado para melhorar os recursos de controle de versão do serializador. Isso é idêntico ao mecanismo <xref:System.Runtime.Serialization.Formatters.FormatterAssemblyStyle> na serialização binária ou SOAP.  
  
-   Os construtores aceitam um parâmetro <xref:System.Runtime.Serialization.StreamingContext> chamado `context` que mapeia para a propriedade <xref:System.Runtime.Serialization.NetDataContractSerializer.Context%2A>. Você pode usar isso para passar informações para os tipos que estão sendo serializados. Esse uso é idêntico ao do mecanismo <xref:System.Runtime.Serialization.StreamingContext> usado em outras classes <xref:System.Runtime.Serialization>.  
  
-   Os métodos <xref:System.Runtime.Serialization.NetDataContractSerializer.Serialize%2A> e <xref:System.Runtime.Serialization.NetDataContractSerializer.Deserialize%2A> são aliases para os métodos <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteObject%2A> e <xref:System.Runtime.Serialization.XmlObjectSerializer.ReadObject%2A>. Eles existem para fornecer um modelo de programação mais consistente com serialização binária ou SOAP.  
  
 Para obter mais informações sobre esses recursos, consulte [serialização binária](../../../../docs/standard/serialization/binary-serialization.md).  
  
 Os formatos XML que o `NetDataContractSerializer` e o `DataContractSerializer` usam não são normalmente compatíveis. Ou seja, tentar serializar com um desses serializadores e desserializar com o outro não é um cenário com suporte.  
  
 Além disso, observe que o `NetDataContractSerializer` não gera o nome completo do tipo e assembly do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] para cada nó no grafo de objeto. Ele gera essas informações apenas quando são ambíguas. Isto é, ele gera no nível do objeto raiz e para qualquer caso polimórfico.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.Runtime.Serialization.NetDataContractSerializer>
- <xref:System.Runtime.Serialization.XmlObjectSerializer>
- [Serialização binária](../../../../docs/standard/serialization/binary-serialization.md)
- [Tipos com suporte fornecido pelo serializador de contrato de dados](../../../../docs/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer.md)
