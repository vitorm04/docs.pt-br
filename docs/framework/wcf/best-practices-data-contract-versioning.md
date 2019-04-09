---
title: 'Melhores práticas: Controle de versão de contrato de dados'
ms.date: 03/30/2017
helpviewer_keywords:
- data contracts
- service contracts
- best practices [WCF], data contract versioning
- Windows Communication Foundation, data contracts
ms.assetid: bf0ab338-4d36-4e12-8002-8ebfdeb346cb
ms.openlocfilehash: 9f92e731132eb564b893e3d34ccd322fbcd66ea7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59118996"
---
# <a name="best-practices-data-contract-versioning"></a>Melhores práticas: Controle de versão de contrato de dados
Este tópico lista as práticas recomendadas para a criação de contratos de dados que podem evoluir facilmente ao longo do tempo. Para obter mais informações sobre contratos de dados, consulte os tópicos [contratos de dados usando](../../../docs/framework/wcf/feature-details/using-data-contracts.md).  
  
## <a name="note-on-schema-validation"></a>Observação sobre validação de esquema  
 Ao discutir o controle de versão de contrato de dados, é importante observar que o esquema de contrato de dados exportado pelo Windows Communication Foundation (WCF) não tem nenhum suporte de controle de versão, além do fato de que os elementos são marcados como opcionais por padrão.  
  
 Isso significa que até mesmo o cenário controle de versão mais comuns, como adicionar um novo membro de dados, não pode ser implementado de forma coesa em relação a um determinado esquema. As versões mais recentes de um contrato de dados (com um novo membro de dados, por exemplo) não validam usando o esquema antigo.  
  
 No entanto, há muitos cenários em que a conformidade de esquema estrita não é necessária. Muitas plataformas de serviços da Web, incluindo o WCF e serviços Web XML criados usando ASP.NET, não realize a validação de esquema padrão e tolerar, portanto, os elementos adicionais que não são descritos no esquema. Ao trabalhar com essas plataformas, muitos cenários de controle de versão são mais fáceis de implementar.  
  
 Portanto, há diretrizes de controle de versão de contrato de dois conjuntos de dados: um conjunto para cenários onde validade de esquema estrita é importante, e outro conjunto para cenários quando não for.  
  
## <a name="versioning-when-schema-validation-is-required"></a>Controle de versão quando a validação de esquema é necessária  
 Se a validade de esquema estrita é necessária em todas as direções (antigo novo e antigo em nova), contratos de dados devem ser considerados imutáveis. Se for necessário o controle de versão, um novo contrato de dados deve ser criado, com um nome diferente ou namespace, e o contrato de serviço usando o tipo de dados deve ter uma versão adequadamente.  
  
 Por exemplo, uma ordem de compra contrato de serviço chamado de processamento `PoProcessing` com um `PostPurchaseOrder` operação leva um parâmetro que está em conformidade com um `PurchaseOrder` contrato de dados. Se o `PurchaseOrder` contrato deve ser alterado, você deve criar um novo contrato de dados, ou seja, `PurchaseOrder2`, que inclui as alterações. Em seguida, você deverá manipular o controle de versão no nível do contrato de serviço. Por exemplo, ao criar uma `PostPurchaseOrder2` operação leva a `PurchaseOrder2` parâmetro, ou criando um `PoProcessing2` contrato de serviço onde o `PostPurchaseOrder` operação leva um `PurchaseOrder2` contrato de dados.  
  
 Observe que as alterações em contratos de dados que são referenciados por outros contratos de dados também estendem para a camada de modelo de serviço. Por exemplo, no cenário anterior a `PurchaseOrder` contrato de dados não precisa alterar. No entanto, ele contém um membro de dados de um `Customer` contrato de dados, que por sua vez, continha um membro de dados do `Address` contrato de dados, que precisam ser alteradas. Nesse caso, você precisaria criar uma `Address2` contrato de dados com as alterações necessárias, uma `Customer2` contrato de dados que contém o `Address2` membro de dados e uma `PurchaseOrder2` contrato de dados que contém um `Customer2` membro de dados. Como no caso anterior, o contrato de serviço tem que ter controle de versão também.  
  
 Embora esses exemplos nomes são alterados (por meio do acréscimo "2"), a recomendação é alterar os namespaces em vez de nomes por meio do acréscimo novos namespaces com um número de versão ou uma data. Por exemplo, o `http://schemas.contoso.com/2005/05/21/PurchaseOrder` contrato de dados seria alteradas para o `http://schemas.contoso.com/2005/10/14/PurchaseOrder` contrato de dados.  
  
 Para obter mais informações, consulte as práticas recomendadas: [Controle de versão de serviço](../../../docs/framework/wcf/service-versioning.md).  
  
 Ocasionalmente, você deve garantir conformidade de esquema estrita para mensagens enviadas pelo seu aplicativo, mas não pode contar com as mensagens de entrada seja estritamente compatíveis com o esquema. Nesse caso, há um risco de que uma mensagem de entrada pode conter dados estranhos. Os valores desconhecidos são armazenados e retornados pelo WCF e, portanto, resulta em esquema inválido mensagens sendo enviadas. Para evitar esse problema, o recurso de ciclo completo deve ser desativado. Há duas formas de fazer isso.  
  
-   Não implementam a <xref:System.Runtime.Serialization.IExtensibleDataObject> interface em qualquer um dos seus tipos.  
  
-   Aplicar uma <xref:System.ServiceModel.ServiceBehaviorAttribute> de atributo ao seu contrato de serviço com o <xref:System.ServiceModel.ServiceBehaviorAttribute.IgnoreExtensionDataObject%2A> propriedade definida como `true`.  
  
 Para obter mais informações sobre o ciclo completo, consulte [contratos de dados compatíveis por encaminhamento](../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md).  
  
## <a name="versioning-when-schema-validation-is-not-required"></a>Controle de versão quando a validação de esquema não é necessária  
 Conformidade de esquema estrita é raramente necessária. Muitas plataformas toleram elementos adicionais não descritos por um esquema. Isso é tolerado, desde que o conjunto completo de recursos descrito em [controle de versão de contrato de dados](../../../docs/framework/wcf/feature-details/data-contract-versioning.md) e [contratos de dados compatíveis por encaminhamento](../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md) pode ser usado. As diretrizes a seguir são recomendadas.  
  
 Algumas das diretrizes devem ser seguidas exatamente a fim de enviar novas versões de um tipo de onde se espera que mais antiga ou enviar uma antiga onde se espera que um novo. Outras diretrizes não são estritamente necessárias, mas são listadas aqui porque eles podem ser afetados pelo futuro do controle de versão do esquema.  
  
1.  Não tente contratos de dados de versão por herança de tipo. Para criar versões posteriores, altere o contrato de dados em um tipo existente ou criar um novo tipo de não relacionado.  
  
2.  O uso de herança junto com os contratos de dados é permitido, desde que a herança não é usada como um mecanismo de controle de versão e certas regras sejam seguidas. Se um tipo derivado de um determinado tipo de base, não o tornará derivar de um tipo base diferente em uma versão futura (a menos que ele tenha os mesmos dados contrato). Há uma exceção a isso: você pode inserir um tipo na hierarquia entre um tipo de contrato de dados e seu tipo base, mas somente se ele não contém membros de dados com os mesmos nomes que outros membros em todas as versões possíveis de outros tipos na hierarquia. Em geral, usando membros de dados com os mesmos nomes em diferentes níveis da mesma hierarquia de herança pode causar problemas graves de controle de versão e deve ser evitada.  
  
3.  Começando com a primeira versão de um contrato de dados, sempre implementar <xref:System.Runtime.Serialization.IExtensibleDataObject> para habilitar o ciclo completo. Para obter mais informações, consulte [Contratos de dados compatíveis por encaminhamento](../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md). Se você tiver lançado uma ou mais versões de um tipo sem implementar essa interface, você deve implementá-la na próxima versão do tipo.  
  
4.  Em versões posteriores, não altere o nome do contrato de dados ou um namespace. Se alterar o nome ou namespace do tipo subjacente de contrato de dados, certifique-se preservar o namespace e nome do contrato de dados usando os mecanismos apropriados, como o <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A> propriedade do <xref:System.Runtime.Serialization.DataContractAttribute>. Para obter mais informações sobre como nomear, consulte [nomes de contrato de dados](../../../docs/framework/wcf/feature-details/data-contract-names.md).  
  
5.  Em versões posteriores, não altere os nomes de todos os membros de dados. Se alterar o nome do campo, propriedade ou evento subjacente o membro de dados, use o `Name` propriedade do <xref:System.Runtime.Serialization.DataMemberAttribute> para preservar o nome de membro de dados existente.  
  
6.  Em versões posteriores, não altere o tipo de qualquer campo, propriedade ou evento subjacente a um membro de dados, de modo que os dados resultantes de contrato que alterações de dados membro. Tenha em mente que tipos de interface são equivalentes a <xref:System.Object> a fim de determinar o contrato de dados esperado.  
  
7.  Em versões posteriores, não altere a ordem dos membros de dados existente, ajustando a <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> propriedade do <xref:System.Runtime.Serialization.DataMemberAttribute> atributo.  
  
8.  Em versões posteriores, é possível adicionar novos membros de dados. Eles sempre devem seguir estas regras:  
  
    1.  O <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> propriedade sempre deve ser deixada com seu valor padrão de `false`.  
  
    2.  Se o valor padrão de `null` ou zero para o membro for inaceitável, um método de retorno de chamada deve ser fornecido usando o <xref:System.Runtime.Serialization.OnDeserializingAttribute> para fornecer uma opção razoável, caso o membro não está presente no fluxo de entrada. Para obter mais informações sobre o retorno de chamada, consulte [retornos de chamada de serialização tolerantes à versão](../../../docs/framework/wcf/feature-details/version-tolerant-serialization-callbacks.md).  
  
    3.  O <xref:System.Runtime.Serialization.DataMemberAttribute.Order?displayProperty=nameWithType> propriedade deve ser usada para certificar-se de que todos os membros de dados recém-adicionados aparecem após os membros de dados existente. A maneira recomendada de fazer isso é da seguinte maneira: Nenhum dos membros de dados na primeira versão do contrato de dados deve ter suas `Order` conjunto de propriedades. Todos os membros de dados adicionados na versão 2 do contrato de dados devem ter suas `Order` propriedade definida como 2. Todos os membros de dados adicionados na versão 3 do contrato de dados devem ter suas `Order` definido como 3 e assim por diante. É permitido ter mais de um membro de dados definido para a mesma `Order` número.  
  
9. Não remova os membros de dados em versões posteriores, mesmo se o <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> propriedade foi deixada com sua propriedade default de `false` em versões anteriores.  
  
10. Não altere o `IsRequired` propriedade em quaisquer membros de dados existente de versão para versão.  
  
11. Para membros de dados necessários (onde `IsRequired` está `true`), não altere o `EmitDefaultValue` propriedade de versão para versão.  
  
12. Não tente criar hierarquias de controle de versão ramificado. Ou seja, deve sempre haver um caminho em pelo menos uma direção de qualquer versão para qualquer outra versão usando apenas as alterações permitidas por essas diretrizes.  
  
     Por exemplo, se a versão 1 de um contrato de dados de pessoa contém apenas o membro de dados de nome, você não deve criar 2a de versão do contrato adicionando somente a idade membro e a versão 2b adicionando apenas o membro de endereço. Vai de 2a e 2b envolveria removendo idade e adicionando endereço; indo na outra direção envolveria a remoção de endereço e a idade de adição. Removendo membros não é permitido por essas diretrizes.  
  
13. Você geralmente não deve criar novos subtipos dos tipos de contrato de dados existente em uma nova versão do seu aplicativo. Da mesma forma, você não deve criar novos contratos de dados que são usados no lugar de dados membros declarados como objeto ou como tipos de interface. Criação destas novas classes é permitida somente quando souber que você pode adicionar os novos tipos à lista de tipos conhecidos de todas as instâncias do seu aplicativo antigo. Por exemplo, na versão 1 do seu aplicativo, você pode ter o tipo com o catálogo de contrato de dados de LibraryItem e os dados de jornal subtipos de contrato. LibraryItem teria uma lista de tipos conhecidos que contém o catálogo e os jornais. Suponha que agora você adicionar um tipo de revista na versão 2, que é um subtipo de LibraryItem. Se você enviar uma instância de revista da versão 2 para a versão 1, o contrato de dados da revista não for encontrado na lista de tipos conhecidos e uma exceção é lançada.  
  
14. Você não deve adicionar ou remover membros de enumeração entre versões. Você também não deve renomear os membros de enumeração, a menos que você use a propriedade de nome no `EnumMemberAttribute` atributo para manter seus nomes no modelo de contrato de dados o mesmo.  
  
15. Coleções são intercambiáveis no modelo de contrato de dados, conforme descrito em [tipos de coleção em contratos de dados](../../../docs/framework/wcf/feature-details/collection-types-in-data-contracts.md). Isso permite um alto grau de flexibilidade. No entanto, certifique-se de que você altere inadvertidamente um tipo de coleção em uma não-intercambiáveis propósito de versão para versão. Por exemplo, não são alterados de uma coleção não personalizado (ou seja, sem o `CollectionDataContractAttribute` atributo) a um personalizado ou um conjunto personalizado para um não personalizado. Além disso, não altere as propriedades no `CollectionDataContractAttribute` de versão para versão. A única alteração permitida é adicionar uma propriedade de nome ou Namespace se o namespace ou nome do tipo de coleção subjacente foi alterado e você precisa fazer seus dados de nome e namespace de contrato igual uma versão anterior.  
  
 Algumas das diretrizes listadas aqui podem ser ignoradas com segurança quando circunstâncias especiais se aplicam. Certifique-se de que entender completamente a serialização, desserialização e mecanismos de esquema envolverem antes desviam-se das diretrizes.  
  
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
- [Usando contratos de dados](../../../docs/framework/wcf/feature-details/using-data-contracts.md)
- [Controle de versão de contrato de dados](../../../docs/framework/wcf/feature-details/data-contract-versioning.md)
- [Nomes de contrato de dados](../../../docs/framework/wcf/feature-details/data-contract-names.md)
- [Contratos de dados compatíveis por encaminhamento](../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md)
- [Retornos de chamada de serialização tolerantes à versão](../../../docs/framework/wcf/feature-details/version-tolerant-serialization-callbacks.md)
