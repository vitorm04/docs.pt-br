---
title: Equivalência de contrato de dados
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data contracts [WCF], equivalence
ms.assetid: f06f3c7e-c235-4ec1-b200-68142edf1ed1
ms.openlocfilehash: a526a58ef801e91775756e6a84a94a066d32d284
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59214930"
---
# <a name="data-contract-equivalence"></a>Equivalência de contrato de dados
Para um cliente enviar com êxito os dados de um determinado tipo para um serviço ou um serviço para enviar com êxito os dados para um cliente, o tipo de envio não necessariamente precisa existir na extremidade receptora. O único requisito é que os contratos de ambos os tipos de dados ser equivalentes. (Às vezes, equivalência estrita não é necessária, conforme discutido em [controle de versão de contrato de dados](../../../../docs/framework/wcf/feature-details/data-contract-versioning.md).)  
  
 Para contratos de dados para serem equivalentes, eles devem ter o mesmo namespace e nome. Além disso, cada membro de dados em um lado deve ter um membro de dados equivalentes no outro lado.  
  
 Para membros de dados para serem equivalentes, eles devem ter o mesmo nome. Além disso, eles devem representar o mesmo tipo de dados; ou seja, seus contratos de dados devem ser equivalentes.  
  
> [!NOTE]
>  Observação de contrato de dados nomes e namespaces, bem como nomes de membro de dados diferenciam maiusculas de minúsculas.  
  
 Para obter mais informações sobre namespaces e nomes de contrato de dados, bem como nomes de membro de dados, consulte [nomes de contrato de dados](../../../../docs/framework/wcf/feature-details/data-contract-names.md).  
  
 Se existem dois tipos no mesmo lado (remetente ou receptor) e seus contratos de dados não são equivalentes (por exemplo, eles têm membros de dados diferente), não deve atribuir o mesmo nome e namespace. Isso pode causar exceções seja lançada.  
  
 Os contratos de dados para os seguintes tipos são equivalentes:  
  
 [!code-csharp[C_DataContractNames#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#5)]
 [!code-vb[C_DataContractNames#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#5)]  
  
## <a name="data-member-order-and-data-contract-equivalence"></a>Equivalência de contrato de dados e de ordem de membro de dados  
 Usando o <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> propriedade do <xref:System.Runtime.Serialization.DataMemberAttribute> classe pode afetar a equivalência de contrato de dados. Os contratos de dados devem ter membros que aparecem na mesma ordem como equivalente. A ordem padrão é alfabética. Para obter mais informações, consulte [ordem de membro de dados](../../../../docs/framework/wcf/feature-details/data-member-order.md).  
  
 Por exemplo, o código a seguir resulta em contratos de dados equivalente.  
  
 [!code-csharp[C_DataContractNames#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#6)]
 [!code-vb[C_DataContractNames#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#6)]  
  
 No entanto, o seguinte não resulta em um contrato de dados equivalente.  
  
 [!code-csharp[C_DataContractNames#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#7)]
 [!code-vb[C_DataContractNames#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#7)]  
  
## <a name="inheritance-interfaces-and-data-contract-equivalence"></a>Herança, Interfaces e equivalência de contrato de dados  
 Ao determinar a equivalência, um contrato de dados que herda de outro contrato de dados é tratado como se ele é apenas um contrato de dados que inclui todos os membros de dados do tipo base. Tenha em mente que a ordem dos membros de dados deve corresponder e que os membros do tipo base precedem derivadas membros de tipo na ordem. Além disso, se, como no exemplo de código a seguir, os membros de dados de dois têm o mesmo valor de ordem, a ordenação para os membros de dados é em ordem alfabética. Para obter mais informações, consulte [ordem de membro de dados](../../../../docs/framework/wcf/feature-details/data-member-order.md).  
  
 No exemplo a seguir, o contrato de dados para o tipo `Employee` é equivalente ao contrato de dados para o tipo `Worker`.  
  
 [!code-csharp[C_DataContractNames#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#8)]
 [!code-vb[C_DataContractNames#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#8)]  
  
 Ao passar parâmetros e valores retornados entre um cliente e um serviço, um contrato de dados de uma classe base não pode ser enviado quando o ponto de extremidade receptor espera que um contrato de dados de uma classe derivada. Isso está de acordo com princípios de programação orientada a objeto. No exemplo anterior, um objeto do tipo `Person` não pode ser enviada quando um `Employee` é esperado.  
  
 Um contrato de dados de uma classe derivada pode ser enviado quando um contrato de dados de uma classe base é esperada, mas somente se o ponto de extremidade de recebimento "sabe" do tipo derivado usando o <xref:System.Runtime.Serialization.KnownTypeAttribute>. Para obter mais informações, consulte [tipos conhecidos de contrato de dados](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md). No exemplo anterior, um objeto do tipo `Employee` podem ser enviadas quando um `Person` é o esperado, mas somente se o código do receptor emprega o <xref:System.Runtime.Serialization.KnownTypeAttribute> incluí-lo na lista de tipos conhecidos.  
  
 Ao passar parâmetros e valores retornados entre aplicativos, se o tipo esperado é uma interface, ele é equivalente o tipo esperado é do tipo <xref:System.Object>. Porque cada tipo, por fim, deriva <xref:System.Object>, cada contrato de dados deriva, por fim, o contrato de dados <xref:System.Object>. Portanto, qualquer tipo de contrato de dados pode ser passado quando se espera que uma interface. São necessárias etapas adicionais para trabalhar com êxito com interfaces; Para obter mais informações, consulte [tipos conhecidos de contrato de dados](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.DataMemberAttribute>
- [Ordem de membro de dados](../../../../docs/framework/wcf/feature-details/data-member-order.md)
- [Tipos conhecidos de contrato de dados](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)
- [Nomes de contrato de dados](../../../../docs/framework/wcf/feature-details/data-contract-names.md)
