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
ms.openlocfilehash: 53080975c03430a6c05bf72f58610b328430a3c2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59118021"
---
# <a name="data-contract-versioning"></a>Controle de versão de contrato de dados
Como desenvolver aplicativos, você também pode ter que alterar o uso de serviços de contratos de dados. Este tópico explica como contratos de dados de versão. Este tópico descreve os mecanismos de controle de versão do contrato de dados. Para obter uma visão geral completa e diretrizes prescritivas do controle de versão, consulte [práticas recomendadas: Controle de versão de contrato de dados](../../../../docs/framework/wcf/best-practices-data-contract-versioning.md).  
  
## <a name="breaking-vs-nonbreaking-changes"></a>Quebrando vs. Alterações imediatas ou não  
 Alterações em um contrato de dados podem ser significativas ou incondicional. Quando um contrato de dados é alterado de forma incondicional, um aplicativo usando a versão mais antiga do contrato pode se comunicar com um aplicativo usando a versão mais recente, e um aplicativo usando a versão mais recente do contrato pode se comunicar com um aplicativo usando a versão mais antiga. Por outro lado, uma alteração significativa impede a comunicação em uma ou ambas as direções.  
  
 Todas as alterações em um tipo que não afetam como são transmitido e recebido são incondicional. Essas alterações não alteram o contrato de dados, somente o tipo subjacente. Por exemplo, você pode alterar o nome de um campo de forma incondicional, se você definir, em seguida, o <xref:System.Runtime.Serialization.DataMemberAttribute.Name%2A> propriedade do <xref:System.Runtime.Serialization.DataMemberAttribute> para o nome da versão mais antigo. O código a seguir mostra a versão 1 de um contrato de dados.  
  
 [!code-csharp[C_DataContractVersioning#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractversioning/cs/source.cs#1)]
 [!code-vb[C_DataContractVersioning#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractversioning/vb/source.vb#1)]  
  
 O código a seguir mostra uma alteração incondicional.  
  
 [!code-csharp[C_DataContractVersioning#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractversioning/cs/source.cs#2)]
 [!code-vb[C_DataContractVersioning#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractversioning/vb/source.vb#2)]  
  
 Algumas alterações modifiquem os dados transmitidos, mas podem ou não podem ser significativas. As seguintes alterações sempre são significativas:  
  
-   Alterando a <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A> ou <xref:System.Runtime.Serialization.DataContractAttribute.Namespace%2A> valor de um contrato de dados.  
  
-   Alterando a ordem dos membros de dados usando o <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> propriedade do <xref:System.Runtime.Serialization.DataMemberAttribute>.  
  
-   Renomeando um membro de dados.  
  
-   Alterando o contrato de dados de um membro de dados. Por exemplo, alterando o tipo de membro de dados de um inteiro para uma cadeia de caracteres ou de um tipo com um contrato de dados denominado "Cliente" em um tipo com um contrato de dados chamado "Person".  
  
 As alterações a seguir também são possíveis.  
  
## <a name="adding-and-removing-data-members"></a>Adicionando e removendo membros de dados  
 Na maioria dos casos, adicionando ou removendo um membro de dados não é uma alteração significativa, a menos que você precisar de validade de esquema estrita (novas instâncias de validar no esquema antigo).  
  
 Quando um tipo com um campo adicional é desserializado em um tipo com um campo ausente, as informações adicionais serão ignoradas. (Também pode ser armazenada para fins de ciclo completo; para obter mais informações, consulte [contratos de dados compatíveis por encaminhamento](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md)).  
  
 Quando um tipo com um campo ausente é desserializado em um tipo com um campo adicional, o campo extra é deixado como seu valor padrão, geralmente zero ou `null`. (O valor padrão pode ser alterado; para obter mais informações, consulte [retornos de chamada de serialização tolerantes à versão](../../../../docs/framework/wcf/feature-details/version-tolerant-serialization-callbacks.md).)  
  
 Por exemplo, você pode usar o `CarV1` classe em um cliente e o `CarV2` classe em um serviço, ou você pode usar o `CarV1` classe em um serviço e o `CarV2` classe em um cliente.  
  
 [!code-csharp[C_DataContractVersioning#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractversioning/cs/source.cs#3)]
 [!code-vb[C_DataContractVersioning#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractversioning/vb/source.vb#3)]  
  
 O ponto de extremidade da versão 2 com êxito pode enviar dados para o ponto de extremidade da versão 1. Serializar a versão 2 do `Car` contrato de dados gera XML semelhante ao seguinte.  
  
```xml  
<Car>  
    <Model>Porsche</Model>  
    <HorsePower>300</HorsePower>  
</Car>  
```  
  
 O mecanismo de desserialização em V1 não encontrar um membro de dados correspondente para o `HorsePower` de campo e, em seguida, descarta os dados.  
  
 Além disso, o ponto de extremidade da versão 1 pode enviar dados para o ponto de extremidade da versão 2. Serializar a versão 1 do `Car` contrato de dados gera XML semelhante ao seguinte.  
  
```xml  
<Car>  
    <Model>Porsche</Model>  
</Car>  
```  
  
 O desserializador versão 2 não sabe o que deve definir o `HorsePower` campo, porque não há nenhum dado correspondente no XML de entrada. Em vez disso, o campo é definido como o valor padrão de 0.  
  
## <a name="required-data-members"></a>Membros de dados necessários  
 Um membro de dados pode ser marcado como sendo solicitados, definindo o <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> propriedade do <xref:System.Runtime.Serialization.DataMemberAttribute> para `true`. Se for necessário que os dados estão ausentes ao desserializar, uma exceção é lançada em vez de definir o membro de dados para seu valor padrão.  
  
 Adicionar um membro de dados necessário é uma alteração significativa. Ou seja, o tipo mais recente ainda pode ser enviado aos pontos de extremidade com o tipo mais antigo, mas não o oposto. Remoção de um membro de dados que foi marcado como obrigatório em qualquer versão anterior é também uma alteração significativa.  
  
 Alterando a <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> valor de propriedade de `true` à `false` é não significativas, mas alterando-o de `false` para `true` podem ser significativas se todas as versões anteriores do tipo não tem o membro de dados em questão.  
  
> [!NOTE]
>  Embora o <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> estiver definida como `true`, os dados de entrada podem ser nulos ou zero e um tipo devem estar preparado para lidar com essa possibilidade. Não use <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> como um mecanismo de segurança para proteger contra os dados de entrada incorretos.  
  
## <a name="omitted-default-values"></a>Valores omitidos padrão  
 É possível (embora não recomendado) para definir a `EmitDefaultValue` propriedade no atributo DataMemberAttribute para `false`, conforme descrito em [valores de padrão de membro de dados](../../../../docs/framework/wcf/feature-details/data-member-default-values.md). Se essa configuração for `false`, o membro de dados não será emitido se ele for definido como seu valor padrão (geralmente é null ou igual a zero). Isso não é compatível com os membros de dados necessários em versões diferentes de duas maneiras:  
  
-   Um contrato de dados com um membro de dados que é necessária em uma versão não pode receber padrão (nulo ou zero) dados de uma versão diferente no qual o membro de dados tem `EmitDefaultValue` definido como `false`.  
  
-   Um membro de dados necessários que tem `EmitDefaultValue` definido como `false` não pode ser usado para serializar seu padrão (nulo ou zero) de valor, mas podem receber esse valor na desserialização. Isso cria um problema de ciclo completo (dados podem ser lidos na, mas os mesmos dados, em seguida, não podem ser gravados). Portanto, se `IsRequired` está `true` e `EmitDefaultValue` é `false` em uma versão, a mesma combinação deve ser aplicada a todas as outras versões, de modo que nenhuma versão do contrato de dados seria capaz de produzir um valor que não resulte em uma viagem de ida e volta.  
  
## <a name="schema-considerations"></a>Considerações sobre o esquema  
 Para obter uma explicação de qual esquema é produzida para tipos de contrato de dados, consulte [referência de esquema de contrato de dados](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md).  
  
 O esquema WCF produz para tipos de contrato de dados não torna nenhuma provisões para controle de versão. Ou seja, o esquema exportado de uma determinada versão de um tipo contém somente os membros de dados presentes nessa versão. Implementando o <xref:System.Runtime.Serialization.IExtensibleDataObject> interface não altera o esquema para um tipo.  
  
 Membros de dados são exportados para o esquema como elementos opcionais por padrão. Ou seja, o `minOccurs` valor (atributo XML) é definido como 0. Membros de dados necessários são exportados com `minOccurs` definido como 1.  
  
 Muitas das alterações consideradas incondicional, na verdade, são significativas se estrita aderência ao esquema for necessária. No exemplo anterior, uma `CarV1` da instância com apenas o `Model` elemento seria validar em relação a `CarV2` esquema (que tem as duas `Model` e `Horsepower`, mas são opcionais). No entanto, o inverso não é verdadeiro: uma `CarV2` instância falharia validação em relação a `CarV1` esquema.  
  
 O ciclo completo também envolve algumas considerações adicionais. Para obter mais informações, consulte a seção "Considerações sobre o esquema" no [contratos de dados compatíveis por encaminhamento](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md).  
  
### <a name="other-permitted-changes"></a>Outras alterações de permissão  
 Implementando o <xref:System.Runtime.Serialization.IExtensibleDataObject> interface é uma alteração incondicional. No entanto, o suporte do ciclo completo não existe para versões do tipo antes da versão na qual <xref:System.Runtime.Serialization.IExtensibleDataObject> foi implementada. Para obter mais informações, consulte [Contratos de dados compatíveis por encaminhamento](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md).  
  
## <a name="enumerations"></a>Enumerações  
 Adicionar ou remover um membro de enumeração é uma alteração significativa. Alterando o nome de um membro de enumeração está interrompendo a menos que seu nome de contrato é mantido igual a versão antiga, usando o `EnumMemberAttribute` atributo. Para obter mais informações, consulte [tipos de enumeração em contratos de dados](../../../../docs/framework/wcf/feature-details/enumeration-types-in-data-contracts.md).  
  
## <a name="collections"></a>Coleções  
 A maioria das alterações de coleção são incondicional porque a maioria dos tipos de coleção são intercambiáveis uns com os outros no modelo de contrato de dados. No entanto, fazer uma coleção não personalizada personalizada ou vice-versa é uma alteração significativa. Além disso, alterando as configurações de personalização da coleção é uma alteração significativa; ou seja, alterando seu nome de contrato de dados e o namespace, nome do elemento, o nome do elemento-chave e o nome do elemento de valor de repetição. Para obter mais informações sobre a personalização da coleção, consulte [tipos de coleção em contratos de dados](../../../../docs/framework/wcf/feature-details/collection-types-in-data-contracts.md).  
Naturalmente, alterar o contrato de dados de conteúdo de uma coleção (por exemplo, a alteração de uma lista de inteiros para uma lista de cadeias de caracteres) é uma alteração significativa.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Runtime.Serialization.DataMemberAttribute.Name%2A>
- <xref:System.Runtime.Serialization.DataMemberAttribute>
- <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A>
- <xref:System.Runtime.Serialization.DataContractAttribute.Namespace%2A>
- <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A>
- <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A>
- <xref:System.Runtime.Serialization.SerializationException>
- <xref:System.Runtime.Serialization.IExtensibleDataObject>
- [Retornos de chamada de serialização tolerantes à versão](../../../../docs/framework/wcf/feature-details/version-tolerant-serialization-callbacks.md)
- [Melhores práticas: Controle de versão de contrato de dados](../../../../docs/framework/wcf/best-practices-data-contract-versioning.md)
- [Usando contratos de dados](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)
- [Equivalência de contrato de dados](../../../../docs/framework/wcf/feature-details/data-contract-equivalence.md)
- [Contratos de dados compatíveis por encaminhamento](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md)
