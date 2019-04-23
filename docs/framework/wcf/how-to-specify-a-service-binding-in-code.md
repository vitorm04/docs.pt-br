---
title: 'Como: especificar uma associação de serviço no código'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 67ab5dd8-79c1-4e62-aa75-828ea918a53a
ms.openlocfilehash: 9f3320b031141246a394191a1924509204707dc1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59303447"
---
# <a name="how-to-specify-a-service-binding-in-code"></a>Como: especificar uma associação de serviço no código
Neste exemplo, uma `ICalculator` contrato é definido para um serviço de Calculadora e, em seguida, o serviço é implementado de `CalculatorService` classe e, em seguida, seu ponto de extremidade é definido no código, onde ele é especificado que o serviço deve usar o <xref:System.ServiceModel.BasicHttpBinding> classe.  
  
 Ele geralmente é a prática recomendada para especificar declarativamente as informações de endereço e associação na configuração em vez de imperativa no código. Definir pontos de extremidade no código geralmente não é prático porque as associações e endereços para um serviço implantado normalmente são diferentes daqueles usados enquanto o serviço está sendo desenvolvido. De modo geral, informações fora do código de endereçamento e manter a associação permite que eles alterem os sem ter que recompilar ou reimplantar o aplicativo.  
  
 Para obter uma descrição de como configurar esse serviço usando os elementos de configuração em vez de código, consulte [como: Especificar uma associação de serviço na configuração](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).  
  
### <a name="to-specify-in-code-to-use-the-basichttpbinding-for-the-service"></a>Para especificar no código para usar o BasicHttpBinding para o serviço  
  
1. Defina um contrato de serviço para o tipo de serviço.  
  
     [!code-csharp[C_HowTo_CodeServiceBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#1)]
     [!code-vb[C_HowTo_CodeServiceBinding#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#1)]  
  
2. Implemente o contrato de serviço em uma classe de serviço.  
  
     [!code-csharp[C_HowTo_CodeServiceBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#2)]
     [!code-vb[C_HowTo_CodeServiceBinding#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#2)]  
  
3. No aplicativo de hospedagem, crie o endereço base para o serviço e associação a ser usada com o serviço.  
  
     [!code-csharp[C_HowTo_CodeServiceBinding#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#3)]
     [!code-vb[C_HowTo_CodeServiceBinding#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#3)]  
  
4. Criar o host para o serviço, adicione o ponto de extremidade e, em seguida, abra o host.  
  
     [!code-csharp[C_HowTo_CodeServiceBinding#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#4)]
     [!code-vb[C_HowTo_CodeServiceBinding#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#4)]  
  
### <a name="to-modify-the-default-values-of-the-binding-properties"></a>Para modificar os valores padrão das propriedades de associação  
  
1. Para modificar um dos valores de propriedade padrão da <xref:System.ServiceModel.BasicHttpBinding> de classe, defina o valor da propriedade na associação para o novo valor antes de criar o host. Por exemplo, para alterar os valores de tempo limite de abertura e fechamento do padrão de 1 minuto para 2 minutos, use o seguinte.  
  
     [!code-csharp[C_HowTo_CodeServiceBinding#5](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#5)]
     [!code-vb[C_HowTo_CodeServiceBinding#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#5)]  
  
## <a name="see-also"></a>Consulte também

- [Usando associações para configurar serviços e clientes](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [Especificando um endereço do ponto de extremidade](../../../docs/framework/wcf/specifying-an-endpoint-address.md)
