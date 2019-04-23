---
title: 'Como: criar um ponto de extremidade de serviço em código'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3fbb22fa-2930-48b8-b437-def1de87c6a0
ms.openlocfilehash: 65d26c0b9a41a6825108b73f822add4d91400055
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59302524"
---
# <a name="how-to-create-a-service-endpoint-in-code"></a>Como: criar um ponto de extremidade de serviço em código
Neste exemplo, uma `ICalculator` contrato é definido para um serviço de Calculadora e, em seguida, o serviço é implementado de `CalculatorService` classe e, em seguida, seu ponto de extremidade é definido no código, onde ele é especificado que o serviço deve usar o <xref:System.ServiceModel.BasicHttpBinding> classe.  
  
 Ele geralmente é a prática recomendada para especificar declarativamente as informações de endereço e associação na configuração em vez de imperativa no código. Definir pontos de extremidade no código geralmente não é prático porque as associações e endereços para um serviço implantado normalmente são diferentes daqueles usados enquanto o serviço está sendo desenvolvido. De modo geral, informações fora do código de endereçamento e manter a associação permite que eles alterem os sem ter que recompilar ou reimplantar o aplicativo.  
  
#### <a name="to-create-a-service-endpoint-in-code"></a>Para criar um ponto de extremidade de serviço no código  
  
1. Crie a interface que define o contrato de serviço.  
  
     [!code-csharp[c_HowTo_CodeServiceBinding#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#1)]
     [!code-vb[c_HowTo_CodeServiceBinding#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#1)]  
  
2. Implemente o contrato de serviço definido na etapa 1.  
  
     [!code-csharp[c_HowTo_CodeServiceBinding#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#2)]
     [!code-vb[c_HowTo_CodeServiceBinding#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#2)]  
  
3. No aplicativo de hospedagem, crie o endereço base para o serviço e a associação a ser usado com o serviço.  
  
     [!code-csharp[c_HowTo_CodeServiceBinding#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#3)]
     [!code-vb[c_HowTo_CodeServiceBinding#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#3)]  
  
4. Criar o host e chamar <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%28System.Type%2CSystem.ServiceModel.Channels.Binding%2CSystem.String%29> ou uma das outras sobrecargas para adicionar o ponto de extremidade de serviço para o host.  
  
     [!code-csharp[c_HowTo_CodeServiceBinding#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#6)]
     [!code-vb[c_HowTo_CodeServiceBinding#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#6)]  
  
     Para especificar a associação no código, mas usar os pontos de extremidade padrão fornecidos pelo tempo de execução, passe o endereço grave no construtor ao criar o <xref:System.ServiceModel.ServiceHost>e não chame <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A>.  
  
     [!code-csharp[c_HowTo_CodeServiceBinding#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#7)]
     [!code-vb[c_HowTo_CodeServiceBinding#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#7)]  
  
     Para obter mais informações sobre pontos de extremidade padrão, consulte [configuração simplificado](../../../../docs/framework/wcf/simplified-configuration.md) e [configuração simplificada para serviços WCF](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).  
  
## <a name="see-also"></a>Consulte também

- [Como: Especificar uma associação de serviço no código](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-code.md)
