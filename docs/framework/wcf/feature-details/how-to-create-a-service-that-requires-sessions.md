---
title: 'Como: Criar um serviço que requer sessões'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8a7613ef-0df9-47c3-b8dc-47f42cb1fd8b
ms.openlocfilehash: fa151d472dbd27a62f91cd3a43339c66787dc456
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54615436"
---
# <a name="how-to-create-a-service-that-requires-sessions"></a>Como: Criar um serviço que requer sessões
As sessões criam um estado compartilhado entre dois ou mais pontos de extremidade que habilita recursos úteis, como os retornos de chamada, a segurança de saltos múltiplos e associações entre clientes e instâncias de serviço. Para obter mais informações sobre as sessões em aplicativos do Windows Communication Foundation (WCF), consulte [sessões usando](../../../../docs/framework/wcf/using-sessions.md).  
  
### <a name="to-specify-that-a-contract-require-its-binding-to-support-sessions"></a>Para especificar que um contrato de exige sua associação dar suporte a sessões  
  
1.  Crie um contrato de serviço com pelo menos uma operação. Para obter um exemplo de como criar um contrato de serviço, consulte [como: Definir um contrato de serviço](../../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md).  
  
2.  Modificar a <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType> que declara o contrato, definindo o <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType> propriedade para qualquer um:  
  
    -   <xref:System.ServiceModel.SessionMode.Required?displayProperty=nameWithType> Se este contrato deve ser executado dentro de uma sessão.  
  
    -   <xref:System.ServiceModel.SessionMode.Allowed?displayProperty=nameWithType> Se esse contrato pode ser executado dentro de uma sessão.  
  
    -   <xref:System.ServiceModel.SessionMode.NotAllowed?displayProperty=nameWithType> Se este contrato não deve ser executado dentro de uma sessão.  
  
3.  Configure o ponto de extremidade de serviço para usar uma associação que dá suporte a sessões. O exemplo de configuração a seguir mostra o uso do <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType>, que oferece suporte a um WS`-`ReliableMessaging sessão.  
  
     [!code-xml[SCA.Session#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/sca.session/cs/hostapplication.exe.config#2)]   
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir mostra como especificar um requisito de contrato de nível de sessão e usar um arquivo de configuração para dar suporte a esse requisito com o <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType> associação.  
  
 [!code-csharp[SCA.Session#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/sca.session/cs/services.cs#1)] 
 [!code-vb[SCA.Session#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/sca.session/vb/services.vb#1)]      
 [!code-xml[SCA.Session#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/sca.session/cs/hostapplication.exe.config#2)]     
  
## <a name="see-also"></a>Consulte também
- <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType>
- <xref:System.ServiceModel.SessionMode?displayProperty=nameWithType>
