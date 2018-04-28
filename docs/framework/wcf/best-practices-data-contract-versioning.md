---
title: 'Práticas recomendadas: controle de versão de contrato de dados'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- data contracts
- service contracts
- best practices [WCF], data contract versioning
- Windows Communication Foundation, data contracts
ms.assetid: bf0ab338-4d36-4e12-8002-8ebfdeb346cb
caps.latest.revision: 24
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: dfb3d781a570db6a929a7d984aa45c224dda66bd
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2018
---
# <a name="best-practices-data-contract-versioning"></a>Práticas recomendadas: controle de versão de contrato de dados
Este tópico lista as práticas recomendadas para a criação de contratos de dados que podem evoluir facilmente ao longo do tempo. [!INCLUDE[crabout](../../../includes/crabout-md.md)] contratos de dados, consulte os tópicos [usando contratos de dados](../../../docs/framework/wcf/feature-details/using-data-contracts.md).  
  
## <a name="note-on-schema-validation"></a>Observação sobre a validação de esquema  
 Discutir sobre o controle de versão de contrato de dados, é importante observar que o contrato de dados esquema exportada por [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] não tem nenhum suporte de controle de versão, que não seja o fato de que os elementos são marcados como opcionais por padrão.  
  
 Isso significa que até mesmo o cenário controle de versão mais comuns, como adicionar um novo membro de dados, não pode ser implementado de maneira que seja consistente em relação a um determinado esquema. As versões mais recentes de um contrato de dados (com um novo membro de dados, por exemplo) não validam usando o esquema antigo.  
  
 No entanto, há muitos cenários em que a compatibilidade de esquema estrita não é necessária. Serviços de Web muitas plataformas, incluindo [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] e XML Web services criados usando ASP.NET, não executar a validação de esquema por padrão e, portanto, tolerar elementos adicionais que não são descritos no esquema. Ao trabalhar com essas plataformas, muitos cenários de controle de versão são mais fáceis de implementar.  
  
 Assim, há diretrizes de controle de versão de contrato de dois conjuntos de dados: um conjunto para cenários em que a validade de esquema estrita é importante e outro conjunto para cenários quando não for.  
  
## <a name="versioning-when-schema-validation-is-required"></a>Controle de versão quando a validação de esquema é necessária  
 Se a validade de esquema estrita é necessário em todas as direções (antigo novo e antigo em nova), os contratos de dados devem ser considerados imutáveis. Se o controle de versão é necessária, deve ser criado um novo contrato de dados com um nome diferente ou namespace, e o contrato de serviço usando o tipo de dados deve ser versão adequadamente.  
  
 Por exemplo, uma ordem de compra processamento contrato de serviço denominado `PoProcessing` com um `PostPurchaseOrder` operação usa um parâmetro que está de acordo com uma `PurchaseOrder` contrato de dados. Se o `PurchaseOrder` contrato deve ser alterado, você deve criar um novo contrato de dados, ou seja, `PurchaseOrder2`, que inclui as alterações. Em seguida, você deve tratar o controle de versão no nível de contrato de serviço. Por exemplo, criando uma `PostPurchaseOrder2` operação que utiliza o `PurchaseOrder2` parâmetro, ou criando uma `PoProcessing2` contrato de serviço onde o `PostPurchaseOrder` operação leva um `PurchaseOrder2` contrato de dados.  
  
 Observe que as alterações em contratos de dados que são referenciados por outros contratos de dados também estendem a camada de modelo de serviço. Por exemplo, no cenário anterior a `PurchaseOrder` contrato de dados não precisa alterar. No entanto, ele contém um membro de dados de um `Customer` contrato de dados, que por sua vez continha um membro de dados do `Address` contrato de dados, que precisam ser alteradas. Nesse caso, você precisaria criar um `Address2` contrato de dados com as alterações necessárias, um `Customer2` contrato de dados que contém o `Address2` membro de dados e um `PurchaseOrder2` contrato de dados que contém um `Customer2` membro de dados. Como no caso anterior, o contrato de serviço precisa ser bem com controle de versão.  
  
 Embora esses exemplos nomes são alterados (anexando "2"), a recomendação é alterar os namespaces em vez de nomes, acrescentando novos namespaces com um número de versão ou uma data. Por exemplo, o `http://schemas.contoso.com/2005/05/21/PurchaseOrder` contrato de dados muda para o `http://schemas.contoso.com/2005/10/14/PurchaseOrder` contrato de dados.  
  
 Para obter mais informações, consulte as práticas recomendadas: [controle de versão do serviço](../../../docs/framework/wcf/service-versioning.md).  
  
 Ocasionalmente, você deve garantir a conformidade de esquema estrita para mensagens enviadas pelo seu aplicativo, mas não pode depender de mensagens de entrada para ser estritamente compatíveis com o esquema. Nesse caso, há um risco de que uma mensagem de entrada pode conter dados incorretos. Os valores incorretos são armazenados e retornados por [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] e, portanto, resulta em esquema inválido mensagens sendo enviadas. Para evitar esse problema, o recurso do ciclo deve ser desativado. Há duas formas de fazer isso.  
  
-   Não implementam a <xref:System.Runtime.Serialization.IExtensibleDataObject> interface em qualquer um dos seus tipos.  
  
-   Aplicar um <xref:System.ServiceModel.ServiceBehaviorAttribute> de atributo para o contrato de serviço com o <xref:System.ServiceModel.ServiceBehaviorAttribute.IgnoreExtensionDataObject%2A> propriedade definida como `true`.  
  
 [!INCLUDE[crabout](../../../includes/crabout-md.md)] ciclo, consulte [contratos de dados compatíveis por encaminhamento](../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md).  
  
## <a name="versioning-when-schema-validation-is-not-required"></a>Controle de versão quando a validação de esquema não é necessária  
 Conformidade de esquema estrita é raramente necessária. Muitas plataformas toleram elementos adicionais não são descritos por um esquema. Como isso é tolerado, o conjunto completo de recursos descritos em [controle de versão de contrato de dados](../../../docs/framework/wcf/feature-details/data-contract-versioning.md) e [contratos de dados compatíveis por encaminhamento](../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md) pode ser usado. As diretrizes a seguir são recomendadas.  
  
 Algumas das diretrizes devem ser seguidas exatamente para enviar novas versões de um tipo em que mais antiga é esperada ou enviar uma antiga onde um novo é esperado. Outras diretrizes não são rigorosamente exigidos, mas estão listados aqui porque eles podem ser afetados pelo futuro do controle de versão do esquema.  
  
1.  Não tente versão contratos de dados por tipo de herança. Para criar versões posteriores, altere o contrato de dados em um tipo existente ou criar um novo tipo relacionado.  
  
2.  O uso de herança junto com os contratos de dados é permitido, desde que a herança não é usada como um mecanismo de controle de versão e algumas regras são seguidas. Se um tipo derivado de um determinado tipo de base, não a tornarem derivar de um tipo base diferente em uma versão futura (a menos que ele tem os mesmos dados contrato). Há uma exceção a isso: você pode inserir um tipo na hierarquia entre um tipo de contrato de dados e seu tipo base, mas somente se ele não contém membros de dados com os mesmos nomes, como outros membros de todas as versões possíveis de outros tipos na hierarquia. Em geral, usando membros de dados com os mesmos nomes em diferentes níveis da mesma hierarquia de herança pode causar problemas graves de controle de versão e deve ser evitada.  
  
3.  Começando com a primeira versão de um contrato de dados, sempre implementar <xref:System.Runtime.Serialization.IExtensibleDataObject> para habilitar o ciclo. Para obter mais informações, consulte [Contratos de dados compatíveis por encaminhamento](../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md). Se você lançou uma ou mais versões de um tipo sem implementar essa interface, implementá-la na próxima versão do tipo.  
  
4.  Em versões posteriores, não altere o namespace ou nome de contrato de dados. Se alterar o nome ou o namespace do tipo subjacente do contrato de dados, certifique-se preservar o namespace e nome de contrato de dados usando os mecanismos adequados, como o <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A> propriedade o <xref:System.Runtime.Serialization.DataContractAttribute>. [!INCLUDE[crabout](../../../includes/crabout-md.md)] nomenclatura, consulte [nomes de contrato de dados](../../../docs/framework/wcf/feature-details/data-contract-names.md).  
  
5.  Em versões posteriores, não altere os nomes de quaisquer membros de dados. Se alterar o nome do campo, propriedade ou evento subjacente o membro de dados, use o `Name` propriedade o <xref:System.Runtime.Serialization.DataMemberAttribute> para preservar o nome de membro de dados existente.  
  
6.  Em versões posteriores, não altere o tipo de qualquer campo, propriedade ou evento subjacente de um membro de dados, de modo que os dados resultantes de contrato que alterações de membro de dados. Tenha em mente que tipos de interface são equivalentes a <xref:System.Object> a fim de determinar o contrato de dados esperado.  
  
7.  Em versões posteriores, não altere a ordem dos membros de dados existentes, ajustando o <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> propriedade o <xref:System.Runtime.Serialization.DataMemberAttribute> atributo.  
  
8.  Em versões posteriores, é possível adicionar novos membros de dados. Eles sempre devem seguir estas regras:  
  
    1.  O <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> propriedade sempre deve ser deixada em seu valor padrão de `false`.  
  
    2.  Se um valor padrão de `null` ou zero para o membro é inaceitável, um método de retorno de chamada deve ser fornecido com o <xref:System.Runtime.Serialization.OnDeserializingAttribute> para fornecer um padrão razoável caso o membro não está presente no fluxo de entrada. [!INCLUDE[crabout](../../../includes/crabout-md.md)] o retorno de chamada, consulte [retornos de chamada de serialização tolerantes à versão](../../../docs/framework/wcf/feature-details/version-tolerant-serialization-callbacks.md).  
  
    3.  O `Order` propriedade o `DataMemberAttribute` deve ser usado para certificar-se de que todos os membros de dados recém-adicionados aparecem após os membros de dados existente. A maneira recomendada de fazer isso é como segue: nenhum dos membros de dados na primeira versão do contrato de dados deve ter seu `Order` conjunto de propriedades. Todos os membros de dados adicionados na versão 2 do contrato de dados devem ter seus `Order` propriedade definida como 2. Todos os membros de dados adicionados na versão 3 do contrato de dados devem ter seu `Order` definido como 3 e assim por diante. É permitido ter mais de um membro de dados definido para o mesmo `Order` número.  
  
9. Não remova os membros de dados em versões posteriores, mesmo se o <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> propriedade foi deixada em sua propriedade padrão de `false` em versões anteriores.  
  
10. Não altere o `IsRequired` propriedade em quaisquer membros de dados existente de versão para versão.  
  
11. Para membros de dados obrigatórios (onde `IsRequired` é `true`), não altere o `EmitDefaultValue` propriedade de versão para versão.  
  
12. Não tente criar hierarquias de controle de versão ramificada. Ou seja, deve sempre haver um caminho em pelo menos uma direção de qualquer versão para qualquer outra versão usando apenas as alterações permitidas por estas diretrizes.  
  
     Por exemplo, se a versão 1 de um contrato de dados da pessoa que contém somente o membro de dados de nome, você não deve criar 2a de versão do contrato adicionando apenas a idade membro e versão 2b adicionando apenas o membro de endereço. Vai de 2a 2b envolveria removendo idade e adicionando endereço; Ir na outra direção envolveria endereço remover e adicionar idade. Não é permitido remover membros estas diretrizes.  
  
13. Você geralmente não deve criar novos subtipos de tipos de contrato de dados existente em uma nova versão do seu aplicativo. Da mesma forma, você não deve criar novos contratos de dados que são usados no lugar de dados membros declarados como objeto ou como tipos de interface. Criar essas novas classes é permitido somente quando souber que você pode adicionar os novos tipos de lista de tipos conhecidos de todas as instâncias do seu aplicativo antigo. Por exemplo, na versão 1 do seu aplicativo, você pode ter o tipo com o catálogo de contrato de dados de LibraryItem e os dados de jornal subtipos de contrato. LibraryItem teria uma lista de tipos conhecidos que contém o catálogo e os jornal. Suponha que agora você adicionar um tipo de revista na versão 2, que é um subtipo de LibraryItem. Se você enviar uma instância de revista da versão 2 para a versão 1, o contrato de dados de revista não foi encontrado na lista de tipos conhecidos e uma exceção será lançada.  
  
14. Você não deve adicionar ou remover membros de enumeração entre versões. Você também não deve renomear membros de enumeração, a menos que você use a propriedade de nome no `EnumMemberAttribute` atributo para manter seus nomes no modelo de contrato de dados iguais.  
  
15. Coleções são intercambiáveis no modelo de contrato de dados, conforme descrito em [tipos de coleção em contratos de dados](../../../docs/framework/wcf/feature-details/collection-types-in-data-contracts.md). Isso possibilita um alto grau de flexibilidade. No entanto, certifique-se de que você não inadvertidamente alterar um tipo de coleção em uma não-intercambiáveis forma de versão para versão. Por exemplo, não altere de uma coleção não personalizada (ou seja, sem o `CollectionDataContractAttribute` atributo) para um nome personalizado ou uma coleção personalizada para um não personalizada. Além disso, não altere as propriedades no `CollectionDataContractAttribute` de versão para versão. A única alteração permitida é adicionar uma propriedade de nome ou Namespace se namespace ou nome do tipo de coleção subjacente foi alterada e você precisa fazer seus dados nome e namespace de contrato igual de uma versão anterior.  
  
 Algumas das diretrizes listadas aqui podem ser ignoradas com segurança quando circunstâncias especiais se apliquem. Certifique-se de que compreender totalmente envolvidos antes desviam-se de que as diretrizes de mecanismos de esquema, serialização e desserialização.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A>  
 <xref:System.Runtime.Serialization.DataContractAttribute>  
 <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A>  
 <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A>  
 <xref:System.Runtime.Serialization.IExtensibleDataObject>  
 <xref:System.ServiceModel.ServiceBehaviorAttribute>  
 <xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A>  
 <xref:System.Runtime.Serialization.ExtensionDataObject>  
 <xref:System.Runtime.Serialization.OnDeserializingAttribute>  
 [Usando contratos de dados](../../../docs/framework/wcf/feature-details/using-data-contracts.md)  
 [Controle de versão de contrato de dados](../../../docs/framework/wcf/feature-details/data-contract-versioning.md)  
 [Nomes de contrato de dados](../../../docs/framework/wcf/feature-details/data-contract-names.md)  
 [Contratos de dados compatíveis com encaminhamento](../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md)  
 [Retornos de chamada de serialização tolerantes à versão](../../../docs/framework/wcf/feature-details/version-tolerant-serialization-callbacks.md)
