---
title: Como criar um serviço que requer sessões
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8a7613ef-0df9-47c3-b8dc-47f42cb1fd8b
ms.openlocfilehash: 495de5a926cfc0c5aab88337f5f33b991c49e71a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184984"
---
# <a name="how-to-create-a-service-that-requires-sessions"></a>Como criar um serviço que requer sessões
As sessões criam um estado compartilhado entre dois ou mais pontos finais que permite recursos úteis, como retornos de chamadas, segurança multi-hop e associações entre clientes e instâncias de serviço. Para obter mais informações sobre sessões em aplicativos da Windows Communication Foundation (WCF), consulte [Usando sessões](../../../../docs/framework/wcf/using-sessions.md).  
  
### <a name="to-specify-that-a-contract-require-its-binding-to-support-sessions"></a>Para especificar que um contrato requer sua vinculação para suportar sessões  
  
1. Crie um contrato de serviço com pelo menos uma operação. Para um exemplo de como criar um contrato de serviço, consulte [Como: Definir um Contrato de Serviço](../../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md).  
  
2. Modificar <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType> o que declara o <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType> contrato definindo a propriedade para:  
  
    - <xref:System.ServiceModel.SessionMode.Required?displayProperty=nameWithType>se este contrato deve ser executado dentro de uma sessão.  
  
    - <xref:System.ServiceModel.SessionMode.Allowed?displayProperty=nameWithType>se este contrato pode ser executado dentro de uma sessão.  
  
    - <xref:System.ServiceModel.SessionMode.NotAllowed?displayProperty=nameWithType>se este contrato não deve ser executado dentro de uma sessão.  
  
3. Configure o ponto final do serviço para usar uma vinculação que suporte as sessões. O exemplo de configuração <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType>a seguir mostra o`-`uso do , que suporta uma sessão WS ReliableMessaging.  
  
     [!code-xml[SCA.Session#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/sca.session/cs/hostapplication.exe.config#2)]
  
## <a name="example"></a>Exemplo  
 O código de exemplo a seguir mostra como especificar um requisito de <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType> sessão de nível de contrato e usar um arquivo de configuração para suportar esse requisito com a vinculação.  
  
 [!code-csharp[SCA.Session#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/sca.session/cs/services.cs#1)]
 [!code-vb[SCA.Session#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/sca.session/vb/services.vb#1)]
 [!code-xml[SCA.Session#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/sca.session/cs/hostapplication.exe.config#2)]
  
## <a name="see-also"></a>Confira também

- <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType>
- <xref:System.ServiceModel.SessionMode?displayProperty=nameWithType>
