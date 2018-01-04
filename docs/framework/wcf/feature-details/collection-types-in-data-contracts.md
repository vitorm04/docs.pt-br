---
title: "Tipos de coleção em contratos de dados"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- collection types [WCF], data contracts
- data contracts [WCF], collection types
- collection types [WCF]
ms.assetid: 9b45b28e-0a82-4ea3-8c33-ec0094aff9d5
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e74bd7d90d5653890fd5cf48e76c81d0227c6172
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="collection-types-in-data-contracts"></a>Tipos de coleção em contratos de dados
Um *coleção* é uma lista de itens de um determinado tipo. No [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], essas listas podem ser representadas usando matrizes ou em uma variedade de outros tipos (lista genérica, genérico <xref:System.ComponentModel.BindingList%601>, <xref:System.Collections.Specialized.StringCollection>, ou <xref:System.Collections.ArrayList>). Por exemplo, uma coleção pode conter uma lista de endereços para um cliente específico. Essas coleções são chamadas *liste coleções*, independentemente de seu tipo real.  
  
 Uma forma especial de coleção existe que representa uma associação entre um item (a "chave") e outro (o "valor"). No [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], esses são representados pelos tipos como <xref:System.Collections.Hashtable> e o dicionário genérico. Por exemplo, uma coleção de associação pode mapear uma cidade ("chave") para a população ("valor"). Essas coleções são chamadas *coleções de dicionário*, independentemente de seu tipo real.  
  
 Coleções recebem tratamento especial no modelo de contrato de dados.  
  
 Tipos que implementam o <xref:System.Collections.IEnumerable> reconhecido interface, inclusive matrizes e coleções genéricas, como coleções. Desses, tipos que implementam o <xref:System.Collections.IDictionary> ou genérico <xref:System.Collections.Generic.IDictionary%602> interfaces são coleções de dicionário; todos os outros são coleções de lista.  
  
 Requisitos adicionais em tipos de coleção, como ter um método chamado `Add` e um construtor padrão, são discutidos em detalhes nas seções a seguir. Isso garante que os tipos de coleção podem ser serializados e desserializados. Isso significa que algumas coleções não são diretamente suportadas, como genérica <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> (porque ele não possui construtor padrão). No entanto, para obter informações sobre como contornar essas restrições, consulte a seção "Usando coleção Interface tipos e coleções somente leitura", mais adiante neste tópico.  
  
 Os tipos contidos em coleções devem ser tipos de contrato de dados ou ser serializável. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Tipos com suporte pelo serializador de contrato de dados](../../../../docs/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer.md).  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]o que é e o que não é considerado uma coleção válida, bem como sobre como as coleções são serializadas, consulte as informações sobre serializando coleções na seção "Regras de coleta avançados" deste tópico.  
  
## <a name="interchangeable-collections"></a>Coleções intercambiáveis  
 Todas as coleções de lista do mesmo tipo são consideradas como tendo os mesmos dados contrato (a menos que eles estão personalizados usando o <xref:System.Runtime.Serialization.CollectionDataContractAttribute> de atributo, conforme discutido posteriormente neste tópico). Assim, por exemplo, os contratos de dados a seguir são equivalentes.  
  
 [!code-csharp[c_collection_types_in_data_contracts#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_collection_types_in_data_contracts/cs/program.cs#0)]
 [!code-vb[c_collection_types_in_data_contracts#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_collection_types_in_data_contracts/vb/program.vb#0)]  
  
 Ambos os contratos de dados resultam em XML semelhante ao seguinte código.  
  
```xml  
<PurchaseOrder>  
    <customerName>...</customerName>  
    <items>  
        <Item>...</Item>  
        <Item>...</Item>  
        <Item>...</Item>  
        ...  
    </items>  
    <comments>  
        <string>...</string>  
        <string>...</string>  
        <string>...</string>  
        ...  
    </comments>  
</PurchaseOrder>  
```  
  
 Intercâmbio de coleção permite que você use, por exemplo, um tipo de coleção otimizado para desempenho do servidor e um tipo de coleção a ser associado a componentes de interface do usuário no cliente.  
  
 Semelhante a coleções de lista, todas as coleções de dicionário que têm os mesmos tipos de chave e valor são consideradas como tendo os mesmos dados contrato (a menos que personalizado com o <xref:System.Runtime.Serialization.CollectionDataContractAttribute> atributo).  
  
 Somente o assuntos de tipo de contrato de dados agora está preocupada equivalência de coleção, não os tipos de .NET. Ou seja, uma coleção de Type1 é considerada equivalente a uma coleção de Type2 se Type1 e Type2 têm contratos de dados equivalentes.  
  
 Coleções genéricas não são consideradas como tendo os mesmos dados contrato como coleções genéricas do tipo `Object`. (Por exemplo, os dados de contratos para <xref:System.Collections.ArrayList> e genérica <xref:System.Collections.Generic.List%601> de `Object` são as mesmas.)  
  
## <a name="using-collection-interface-types-and-read-only-collections"></a>Usando coleções somente leitura e os tipos de Interface de coleção  
 Tipos de interface de coleção (<xref:System.Collections.IEnumerable>, <xref:System.Collections.IDictionary>genérica <xref:System.Collections.Generic.IDictionary%602>, ou interfaces derivam essas interfaces) também são considerados como tendo contratos de dados de coleção, equivalente a coleção de contratos de dados para tipos de coleção real. Portanto, é possível declarar o tipo que está sendo serializado como um tipo de interface de coleção e os resultados são os mesmos, como se tivesse sido usado um tipo de coleção real. Por exemplo, os contratos de dados a seguir são equivalentes.  
  
 [!code-csharp[c_collection_types_in_data_contracts#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_collection_types_in_data_contracts/cs/program.cs#1)]
 [!code-vb[c_collection_types_in_data_contracts#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_collection_types_in_data_contracts/vb/program.vb#1)]  
  
 Durante a serialização, quando o tipo declarado é uma interface, o tipo de instância real usado pode ser qualquer tipo que implementa essa interface. Restrições discutidos anteriormente (ter um construtor padrão e um `Add` método) não se aplicam. Por exemplo, você pode definir endereços em Customer2 a uma instância do genérico <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> do endereço, embora diretamente, você não pode declarar um membro de dados de tipo genérico <xref:System.Collections.ObjectModel.ReadOnlyCollection%601>.  
  
 Durante a desserialização, quando o tipo declarado é uma interface, o mecanismo de serialização escolhe um tipo que implementa a interface declarada e o tipo é instanciado. De tipos conhecidos mecanismo (descrito na [tipos conhecidos de contrato de dados](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)) não tem nenhum efeito aqui; a escolha do tipo é criada em [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
## <a name="customizing-collection-types"></a>Personalizando tipos de coleção  
 Você pode personalizar os tipos de coleção usando o <xref:System.Runtime.Serialization.CollectionDataContractAttribute> atributo, que tem vários usos.  
  
 Observe que personalizando coleta tipos comprometimentos coleção obrigatórios, portanto, geralmente é recomendável para evitar aplicar esse atributo sempre que possível. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Esse problema, consulte a seção "Regras de coleta avançados" mais adiante neste tópico.  
  
### <a name="collection-data-contract-naming"></a>Contrato de dados de coleção de nomenclatura  
 As regras de nomeação de tipos de coleção são semelhantes às para nomear tipos de contrato de dados regulares, conforme descrito em [nomes de contrato de dados](../../../../docs/framework/wcf/feature-details/data-contract-names.md), embora existam algumas diferenças importantes:  
  
-   O <xref:System.Runtime.Serialization.CollectionDataContractAttribute> atributo é usado para personalizar o nome, em vez do <xref:System.Runtime.Serialization.DataContractAttribute> atributo. O <xref:System.Runtime.Serialization.CollectionDataContractAttribute> também tem um atributo `Name` e `Namespace` propriedades.  
  
-   Quando o <xref:System.Runtime.Serialization.CollectionDataContractAttribute> atributo não é aplicado, o nome padrão e o namespace para tipos de coleção dependem se os nomes e os namespaces de tipos contidos na coleção. Eles não são afetados pelo nome e o namespace do tipo de coleção em si. Para obter um exemplo, consulte os seguintes tipos.  
  
    ```  
    public CustomerList1 : Collection<string> {}  
    public StringList1 : Collection<string> {}  
    ```  
  
 Nome de contrato de dados de ambos os tipos é "ArrayOfstring" e não "CustomerList1" ou "StringList1". Isso significa que a serialização de qualquer um desses tipos no nível raiz gera XML semelhante ao seguinte código.  
  
```xml  
<ArrayOfstring>  
    <string>...</string>  
    <string>...</string>  
    <string>...</string>  
    ...  
</ArrayOfstring>  
```  
  
 Essa regra de nomenclatura foi escolhida para garantir que qualquer tipo não personalizada que representa uma lista de cadeias de caracteres tem o mesmo contrato de dados e a representação XML. Isso possibilita o intercâmbio de coleção. Neste exemplo, CustomerList1 e StringList1 são intercambiáveis completamente.  
  
 No entanto, quando o <xref:System.Runtime.Serialization.CollectionDataContractAttribute> atributo é aplicado, a coleção se torna um contrato de dados de coleta personalizado, mesmo se nenhuma propriedade estiver definida no atributo. O nome e o namespace dos dados de coleção de contrato e dependem do tipo de coleção em si. Para obter um exemplo, consulte o seguinte tipo.  
  
 [!code-csharp[c_collection_types_in_data_contracts#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_collection_types_in_data_contracts/cs/program.cs#2)]
 [!code-vb[c_collection_types_in_data_contracts#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_collection_types_in_data_contracts/vb/program.vb#2)]  
  
 Quando serializado, o XML resultante é semelhante ao seguinte.  
  
```xml  
<CustomerList2>  
    <string>...</string>  
    <string>...</string>  
    <string>...</string>  
    ...  
</CustomerList2>  
```  
  
 Observe que isso não é equivalente a representação XML dos tipos não personalizada.  
  
-   Você pode usar o `Name` e `Namespace` propriedades para obter mais personalizar a nomeação. Consulte a seguinte classe.  
  
     [!code-csharp[c_collection_types_in_data_contracts#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_collection_types_in_data_contracts/cs/program.cs#3)]
     [!code-vb[c_collection_types_in_data_contracts#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_collection_types_in_data_contracts/vb/program.vb#3)]  
  
 O XML resultante é semelhante ao seguinte.  
  
```xml  
<cust_list>  
    <string>...</string>  
    <string>...</string>  
    <string>...</string>  
    ...  
</cust_list>  
```  
  
 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]a seção "Regras de coleta avançada" neste tópico.  
  
### <a name="customizing-the-repeating-element-name-in-list-collections"></a>Personalizando o nome de elemento de repetição em coleções de lista  
 Lista de coleções contêm as entradas repetidas. Normalmente, cada entrada de repetição é representada como um elemento nomeado de acordo com o nome do contrato de dados do tipo contido na coleção.  
  
 No `CustomerList` exemplos, as cadeias de caracteres de coleções contidas. O nome de contrato de dados para o tipo primitivo de cadeia de caracteres é "string", para o elemento de repetição foi "\<cadeia de caracteres >".  
  
 No entanto, usando o <xref:System.Runtime.Serialization.CollectionDataContractAttribute.ItemName%2A> propriedade o <xref:System.Runtime.Serialization.CollectionDataContractAttribute> de atributo, essa repetição nome de elemento pode ser personalizado. Para obter um exemplo, consulte o seguinte tipo.  
  
 [!code-csharp[c_collection_types_in_data_contracts#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_collection_types_in_data_contracts/cs/program.cs#4)]
 [!code-vb[c_collection_types_in_data_contracts#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_collection_types_in_data_contracts/vb/program.vb#4)]  
  
 O XML resultante é semelhante ao seguinte.  
  
```xml  
<CustomerList4>  
    <customer>...</customer>  
    <customer>...</customer>  
    <customer>...</customer>  
    ...  
</CustomerList4>  
```  
  
 O namespace do elemento de repetição é sempre o mesmo que o namespace do contrato de dados de coleção, que pode ser personalizado usando o `Namespace` propriedade, conforme descrito anteriormente.  
  
### <a name="customizing-dictionary-collections"></a>Personalizando a coleções de dicionário  
 Coleções do dicionário são essencialmente listas de entradas, onde cada entrada tem uma chave seguida por um valor. Assim como com listas regulares, você pode alterar o nome do elemento que corresponde ao elemento de repetição usando o <xref:System.Runtime.Serialization.CollectionDataContractAttribute.ItemName%2A> propriedade.  
  
 Além disso, você pode alterar os nomes dos elementos que representam a chave e o valor usando o <xref:System.Runtime.Serialization.CollectionDataContractAttribute.KeyName%2A> e <xref:System.Runtime.Serialization.CollectionDataContractAttribute.ValueName%2A> propriedades. Os namespaces para esses elementos são o mesmo que o namespace do contrato de dados de coleção.  
  
 Para obter um exemplo, consulte o seguinte tipo.  
  
 [!code-csharp[c_collection_types_in_data_contracts#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_collection_types_in_data_contracts/cs/program.cs#5)]
 [!code-vb[c_collection_types_in_data_contracts#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_collection_types_in_data_contracts/vb/program.vb#5)]  
  
 Quando serializado, o XML resultante é semelhante ao seguinte.  
  
```xml  
<CountriesOrRegionsWithCapitals>  
    <entry>  
        <countryorregion>USA</countryorregion>  
        <capital>Washington</capital>  
    </entry>  
    <entry>  
        <countryorregion>France</countryorregion>  
        <capital>Paris</capital>  
    </entry>  
    ...  
</CountriesOrRegionsWithCapitals>  
```  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]coleções de dicionário, consulte a seção "Regras de coleta avançados" mais adiante neste tópico.  
  
## <a name="collections-and-known-types"></a>Coleções e tipos conhecidos  
 Você não precisa adicionar tipos de coleção de tipos conhecidos quando polimorficamente usado no lugar de outras coleções ou interfaces de coleção. Por exemplo, se você declarar um membro de dados do tipo <xref:System.Collections.IEnumerable> e usá-lo para enviar uma instância do <xref:System.Collections.ArrayList>, você não precisa adicionar <xref:System.Collections.ArrayList> para tipos conhecidos.  
  
 Quando você usa coleções polimorficamente no lugar de tipos de coleção não, eles devem ser adicionados aos tipos conhecidos. Por exemplo, se você declarar um membro de dados do tipo `Object` e usá-lo para enviar uma instância do <xref:System.Collections.ArrayList>, adicionar <xref:System.Collections.ArrayList> para tipos conhecidos.  
  
 Isso não permite a serialização de qualquer coleção equivalente polimorficamente. Por exemplo, quando você adiciona <xref:System.Collections.ArrayList> à lista de tipos conhecidos no exemplo anterior, isso não permite que você atribua a `Array of Object` classe, embora tenha um contrato de dados equivalente. Isso não é diferente do comportamento de tipos conhecidos regular na serialização de tipos de coleção não, mas é especialmente importante entender no caso de coleções porque é muito comum a ser equivalente para coleções.  
  
 Durante a serialização, apenas um tipo pode ser conhecido no escopo especificado para um contrato de dados e equivalentes coleções de todos os tem os mesmos contratos de dados. Isso significa que, no exemplo anterior, você não pode adicionar ambos <xref:System.Collections.ArrayList> e `Array of Object` para tipos conhecidos no mesmo escopo. Novamente, isso é equivalente ao comportamento de tipos conhecidos para tipos de coleção não, mas é especialmente importante entender para coleções.  
  
 Também podem ser necessários para conteúdo de coleções de tipos conhecidos. Por exemplo, se um <xref:System.Collections.ArrayList> realmente contém instâncias de `Type1` e `Type2`, ambos os tipos devem ser adicionados aos tipos conhecidos.  
  
 O exemplo a seguir mostra um gráfico de objeto construído corretamente usando coleções e tipos conhecidos. O exemplo é um pouco contrived porque em um aplicativo real, você normalmente não deve definir os seguintes membros de dados como `Object`e, portanto, não terão problemas conhecidos de tipo/polimorfismo.  
  
 [!code-csharp[c_collection_types_in_data_contracts#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_collection_types_in_data_contracts/cs/program.cs#6)]
 [!code-vb[c_collection_types_in_data_contracts#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_collection_types_in_data_contracts/vb/program.vb#6)]  
  
 Na desserialização, se o tipo declarado é um tipo de coleção, o tipo declarado é instanciado, independentemente do tipo que foi enviado. Se o tipo declarado é uma interface de coleção, o desserializador escolhe um tipo a ser instanciado com nenhuma relação para tipos conhecidos.  
  
 Também na desserialização, se o tipo declarado não é um tipo de coleção, mas um tipo de coleção está sendo enviado, um tipo de coleção correspondente é escolhido fora da lista de tipos conhecidos. É possível adicionar tipos de interface de coleção para a lista de tipos conhecidos na desserialização. Nesse caso, o mecanismo de desserialização novamente escolhe um tipo a ser instanciado.  
  
## <a name="collections-and-the-netdatacontractserializer-class"></a>A classe NetDataContractSerializer e coleções  
 Quando o <xref:System.Runtime.Serialization.NetDataContractSerializer> classe está em uso, tipos de coleção não personalizada (sem o <xref:System.Runtime.Serialization.CollectionDataContractAttribute> atributo) que são matrizes não perca seu significado especial.  
  
 Tipos de coleção personalizados não marcado com o <xref:System.SerializableAttribute> ainda pode ser serializado com atributo pelo <xref:System.Runtime.Serialization.NetDataContractSerializer> classe de acordo com o <xref:System.SerializableAttribute> atributo ou o <xref:System.Runtime.Serialization.ISerializable> regras de interface.  
  
 Tipos de coleção personalizados, interfaces de coleção e matrizes ainda são tratados como coleções, mesmo quando o <xref:System.Runtime.Serialization.NetDataContractSerializer> classe está em uso.  
  
## <a name="collections-and-schema"></a>Coleções e esquema  
 Todas as coleções equivalentes possuem a mesma representação no esquema de linguagem XSD de definição de esquema XML. Por isso, você normalmente não obtém o mesmo tipo de coleção no código do cliente gerado como um no servidor. Por exemplo, o servidor pode usar um contrato de dados com um genérico <xref:System.Collections.Generic.List%601> de membro de dados inteiro, mas no código do cliente gerado do mesmo membro de dados pode se tornar uma matriz de inteiros.  
  
 Coleções do dicionário são marcadas com um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]-anotação de esquema específico que indicar que eles são dicionários; caso contrário, eles são indistinguíveis de listas simples que contém entradas com uma chave e um valor. Para obter uma descrição exata de como as coleções são representadas no esquema de contrato de dados, consulte [referência de esquema de contrato de dados](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md).  
  
 Por padrão, os tipos não são gerados para coleções não personalizada em código importado. Membros de dados de lista de tipos de coleção são importados como matrizes e membros de dados de dicionário de tipos de coleção são importados como um dicionário genérico.  
  
 No entanto, para coleções personalizadas, tipos separados são gerados, marcado com o <xref:System.Runtime.Serialization.CollectionDataContractAttribute> atributo. (Um tipo de coleção personalizada no esquema é aquele que não usa o namespace padrão, nome, repetição elemento nome ou chave/valor nomes de elemento.) Esses tipos são vazios tipos que derivam genérico <xref:System.Collections.Generic.List%601> para tipos de lista e um dicionário genérico para tipos de dicionário.  
  
 Por exemplo, você pode ter os seguintes tipos no servidor.  
  
 [!code-csharp[c_collection_types_in_data_contracts#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_collection_types_in_data_contracts/cs/program.cs#7)]
 [!code-vb[c_collection_types_in_data_contracts#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_collection_types_in_data_contracts/vb/program.vb#7)]  
  
 Quando o esquema é exportado e importados novamente, o código de cliente gerado é semelhante à seguinte (os campos são exibidos em vez de propriedades para facilitar a leitura).  
  
 [!code-csharp[c_collection_types_in_data_contracts#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_collection_types_in_data_contracts/cs/program.cs#8)]
 [!code-vb[c_collection_types_in_data_contracts#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_collection_types_in_data_contracts/vb/program.vb#8)]  
  
 Você talvez queira usar tipos diferentes no código gerado que as definições padrão. Por exemplo, você talvez queira usar genéricos <xref:System.ComponentModel.BindingList%601> em vez de matrizes regulares para os membros de dados facilitar a associá-las a componentes de interface do usuário.  
  
 Para escolher os tipos de coleção para gerar, passar uma lista de tipos de coleção que você deseja usar para o <xref:System.Runtime.Serialization.ImportOptions.ReferencedCollectionTypes%2A> propriedade o <xref:System.Runtime.Serialization.ImportOptions> ao importar o esquema do objeto. Esses tipos são chamados *referenciado tipos de coleção*.  
  
 Quando estão sendo referenciados tipos genéricos, eles devem ser genéricos totalmente aberto ou fechado totalmente genéricos.  
  
> [!NOTE]
>  Ao usar a ferramenta Svcutil.exe, essa referência pode ser feita usando o **/collectionType** opção de linha de comando (forma abreviada: **/ct**). Tenha em mente que você também deve especificar o assembly para os tipos de coleção referenciada usando o **/Reference** alternar (forma abreviada: **/r**). Se o tipo é genérico, ele deve ser seguido uma cotação voltar e o número de parâmetros genéricos. É a back aspas (') não deve ser confundido com o caractere de aspas simples ('). Você pode especificar vários tipos de coleção referenciada usando o **/collectionType** alternar mais de uma vez.  
  
 Por exemplo, para fazer com que todas as listas são importados como genérica <xref:System.Collections.Generic.List%601>.  
  
```  
svcutil.exe MyService.wsdl MyServiceSchema.xsd /r:C:\full_path_to_system_dll\System.dll /ct:System.Collections.Generic.List`1  
```  
  
 Ao importar qualquer coleção, esta lista de tipos de coleção referenciado é examinada e a coleção de melhor correspondência é usada se uma for encontrada, como um tipo de membro de dados (para coleções não personalizada) ou como um tipo base para derivar de (para coleções personalizadas). Dicionários só são comparados com dicionários, enquanto as listas são comparadas com listas.  
  
 Por exemplo, se você adicionar genérica <xref:System.ComponentModel.BindingList%601> e <xref:System.Collections.Hashtable> à lista de tipos referenciados, o código de cliente gerada para o exemplo anterior é semelhante à seguinte.  
  
 [!code-csharp[c_collection_types_in_data_contracts#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_collection_types_in_data_contracts/cs/program.cs#9)]
 [!code-vb[c_collection_types_in_data_contracts#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_collection_types_in_data_contracts/vb/program.vb#9)]  
  
 Você pode especificar os tipos de interface de coleção como parte de seus tipos de coleção referenciada, mas você não pode especificar os tipos de coleção inválido (como aqueles sem nenhum `Add` método ou construtor público).  
  
 Um genérico fechado é considerado a melhor correspondência. (Tipos genéricos não são considerados equivalentes aos genéricos fechados de `Object`). Por exemplo, se os tipos genéricos <xref:System.Collections.Generic.List%601> de <xref:System.DateTime>genérica <xref:System.ComponentModel.BindingList%601> (genérico aberto), e <xref:System.Collections.ArrayList> são os tipos de coleção referenciada, o seguinte é gerado.  
  
 [!code-csharp[c_collection_types_in_data_contracts#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_collection_types_in_data_contracts/cs/program.cs#10)]
 [!code-vb[c_collection_types_in_data_contracts#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_collection_types_in_data_contracts/vb/program.vb#10)]  
  
 Para coleções de lista, somente os casos na tabela a seguir têm suporte.  
  
|Tipo referenciado|Interface implementada pelo tipo referenciado|Exemplo|Tipo é tratado como:|  
|---------------------|----------------------------------------------|-------------|----------------------|  
|Não genérico ou fechado genérico (qualquer número de parâmetros)|Não genérico|`MyType : IList`<br /><br /> ou<br /><br /> `MyType<T> : IList`<br /><br /> onde T =`int`|Fechado genérico de `Object` (por exemplo, `IList<object>`)|  
|Não genérico ou fechado genérico (qualquer número de parâmetros que não necessariamente correspondem ao tipo de coleção)|Fechado genérico|`MyType : IList<string>`<br /><br /> ou<br /><br /> `MyType<T> : IList<string>`onde T =`int`|Genérico fechado (por exemplo, `IList<string>`)|  
|Fechado genérico com qualquer número de parâmetros|Abra genérico usando qualquer um dos parâmetros do tipo|`MyType<T,U,V> : IList<U>`<br /><br /> onde T =`int`, U =`string`, V =`bool`|Genérico fechado (por exemplo, `IList<string>`)|  
|Genérico aberto com um parâmetro|Genérico aberto usando o parâmetro do tipo|`MyType<T> : IList<T>`, T é aberto|Genérico aberto (por exemplo, `IList<T>`)|  
  
 Se um tipo implementa mais de uma interface de coleção da lista, as seguintes restrições se aplicam:  
  
-   Se o tipo implementa genérico <xref:System.Collections.Generic.IEnumerable%601> (ou suas interfaces derivadas) várias vezes para tipos diferentes, o tipo não é considerado um tipo de coleção referenciado válido e será ignorado. Isso é verdadeiro mesmo se algumas implementações são inválidas ou usam genéricos abertos. Por exemplo, um tipo que implementa genérico <xref:System.Collections.Generic.IEnumerable%601> de `int` e genérica <xref:System.Collections.Generic.IEnumerable%601> de T nunca serão usadas como uma coleção referenciada de `int` ou qualquer outro tipo, independentemente se o tipo tem um `Add` método aceitar `int` ou um `Add` método aceita um parâmetro de tipo T, ou ambos.  
  
-   Se o tipo implementa uma interface de coleção genérica, bem como <xref:System.Collections.IList>, o tipo nunca é usado como um tipo de coleção referenciada, a menos que a interface de coleção genérica é fechado genérico do tipo <xref:System.Object>.  
  
 Para coleções de dicionário, somente os casos na tabela a seguir têm suporte.  
  
|Tipo referenciado|Interface implementada pelo tipo referenciado|Exemplo|Tipo tratado como|  
|---------------------|----------------------------------------------|-------------|---------------------|  
|Não genérico ou fechado genérico (qualquer número de parâmetros)|<xref:System.Collections.IDictionary>|`MyType : IDictionary`<br /><br /> ou<br /><br /> `MyType<T> : IDictionary`onde T =`int`|Fechado genérico`IDictionary<object,object>`|  
|Genérico fechado (qualquer número de parâmetros)|<xref:System.Collections.Generic.IDictionary%602>, fechado|`MyType<T> : IDictionary<string, bool>`onde T =`int`|Genérico fechado (por exemplo, `IDIctionary<string,bool>`)|  
|Genérico fechado (qualquer número de parâmetros)|Genérica <xref:System.Collections.Generic.IDictionary%602>, chave ou valor é fechado, o outro está aberto e usa um dos parâmetros do tipo|`MyType<T,U,V> : IDictionary<string,V>`onde T =`int`, U =`float`, V =`bool`<br /><br /> ou<br /><br /> `MyType<Z> : IDictionary<Z,bool>`onde Z =`string`|Genérico fechado (por exemplo, `IDictionary<string,bool>`)|  
|Genérico fechado (qualquer número de parâmetros)|Genérica <xref:System.Collections.Generic.IDictionary%602>, chave e valor são abertos e cada uma usa um dos parâmetros do tipo|`MyType<T,U,V> : IDictionary<V,U>`onde T =`int`, U =`bool`, V =`string`|Genérico fechado (por exemplo, `IDictionary<string,bool>`)|  
|Abra genérico (dois parâmetros)|Genérica <xref:System.Collections.Generic.IDictionary%602>, abrir, que usa dois parâmetros genéricos do tipo na ordem em que aparecem|`MyType<K,V> : IDictionary<K,V>`, K e V abertos|Genérico aberto (por exemplo, `IDictionary<K,V>`)|  
  
 Se o tipo implementa ambos <xref:System.Collections.IDictionary> e genérica <xref:System.Collections.Generic.IDictionary%602>somente genérica <xref:System.Collections.Generic.IDictionary%602> é considerada.  
  
 Não há suporte para referenciar tipos genéricos parciais.  
  
 Não são permitidas duplicatas, por exemplo, você não pode adicionar os dois genérica <xref:System.Collections.Generic.List%601> de `Integer` e a coleção genérica de `Integer` para <xref:System.Runtime.Serialization.ImportOptions.ReferencedCollectionTypes%2A>, pois isso torna impossível determinar qual delas usar quando uma lista de inteiros foi encontrado no esquema. Duplicatas são detectadas somente se houver um tipo no esquema que expõe o problema de duplicatas. Por exemplo, se o esquema que está sendo importado não contém listas de números inteiros, ele é permitido ter ambos genérica <xref:System.Collections.Generic.List%601> de `Integer` e a coleção genérica de `Integer` no <xref:System.Runtime.Serialization.ImportOptions.ReferencedCollectionTypes%2A>, mas não tem nenhum efeito.  
  
## <a name="advanced-collection-rules"></a>Regras de coleta avançados  
  
### <a name="serializing-collections"></a>Serializando coleções  
 A seguir está uma lista de regras de coleção para a serialização:  
  
-   A combinação de tipos de coleção (com coleções de coleções) é permitida. Matrizes denteadas são tratados como coleções de coleções. Não há suporte para matrizes multidimensionais.  
  
-   Matrizes de bytes e matrizes de <xref:System.Xml.XmlNode> são tipos especiais de matriz são tratados como tipos primitivos, coleções não. Serialização de uma matriz de bytes de resultados em um único elemento XML que contém um bloco de dados codificados na Base64, em vez de um elemento separado para cada byte. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]como uma matriz de <xref:System.Xml.XmlNode> é tratado, consulte [XML e tipos de ADO.NET em contratos de dados](../../../../docs/framework/wcf/feature-details/xml-and-ado-net-types-in-data-contracts.md). Obviamente, esses tipos especiais próprios participem de coleções: uma matriz de conjunto de resultados de bytes em vários elementos XML, com cada um contendo uma parte dos dados codificados na Base64.  
  
-   Se o <xref:System.Runtime.Serialization.DataContractAttribute> atributo é aplicado a um tipo de coleção, o tipo é tratado como um tipo de contrato de dados regular, não como uma coleção.  
  
-   Se um tipo de coleção implementa o <xref:System.Xml.Serialization.IXmlSerializable> interface, as seguintes regras se aplicam, considerando um tipo `myType:IList<string>, IXmlSerializable`:  
  
    -   Se o tipo declarado é `IList<string>`, o tipo é serializado como uma lista.  
  
    -   Se o tipo declarado é `myType`, ele é serializado como `IXmlSerializable`.  
  
    -   Se o tipo declarado é `IXmlSerializable`, ele é serializado como `IXmlSerializable`, mas somente se você adicionar `myType` à lista de tipos conhecidos.  
  
-   Coleções são serializadas e desserializados usando os métodos mostrados na tabela a seguir.  
  
|Implementa o tipo de coleção|Método chamado em serialização|Chamada de método (s) na desserialização|  
|--------------------------------|-----------------------------------------|-------------------------------------------|  
|<xref:System.Collections.Generic.IDictionary%602>genérico|`get_Keys`, `get_Values`|Adicionar genérico|  
|<xref:System.Collections.IDictionary>|`get_Keys`, `get_Values`|`Add`|  
|<xref:System.Collections.Generic.IList%601>genérico|Genérica <xref:System.Collections.Generic.IList%601> indexador|Adicionar genérico|  
|<xref:System.Collections.Generic.ICollection%601>genérico|Enumerador|Adicionar genérico|  
|<xref:System.Collections.IList>|<xref:System.Collections.IList>Indexador|`Add`|  
|<xref:System.Collections.Generic.IEnumerable%601>genérico|`GetEnumerator`|Um método não estático chamado `Add` que recebe um parâmetro do tipo apropriado (o tipo do parâmetro genérico) ou um de seus tipos base. Esse método um deve existir para o serializador tratar um tipo de coleção como uma coleção durante a serialização e desserialização.|  
|<xref:System.Collections.IEnumerable>(e, portanto, <xref:System.Collections.ICollection>, que é derivado dele)|`GetEnumerator`|Um método não estático chamado `Add` que recebe um parâmetro do tipo `Object`. Esse método um deve existir para o serializador tratar um tipo de coleção como uma coleção durante a serialização e desserialização.|  
  
 A tabela anterior lista interfaces de coleção em ordem decrescente de precedência. Isso significa que, por exemplo, que se um tipo implementa ambos <xref:System.Collections.IList> e genérica <xref:System.Collections.Generic.IEnumerable%601>, a coleção é serializada e desserializada de acordo com o <xref:System.Collections.IList> regras:  
  
-   A desserialização, todas as coleções são desserializadas pelo primeiro criar uma instância do tipo chamando o construtor padrão, que deve estar presente para o serializador tratar um tipo de coleção como uma coleção durante a serialização e desserialização.  
  
-   Se a mesma interface de coleção genérica é implementada mais de uma vez (por exemplo, se um tipo implementa tanto do genérico <xref:System.Collections.Generic.ICollection%601> de `Integer` e genérica <xref:System.Collections.Generic.ICollection%601> de <xref:System.String>) e nenhuma interface de precedência mais alta for encontrado, a coleção é não é tratado como uma coleção válida.  
  
-   Tipos de coleção podem ter o <xref:System.SerializableAttribute> atributo aplicado a eles e pode implementar o <xref:System.Runtime.Serialization.ISerializable> interface. Ambos são ignorados. No entanto, se o tipo não totalmente atende aos requisitos de tipo de coleção (por exemplo, o `Add` método está ausente), o tipo não é considerado um tipo de coleção e, portanto, o <xref:System.SerializableAttribute> atributo e o <xref:System.Runtime.Serialization.ISerializable> interface são usados para determinar o tipo pode ser serializado.  
  
-   Aplicar o <xref:System.Runtime.Serialization.CollectionDataContractAttribute> atributo a uma coleção para personalizá-la remove o <xref:System.SerializableAttribute> precede o mecanismo de fallback. Em vez disso, se uma coleção personalizada coleção não atender aos requisitos de tipos, um <xref:System.Runtime.Serialization.InvalidDataContractException> exceção será lançada. A cadeia de caracteres de exceção geralmente contém informações que explicam por que um determinado tipo não é considerado uma coleção válida (nenhum `Add` método, nenhum construtor padrão e assim por diante), portanto, geralmente é útil aplicar o <xref:System.Runtime.Serialization.CollectionDataContractAttribute> atributo para fins de depuração.  
  
### <a name="collection-naming"></a>Coleção de nomenclatura  
 A seguir está uma lista das regras de nomenclatura de coleção:  
  
-   O namespace padrão para todos os contratos de dados de coleção de dicionário, bem como para contratos de dados de coleção de lista que contém os tipos primitivos, é http://schemas.microsoft.com/2003/10/Serialization/Arrays a menos que substituído usando o Namespace. Tipos que são mapeados para tipos XSD internos, bem como `char`, `Timespan`, e `Guid` tipos, são consideradas primitivos para essa finalidade.  
  
-   O namespace padrão para tipos de coleção que contém os tipos de não primitivo, a menos que ele seja substituído usando o Namespace, é o mesmo que o namespace de contrato de dados do tipo contido na coleção.  
  
-   O nome padrão para contratos de dados de coleção de lista, a menos que substituído usando o nome, é a cadeia de caracteres "ArrayOf" combinado com o nome de contrato de dados do tipo contido na coleção. Por exemplo, o nome de contrato de dados para uma lista de inteiros genérico é "ArrayOfint". Tenha em mente que o contrato de dados nome do `Object` é "anyType", portanto, como o nome de contrato de dados de listas não genérico <xref:System.Collections.ArrayList> é "ArrayOfanyType".  
  
 O nome padrão para dados de coleção de dicionário de contratos, a menos que substituído usando `Name`, é a cadeia de caracteres "ArrayOfKeyValueOf" combinado com o nome de contrato de dados do tipo de chave, seguido do nome de contrato de dados do tipo de valor. Por exemplo, os dados de nome de contrato para um dicionário de cadeia de caracteres genérica e inteiro é "ArrayOfKeyValueOfstringint". Além disso, se os tipos de valor ou a chave não são tipos primitivos, um hash de namespace dos namespaces de contrato de dados dos tipos de chave e o valor é anexado ao nome. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]hashes de namespace, consulte [nomes de contrato de dados](../../../../docs/framework/wcf/feature-details/data-contract-names.md).  
  
 Cada contrato de dados de coleção de dicionário tem um contrato de dados complementares que representa uma entrada no dicionário. Seu nome é o mesmo para o contrato de dados do dicionário, exceto para o prefixo "ArrayOf", e seu namespace é o mesmo contrato de dados de dicionário. Por exemplo, para o contrato de dados de dicionário "ArrayOfKeyValueOfstringint", o contrato de dados "KeyValueofstringint" representa uma entrada no dicionário. Você pode personalizar o nome do contrato de dados usando o `ItemName` propriedade, conforme descrito na próxima seção.  
  
 Regras de nomenclatura de tipo genérico conforme descrito em [nomes de contrato de dados](../../../../docs/framework/wcf/feature-details/data-contract-names.md), totalmente se aplicam a tipos de coleção; o que é, você pode usar as chaves no nome para indicar parâmetros de tipo genérico. No entanto, os números dentro dos colchetes consultem parâmetros genéricos e não os tipos contidos na coleção.  
  
## <a name="collection-customization"></a>Personalização de coleção  
 Os seguintes usos da <xref:System.Runtime.Serialization.CollectionDataContractAttribute> atributo são proibidos e resultar em um <xref:System.Runtime.Serialization.InvalidDataContractException> exceção:  
  
-   Aplicar o <xref:System.Runtime.Serialization.DataContractAttribute> de atributo para um tipo para o qual o <xref:System.Runtime.Serialization.CollectionDataContractAttribute> atributo foi aplicado, ou para um de seus tipos derivados.  
  
-   Aplicar o <xref:System.Runtime.Serialization.CollectionDataContractAttribute> de atributo para um tipo que implementa o <xref:System.Xml.Serialization.IXmlSerializable> interface.  
  
-   Aplicar o <xref:System.Runtime.Serialization.CollectionDataContractAttribute> de atributo para um tipo de coleção não.  
  
-   Tentativa de definir <xref:System.Runtime.Serialization.CollectionDataContractAttribute.KeyName%2A> ou <xref:System.Runtime.Serialization.CollectionDataContractAttribute.ValueName%2A> em um <xref:System.Runtime.Serialization.CollectionDataContractAttribute> atributo aplicado a um tipo de dicionário não.  
  
### <a name="polymorphism-rules"></a>Polimorfismo regras  
 Como mencionado anteriormente, personalizando coleções usando o <xref:System.Runtime.Serialization.CollectionDataContractAttribute> atributo pode interferir com obrigatórios da coleção. Dois tipos de coleção personalizados somente podem ser considerados equivalentes quando seu nome, namespace, nome do item, bem como nomes de chave e valor (se eles são coleções de dicionário) correspondem.  
  
 Devido a personalizações, é possível inadvertidamente use contrato de dados de uma coleção em que outra é esperada. Isso deve ser evitado. Consulte os seguintes tipos.  
  
 [!code-csharp[c_collection_types_in_data_contracts#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_collection_types_in_data_contracts/cs/program.cs#11)]
 [!code-vb[c_collection_types_in_data_contracts#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_collection_types_in_data_contracts/vb/program.vb#11)]  
  
 Nesse caso, uma instância do `Marks1` podem ser atribuídos a `testMarks`. No entanto, `Marks2` não deve ser usado porque seu contrato de dados não é equivalente a `IList<int>` contrato de dados. O nome de contrato de dados é "Marks2" e não "ArrayOfint" e o nome de elemento de repetição é "\<marcar >" e não "\<int >".  
  
 As regras na tabela a seguir se aplicam a atribuição polimórfica de coleções.  
  
|Tipo declarado|Atribuir uma coleção não personalizada|Atribuir uma coleção personalizada|  
|-------------------|--------------------------------------------|---------------------------------------|  
|Objeto|Nome do contrato é serializado.|Nome do contrato é serializado.<br /><br /> Personalização é usada.|  
|Interface de coleção|Nome do contrato não é serializado.|Nome do contrato não é serializado.<br /><br /> A personalização não é used.*|  
|Coleção não personalizada|Nome do contrato não é serializado.|Nome do contrato é serializado.<br /><br /> A personalização é used.* *|  
|Coleção personalizada|Nome do contrato é serializado. Não é de personalização used.* *|Nome do contrato é serializado.<br /><br /> Personalização do tipo atribuído é used.* *|  
  
 * Com o <xref:System.Runtime.Serialization.NetDataContractSerializer> classe, personalização é usada neste caso. O <xref:System.Runtime.Serialization.NetDataContractSerializer> classe serializa também o nome do tipo real nesse caso, portanto a desserialização funciona conforme o esperado.  
  
 * * Nesses casos resultam em instâncias de esquema inválida e, portanto, devem ser evitados.  
  
 Nos casos em que o nome do contrato é serializado, deve ser o tipo de coleção atribuída na lista de tipos conhecidos. O oposto também é verdadeiro: nos casos em que o nome não é serializado, adicionando o tipo à lista de tipos conhecidos não é necessária.  
  
 Uma matriz de um tipo derivado pode ser atribuída a uma matriz de um tipo base. Nesse caso, o nome do contrato para o tipo derivado é serializado para cada elemento de repetição. Por exemplo, se um tipo `Book` deriva do tipo `LibraryItem`, você pode atribuir uma matriz de `Book` para uma matriz de `LibraryItem`. Isso não se aplica a outros tipos de coleção. Por exemplo, você não pode atribuir um `Generic List of Book` para um `Generic List of LibraryItem`. No entanto, você pode atribuir um `Generic List of LibraryItem` que contém `Book` instâncias. A matriz e o caso não sejam de matriz, `Book` devem estar na lista de tipos conhecidos.  
  
## <a name="collections-and-object-reference-preservation"></a>Coleções e preservação de referência de objeto  
 Quando funções um serializador em um modo em que preserva as referências de objeto, preservação de referência de objeto também se aplica às coleções. Especificamente, a identidade do objeto é preservada para coleções inteiras e contidos em coleções de itens individuais. Para dicionários, a identidade do objeto é preservada para os objetos de par chave/valor e os objetos individuais de chave e valor.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Runtime.Serialization.CollectionDataContractAttribute>
