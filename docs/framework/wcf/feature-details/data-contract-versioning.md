---
title: Controle de versão de contrato de dados
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- versioning [WCF], data contracts
- versioning [WCF]
- data contracts [WCF], versioning
ms.assetid: 4a0700cb-5f5f-4137-8705-3a3ecf06461f
ms.openlocfilehash: 1ba51c51f30293e05dee17f9cf78cc049e1c751f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33496280"
---
# <a name="data-contract-versioning"></a>Controle de versão de contrato de dados
Como desenvolvem aplicativos, você também terá que alterar o uso de serviços de contratos de dados. Este tópico explica como contratos de dados de versão. Este tópico descreve os mecanismos de controle de versão do contrato de dados. Para obter uma visão geral completa e orientação prescritiva do controle de versão, consulte [práticas recomendadas: controle de versão de contrato de dados](../../../../docs/framework/wcf/best-practices-data-contract-versioning.md).  
  
## <a name="breaking-vs-nonbreaking-changes"></a>Quebrando vs. Alterações incondicionais  
 As alterações a um contrato de dados podem quebrar ou incondicional. Quando um contrato de dados é alterado de forma incondicional, um aplicativo usando a versão mais antiga do contrato pode se comunicar com um aplicativo usando a versão mais recente e um aplicativo usando a versão mais recente do contrato pode se comunicar com um aplicativo usando a versão mais antiga. Por outro lado, uma alteração significativa impede a comunicação em uma ou ambas as direções.  
  
 As alterações para um tipo que não afetam como são transmitida e recebida são incondicional. Essas alterações não alteram o contrato de dados, somente o tipo subjacente. Por exemplo, você pode alterar o nome de um campo de forma incondicional, se você definir o <xref:System.Runtime.Serialization.DataMemberAttribute.Name%2A> propriedade o <xref:System.Runtime.Serialization.DataMemberAttribute> para o nome da versão mais antigo. O código a seguir mostra a versão 1 de um contrato de dados.  
  
 [!code-csharp[C_DataContractVersioning#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractversioning/cs/source.cs#1)]
 [!code-vb[C_DataContractVersioning#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractversioning/vb/source.vb#1)]  
  
 O código a seguir mostra uma alteração incondicional.  
  
 [!code-csharp[C_DataContractVersioning#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractversioning/cs/source.cs#2)]
 [!code-vb[C_DataContractVersioning#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractversioning/vb/source.vb#2)]  
  
 Algumas alterações modifiquem os dados transmitidos, mas podem ou não podem ser recentes. As seguintes alterações sempre são significativas:  
  
-   Alterando o <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A> ou <xref:System.Runtime.Serialization.DataContractAttribute.Namespace%2A> valor de um contrato de dados.  
  
-   Alterando a ordem dos membros de dados usando o <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> propriedade o <xref:System.Runtime.Serialization.DataMemberAttribute>.  
  
-   Renomeando um membro de dados.  
  
-   Alterando o contrato de dados de um membro de dados. Por exemplo, alterando o tipo de membro de dados de um inteiro como uma cadeia de caracteres ou de um tipo com um contrato de dados denominado "Customer" para um tipo com um contrato de dados denominado "Pessoa".  
  
 As alterações a seguir também são possíveis.  
  
## <a name="adding-and-removing-data-members"></a>Adicionando e removendo membros de dados  
 Na maioria dos casos, adicionar ou remover um membro de dados não é uma alteração significativa, a menos que exigem a validade de esquema estrita (novas instâncias validar em relação ao esquema antigo).  
  
 Quando um tipo com um campo extra é desserializado em um tipo com um campo ausente, as informações adicionais serão ignoradas. (Também pode ser armazenada para fins de ciclo; para obter mais informações, consulte [contratos de dados compatíveis por encaminhamento](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md)).  
  
 Quando um tipo com um campo ausente é desserializado em um tipo com um campo adicional, o campo extra for deixado em seu valor padrão, zero geralmente ou `null`. (O valor padrão pode ser alterado; para obter mais informações, consulte [retornos de chamada de serialização tolerantes à versão](../../../../docs/framework/wcf/feature-details/version-tolerant-serialization-callbacks.md).)  
  
 Por exemplo, você pode usar o `CarV1` classe em um cliente e o `CarV2` classe em um serviço, ou você pode usar o `CarV1` classe em um serviço e o `CarV2` classe em um cliente.  
  
 [!code-csharp[C_DataContractVersioning#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractversioning/cs/source.cs#3)]
 [!code-vb[C_DataContractVersioning#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractversioning/vb/source.vb#3)]  
  
 O ponto de extremidade de versão 2 com êxito pode enviar dados para o ponto de extremidade de versão 1. Serializar a versão 2 do `Car` contrato de dados gera XML semelhante à seguinte.  
  
```xml  
<Car>  
    <Model>Porsche</Model>  
    <HorsePower>300</HorsePower>  
</Car>  
```  
  
 O mecanismo de desserialização em V1 não localizar um membro de dados correspondente para o `HorsePower` campo e, em seguida, descarta os dados.  
  
 Além disso, o ponto de extremidade de versão 1 pode enviar dados para o ponto de extremidade de versão 2. Serializar a versão 1 do `Car` contrato de dados gera XML semelhante à seguinte.  
  
```xml  
<Car>  
    <Model>Porsche</Model>  
</Car>  
```  
  
 O desserializador versão 2 não sabe o que definir o `HorsePower` campo, porque não há nenhum dado correspondentes no XML de entrada. Em vez disso, o campo é definido como o valor padrão de 0.  
  
## <a name="required-data-members"></a>Membros de dados necessários  
 Um membro de dados pode ser marcado como sendo necessária definindo o <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> propriedade o <xref:System.Runtime.Serialization.DataMemberAttribute> para `true`. Se necessárias estão faltando dados durante a desserialização, uma exceção será lançada em vez de definir o membro de dados para o valor padrão.  
  
 Adicionando um membro de dados necessários é uma alteração significativa. Ou seja, o tipo mais recente ainda pode ser enviado aos pontos de extremidade com o tipo mais antigo, mas não o oposto. Remover um membro de dados que foi marcado como necessária em qualquer versão anterior é também uma alteração significativa.  
  
 Alterando o <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> valor de propriedade de `true` para `false` não recentes, mas mudando de `false` para `true` pode ser quebrar se todas as versões anteriores do tipo não tem o membro de dados em questão.  
  
> [!NOTE]
>  Embora o <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> está definida como `true`, os dados de entrada podem ser nulos ou zero e um tipo devem estar preparado para lidar com essa possibilidade. Não use <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> como um mecanismo de segurança para ajudar a proteger os dados de entrada incorretos.  
  
## <a name="omitted-default-values"></a>Valores padrão omitido  
 É possível (embora não recomendado) para definir o `EmitDefaultValue` propriedade no atributo DataMemberAttribute para `false`, conforme descrito em [valores de padrão de membro de dados](../../../../docs/framework/wcf/feature-details/data-member-default-values.md). Se essa configuração for `false`, o membro de dados não será emitido se ele for definido como seu valor padrão (geralmente nulo ou zero). Isso não é compatível com membros de dados necessários em versões diferentes de duas maneiras:  
  
-   Um contrato de dados com um membro de dados que é necessário em uma versão não pode receber padrão (null ou zero) dados de uma versão diferente no qual o membro de dados tem `EmitDefaultValue` definido como `false`.  
  
-   Um membro de dados necessários que tem `EmitDefaultValue` definida como `false` não pode ser usado para serializar o padrão (null ou zero) valor, mas pode receber esse valor na desserialização. Isso cria um problema de ciclo (os dados podem ser lidos em mas os mesmos dados, em seguida, não podem ser gravados). Portanto, se `IsRequired` é `true` e `EmitDefaultValue` é `false` em uma versão, a mesma combinação deve ser aplicados a todas as outras versões, de modo que nenhuma versão do contrato de dados poderá produzir um valor que não resultam em uma viagem de ida e.  
  
## <a name="schema-considerations"></a>Considerações de esquema  
 Para obter uma explicação de como o esquema é produzida para tipos de contrato de dados, consulte [referência de esquema de contrato de dados](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md).  
  
 O esquema WCF produz para tipos de contrato de dados torna não pode fornecer controle de versão. Ou seja, o esquema exportado de uma determinada versão de um tipo contém somente os membros de dados presentes nessa versão. Implementando o <xref:System.Runtime.Serialization.IExtensibleDataObject> interface não altera o esquema para um tipo.  
  
 Membros de dados são exportados para o esquema como elementos opcionais por padrão. Ou seja, o `minOccurs` (atributo XML) valor é definido como 0. Membros de dados necessários são exportados com `minOccurs` definido como 1.  
  
 Muitas das alterações consideradas incondicional, na verdade, são significativas se estrita aderência a esquema é necessária. No exemplo anterior, um `CarV1` instância com apenas o `Model` elemento seria validar em relação a `CarV2` esquema (que tem `Model` e `Horsepower`, mas são opcionais). No entanto, o inverso é verdadeiro não: uma `CarV2` instância falhará a validação em relação a `CarV1` esquema.  
  
 Ciclo também envolve algumas considerações adicionais. Para obter mais informações, consulte a seção "Considerações sobre o esquema" [contratos de dados compatíveis por encaminhamento](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md).  
  
### <a name="other-permitted-changes"></a>Outras alterações de permissão  
 Implementando o <xref:System.Runtime.Serialization.IExtensibleDataObject> interface é uma alteração incondicional. No entanto, o suporte do ciclo não existe para versões do tipo antes da versão na qual <xref:System.Runtime.Serialization.IExtensibleDataObject> foi implementado. Para obter mais informações, consulte [Contratos de dados compatíveis por encaminhamento](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md).  
  
## <a name="enumerations"></a>Enumerações  
 Adicionar ou remover um membro de enumeração é uma alteração significativa. Alterando o nome de um membro de enumeração é recentes, a menos que seu nome de contrato é mantido o mesmo que a versão antiga, usando o `EnumMemberAtttribute` atributo. Para obter mais informações, consulte [tipos de enumeração em contratos de dados](../../../../docs/framework/wcf/feature-details/enumeration-types-in-data-contracts.md).  
  
## <a name="collections"></a>Coleções  
 A maioria das alterações de coleção são incondicional porque a maioria dos tipos de coleção são intercambiáveis entre si no modelo de contrato de dados. No entanto, fazer uma coleção nãopersonalizada personalizada ou vice-versa é uma alteração significativa. Além disso, alterar as configurações de personalização da coleção é uma alteração significativa; ou seja, alterar seu nome de contrato de dados e o namespace, nome do elemento, o nome do elemento chave e o nome do elemento de valor de repetição. Para obter mais informações sobre personalização da coleção, consulte [tipos de coleção em contratos de dados](../../../../docs/framework/wcf/feature-details/collection-types-in-data-contracts.md).  
Naturalmente, o contrato de dados de conteúdo de uma coleção (por exemplo, a alteração de uma lista de inteiros para uma lista de cadeias de caracteres) a alteração é uma alteração significativa.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Runtime.Serialization.DataMemberAttribute.Name%2A>  
 <xref:System.Runtime.Serialization.DataMemberAttribute>  
 <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A>  
 <xref:System.Runtime.Serialization.DataContractAttribute.Namespace%2A>  
 <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A>  
 <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A>  
 <xref:System.Runtime.Serialization.SerializationException>  
 <xref:System.Runtime.Serialization.IExtensibleDataObject>  
 [Retornos de chamada de serialização tolerantes à versão](../../../../docs/framework/wcf/feature-details/version-tolerant-serialization-callbacks.md)  
 [Práticas recomendadas: controle de versão de contrato de dados](../../../../docs/framework/wcf/best-practices-data-contract-versioning.md)  
 [Usando contratos de dados](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)  
 [Equivalência de contrato de dados](../../../../docs/framework/wcf/feature-details/data-contract-equivalence.md)  
 [Contratos de dados compatíveis com encaminhamento](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md)
