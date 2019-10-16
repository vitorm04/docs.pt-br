---
title: 'Práticas recomendadas: controle de versão de contrato de dados'
ms.date: 03/30/2017
helpviewer_keywords:
- data contracts
- service contracts
- best practices [WCF], data contract versioning
- Windows Communication Foundation, data contracts
ms.assetid: bf0ab338-4d36-4e12-8002-8ebfdeb346cb
ms.openlocfilehash: 4d500c37efa4a90e24b06cd2e886147e1f159d4e
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320788"
---
# <a name="best-practices-data-contract-versioning"></a>Práticas recomendadas: controle de versão de contrato de dados
Este tópico lista as práticas recomendadas para a criação de contratos de dados que podem evoluir facilmente ao longo do tempo. Para obter mais informações sobre contratos de dados, consulte os tópicos em [usando contratos de dados](./feature-details/using-data-contracts.md).  
  
## <a name="note-on-schema-validation"></a>Observação sobre a validação de esquema  
 Ao discutir o controle de versão de contrato de dados, é importante observar que o esquema de contrato de dados exportado pelo Windows Communication Foundation (WCF) não tem nenhum suporte de controle de versão, além do fato de que os elementos são marcados como opcionais por padrão.  
  
 Isso significa que até mesmo o cenário de controle de versão mais comum, como adicionar um novo membro de dados, não pode ser implementado de forma direta em relação a um determinado esquema. As versões mais recentes de um contrato de dados (com um novo membro de dados, por exemplo) não são validadas usando o esquema antigo.  
  
 No entanto, há muitos cenários em que a conformidade de esquema estrita não é necessária. Muitas plataformas de serviços da Web, incluindo WCF e serviços Web XML criados usando ASP.NET, não executam a validação de esquema por padrão e, portanto, toleram elementos extras que não são descritos pelo esquema. Ao trabalhar com essas plataformas, muitos cenários de controle de versão são mais fáceis de implementar.  
  
 Assim, há dois conjuntos de diretrizes de controle de versão de contrato de dados: um conjunto para cenários em que a validade de esquema estrita é importante e outro conjunto para cenários quando não está.  
  
## <a name="versioning-when-schema-validation-is-required"></a>Controle de versão quando a validação de esquema é necessária  
 Se a validade estrita do esquema for necessária em todas as direções (nova-para-antigo e antiga para a nova), os contratos de dados deverão ser considerados imutáveis. Se o controle de versão for necessário, um novo contrato de dados deverá ser criado, com um nome ou namespace diferente, e o contrato de serviço que usa o tipo de dados deve ter a versão do respectivo controle.  
  
 Por exemplo, um contrato de serviço de processamento de ordem de compra chamado `PoProcessing` com uma operação `PostPurchaseOrder` usa um parâmetro que está em conformidade com um contrato de dados `PurchaseOrder`. Se o contrato `PurchaseOrder` precisar ser alterado, você deverá criar um novo contrato de dados, ou seja, `PurchaseOrder2`, que inclui as alterações. Em seguida, você deve manipular o controle de versão no nível do contrato de serviço. Por exemplo, criando uma operação `PostPurchaseOrder2` que usa o parâmetro `PurchaseOrder2` ou criando um contrato de serviço `PoProcessing2` em que a operação `PostPurchaseOrder` usa um contrato de dados `PurchaseOrder2`.  
  
 Observe que as alterações em contratos de dados que são referenciadas por outros contratos de dados também se estendem para a camada de modelo de serviço. Por exemplo, no cenário anterior, o contrato de dados `PurchaseOrder` não precisa ser alterado. No entanto, ele contém um membro de dados de um contrato de dados `Customer` que, por sua vez, continha um membro de dados do contrato de dados `Address`, que precisa ser alterado. Nesse caso, você precisaria criar um contrato de dados `Address2` com as alterações necessárias, um contrato de dados `Customer2` que contenha o membro de dados `Address2` e um contrato de dados `PurchaseOrder2` que contenha um membro de dados `Customer2`. Como no caso anterior, o contrato de serviço teria de ter a versão também.  
  
 Embora esses nomes de exemplos sejam alterados (acrescentando um "2"), a recomendação é alterar namespaces em vez de nomes acrescentando novos namespaces com um número de versão ou uma data. Por exemplo, o contrato de dados `http://schemas.contoso.com/2005/05/21/PurchaseOrder` mudaria para o contrato de dados `http://schemas.contoso.com/2005/10/14/PurchaseOrder`.  
  
 Para obter mais informações, consulte práticas recomendadas: [controle de versão de serviço](service-versioning.md).  
  
 Ocasionalmente, você deve garantir a conformidade de esquema estrita para mensagens enviadas pelo seu aplicativo, mas não pode contar com as mensagens de entrada para serem estritamente compatíveis com o esquema. Nesse caso, há um perigo de que uma mensagem de entrada possa conter dados estranhos. Os valores estranhos são armazenados e retornados pelo WCF e, portanto, resultam no esquema-mensagens inválidas sendo enviadas. Para evitar esse problema, o recurso de ida e volta deve ser desativado. Há duas formas de fazer isso.  
  
- Não implemente a interface <xref:System.Runtime.Serialization.IExtensibleDataObject> em nenhum dos seus tipos.  
  
- Aplique um atributo <xref:System.ServiceModel.ServiceBehaviorAttribute> ao seu contrato de serviço com a propriedade <xref:System.ServiceModel.ServiceBehaviorAttribute.IgnoreExtensionDataObject%2A> definida como `true`.  
  
 Para obter mais informações sobre ida e volta, consulte [contratos de dados compatíveis com o encaminhamento](./feature-details/forward-compatible-data-contracts.md).  
  
## <a name="versioning-when-schema-validation-is-not-required"></a>Controle de versão quando a validação de esquema não é necessária  
 A conformidade de esquema estrita raramente é necessária. Muitas plataformas toleram elementos adicionais não descritos por um esquema. Desde que isso seja tolerado, o conjunto completo de recursos descritos em [controle de versão de contrato de dados](./feature-details/data-contract-versioning.md) e [contratos de dados compatíveis com encaminhamento](./feature-details/forward-compatible-data-contracts.md) pode ser usado. As diretrizes a seguir são recomendadas.  
  
 Algumas das diretrizes devem ser seguidas exatamente para enviar novas versões de um tipo em que uma antiga é esperada ou enviar uma antiga em que a nova é esperada. Outras diretrizes não são estritamente necessárias, mas são listadas aqui porque podem ser afetadas pelo futuro do controle de versão do esquema.  
  
1. Não tente a versão de contratos de dados por herança de tipo. Para criar versões posteriores, altere o contrato de dados em um tipo existente ou crie um novo tipo não relacionado.  
  
2. O uso de herança junto com contratos de dados é permitido, desde que a herança não seja usada como um mecanismo de controle de versão e que determinadas regras sejam seguidas. Se um tipo derivar de um determinado tipo base, não o tornará derivado de um tipo base diferente em uma versão futura (a menos que ele tenha o mesmo contrato de dados). Há uma exceção a isso: você pode inserir um tipo na hierarquia entre um tipo de contrato de dados e seu tipo base, mas somente se ele não contiver membros de dados com os mesmos nomes de outros membros em qualquer uma das versões possíveis dos outros tipos na hierarquia. Em geral, o uso de membros de dados com os mesmos nomes em diferentes níveis da mesma hierarquia de herança pode levar a problemas sérios de controle de versão e deve ser evitado.  
  
3. A partir da primeira versão de um contrato de dados, sempre implemente <xref:System.Runtime.Serialization.IExtensibleDataObject> para habilitar o ida e volta. Para obter mais informações, consulte [Contratos de dados compatíveis por encaminhamento](./feature-details/forward-compatible-data-contracts.md). Se você lançou uma ou mais versões de um tipo sem implementar essa interface, implemente-a na próxima versão do tipo.  
  
4. Em versões posteriores, não altere o namespace ou o nome do contrato de dados. Se estiver alterando o nome ou o namespace do tipo subjacente ao contrato de dados, lembre-se de preservar o nome do contrato de dados e o namespace usando os mecanismos apropriados, como a propriedade <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A> do <xref:System.Runtime.Serialization.DataContractAttribute>. Para obter mais informações sobre Nomenclatura, consulte [nomes de contrato de dados](./feature-details/data-contract-names.md).  
  
5. Em versões posteriores, não altere os nomes de quaisquer membros de dados. Se alterar o nome do campo, da propriedade ou do evento subjacente ao membro de dados, use a propriedade `Name` do <xref:System.Runtime.Serialization.DataMemberAttribute> para preservar o nome do membro de dados existente.  
  
6. Em versões posteriores, não altere o tipo de qualquer campo, propriedade ou evento subjacente a um membro de dados, de modo que o contrato de dados resultante para esse membro de dados seja alterado. Tenha em mente que os tipos de interface são equivalentes a <xref:System.Object> para fins de determinação do contrato de dados esperado.  
  
7. Em versões posteriores, não altere a ordem dos membros de dados existentes ajustando a propriedade <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> do atributo <xref:System.Runtime.Serialization.DataMemberAttribute>.  
  
8. Em versões posteriores, novos membros de dados podem ser adicionados. Eles sempre devem seguir estas regras:  
  
    1. A propriedade <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> sempre deve ser deixada com seu valor padrão de `false`.  
  
    2. Se um valor padrão de `null` ou zero para o membro for inaceitável, um método de retorno de chamada deverá ser fornecido usando o <xref:System.Runtime.Serialization.OnDeserializingAttribute> para fornecer um padrão razoável caso o membro não esteja presente no fluxo de entrada. Para obter mais informações sobre o retorno de chamada, consulte [retornos de chamada de serialização tolerantes à versão](./feature-details/version-tolerant-serialization-callbacks.md).  
  
    3. A propriedade <xref:System.Runtime.Serialization.DataMemberAttribute.Order?displayProperty=nameWithType> deve ser usada para garantir que todos os membros de dados adicionados recentemente apareçam após os membros de dados existentes. A maneira recomendada de fazer isso é a seguinte: nenhum dos membros de dados na primeira versão do contrato de dados deve ter sua propriedade `Order` definida. Todos os membros de dados adicionados na versão 2 do contrato de dados devem ter sua propriedade `Order` definida como 2. Todos os membros de dados adicionados na versão 3 do contrato de dados devem ter seu `Order` definido como 3 e assim por diante. É permitido ter mais de um membro de dados definido com o mesmo número `Order`.  
  
9. Não remova os membros de dados em versões posteriores, mesmo que a propriedade <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> tenha sido deixada em sua propriedade padrão de `false` em versões anteriores.  
  
10. Não altere a propriedade `IsRequired` em todos os membros de dados existentes da versão para a versão.  
  
11. Para os membros de dados necessários (em que `IsRequired` é `true`), não altere a propriedade `EmitDefaultValue` de versão para versão.  
  
12. Não tente criar hierarquias de controle de versão ramificadas. Ou seja, sempre deve haver um caminho em pelo menos uma direção de qualquer versão para qualquer outra versão usando apenas as alterações permitidas por essas diretrizes.  
  
     Por exemplo, se a versão 1 de um contrato de dados de pessoa contiver apenas o nome membro de dados, você não deverá criar a versão 2A do contrato adicionando somente o membro age e a versão 2B adicionando apenas o membro de endereço. Ir de 2a para 2B envolverá a remoção da idade e a adição de endereço; entrar na outra direção envolveria a remoção de endereço e a adição de idade. A remoção de membros não é permitida por essas diretrizes.  
  
13. Em geral, você não deve criar novos subtipos de tipos de contrato de dados existentes em uma nova versão do seu aplicativo. Da mesma forma, você não deve criar novos contratos de dados que são usados no lugar de membros de dados declarados como objetos ou como tipos de interface. A criação dessas novas classes é permitida somente quando você sabe que pode adicionar os novos tipos à lista de tipos conhecidos de todas as instâncias do aplicativo antigo. Por exemplo, na versão 1 do seu aplicativo, você pode ter o tipo de contrato de dados LibraryItem com o livro e subtipos de contrato de dados de jornal. O LibraryItem teria uma lista de tipos conhecidos que contém livros e jornal. Suponha que agora você adicione um tipo de revista na versão 2, que é um subtipo de LibraryItem. Se você enviar uma instância da revista da versão 2 para a versão 1, o contrato de dados da revista não será encontrado na lista de tipos conhecidos e uma exceção será gerada.  
  
14. Você não deve adicionar ou remover membros de enumeração entre versões. Você também não deve renomear membros de enumeração, a menos que use a propriedade Name no atributo `EnumMemberAttribute` para manter seus nomes no modelo de contrato de dados o mesmo.  
  
15. As coleções são intercambiáveis no modelo de contrato de dados, conforme descrito em [tipos de coleção em contratos de dados](./feature-details/collection-types-in-data-contracts.md). Isso permite um grande grau de flexibilidade. No entanto, certifique-se de que você não altere inadvertidamente um tipo de coleção de uma forma não intercambiável de versão para versão. Por exemplo, não altere de uma coleção não personalizada (ou seja, sem o atributo `CollectionDataContractAttribute`) para uma coleção personalizada ou personalizada para um não personalizado. Além disso, não altere as propriedades no `CollectionDataContractAttribute` da versão para a versão. A única alteração permitida é adicionar um nome ou uma propriedade de namespace se o nome ou o namespace do tipo de coleção subjacente tiver sido alterado e você precisar tornar seu nome de contrato de dados e namespace o mesmo que em uma versão anterior.  
  
 Algumas das diretrizes listadas aqui podem ser ignoradas com segurança quando se aplicam circunstâncias especiais. Certifique-se de compreender totalmente os mecanismos de serialização, desserialização e esquema envolvidos antes de deviating das diretrizes.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A>
- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A>
- <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A>
- <xref:System.Runtime.Serialization.IExtensibleDataObject>
- <xref:System.ServiceModel.ServiceBehaviorAttribute>
- <xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A>
- <xref:System.Runtime.Serialization.ExtensionDataObject>
- <xref:System.Runtime.Serialization.OnDeserializingAttribute>
- [Usando contratos de dados](./feature-details/using-data-contracts.md)
- [Controle de versão de contrato de dados](./feature-details/data-contract-versioning.md)
- [Nomes de contrato de dados](./feature-details/data-contract-names.md)
- [Contratos de dados compatíveis com encaminhamento](./feature-details/forward-compatible-data-contracts.md)
- [Retornos de chamada de serialização tolerantes à versão](./feature-details/version-tolerant-serialization-callbacks.md)
