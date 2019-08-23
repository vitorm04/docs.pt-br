---
title: 'Como: usar um moniker de serviço com contratos de intercâmbio de metadados'
ms.date: 03/30/2017
ms.assetid: c41a07e5-cb9d-45d6-9ea4-34511e227faf
ms.openlocfilehash: 00aa1bbde95c0636391f213f830fc67b2dedf459
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968799"
---
# <a name="how-to-use-a-service-moniker-with-metadata-exchange-contracts"></a>Como: usar um moniker de serviço com contratos de intercâmbio de metadados
Depois de desenvolver alguns novos serviços WCF, você pode decidir que deseja ser capaz de chamar esses serviços de um script ou de um aplicativo Visual Basic 6,0. Um método seria gerar um assembly de cliente WCF, registrar o assembly com COM, instalar o assembly no GAC e, em seguida, fazer referência aos tipos COM do seu código Visual Basic. Ao distribuir o aplicativo, você também precisará distribuir o assembly do cliente WCF. O usuário precisará registrar o assembly do cliente WCF com com e colocá-lo no GAC. A interoperabilidade COM do WCF também permite que você faça as mesmas chamadas de serviço sem depender de um assembly de cliente WCF. O moniker do WCF permite chamar qualquer serviço WCF de qualquer linguagem compatível COM COM (Visual Basic, VBScript, Visual Basic for Applications (VBA) e assim por diante) especificando um URI de ponto de extremidade de intercâmbio de metadados (MEX) que o moniker do serviço usa para extrair o tipo informações sobre o serviço. Este tópico descreve como chamar o Introdução exemplo do WCF usando um moniker do WCF que especifica um ponto de extremidade MEX.  
  
> [!NOTE]
> Os tipos definidos pelo assembly do cliente WCF nunca são instanciados na verdade. O assembly é usado somente para metadados.  
  
### <a name="using-the-service-moniker-with-a-mex-address"></a>Usando o moniker do serviço com um endereço MEX  
  
1. Crie o introdução exemplo e use o Internet Explorer para navegar até sua URL http://localhost/ServiceModelSamples/Service.svc) (para garantir que o serviço esteja funcionando.  
  
2. Crie um script de Visual Basic ou Visual Basic aplicativo que contenha o seguinte código:  
  
    ```  
    monString = "service:mexaddress=http://localhost/ServiceModelSamples/Service.svc/MEX"  
    monString = monString + ", address=http://localhost/ServiceModelSamples/Service.svc"  
    monString = monString + ", contract=ICalculator, contractNamespace=http://Microsoft.ServiceModel.Samples"  
    monString = monString + ", binding=WSHttpBinding_ICalculator, bindingNamespace=http://Microsoft.ServiceModel.Samples"  
  
    Set calc = GetObject(monString)  
    MsgBox calc.Add(3, 4)  
    ```  
  
3. Execute o aplicativo Visual Basic ou o script.  
  
    > [!NOTE]
    > O serviço que você está chamando deve expor um ponto de extremidade MEX para que o moniker possa ler os metadados do serviço. Para obter mais informações, confira [Como: Publicar metadados para um serviço usando um arquivo](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)de configuração.  
  
    > [!NOTE]
    > Se o moniker estiver malformado ou se o serviço estiver indisponível, a `GetObject` chamada para retornará um erro dizendo "sintaxe inválida".  Se você receber esse erro, verifique se o moniker que você está usando está correto e se o serviço está disponível.  
  
## <a name="see-also"></a>Consulte também

- [Como: Usar o moniker do serviço Windows Communication Foundation sem registro](../../../../docs/framework/wcf/feature-details/use-the-wcf-service-moniker-without-registration.md)
- [Como: Usar um moniker de serviço com contratos WSDL](../../../../docs/framework/wcf/feature-details/how-to-use-a-service-moniker-with-wsdl-contracts.md)
