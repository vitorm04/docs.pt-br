---
title: 'Como: usar um moniker de serviço com contratos de intercâmbio de metadados'
ms.date: 03/30/2017
ms.assetid: c41a07e5-cb9d-45d6-9ea4-34511e227faf
ms.openlocfilehash: 367cbd4a2bfbde3d4ab0a74eeeaf5d5f5662ec27
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61972894"
---
# <a name="how-to-use-a-service-moniker-with-metadata-exchange-contracts"></a>Como: usar um moniker de serviço com contratos de intercâmbio de metadados
Após desenvolver alguns novos serviços do WCF, você pode decidir o que você deseja ser capaz de chamar esses serviços de um script ou um aplicativo Visual Basic 6.0. Um método seria gerar um assembly de cliente do WCF, registre o assembly com, instale o assembly no GAC e, em seguida, referenciar os tipos COM seu código do Visual Basic. Quando você distribui o aplicativo, você precisará distribuir o assembly de cliente WCF também. O usuário, em seguida, será preciso registrar o assembly de cliente do WCF com e colocá-lo no GAC. Interoperabilidade de COM do WCF também permite que você faça as mesmas chamadas de serviço sem depender de um assembly de cliente do WCF. O WCF moniker permite que você chame qualquer serviço WCF em qualquer linguagem compatível COM (Visual Basic, VBScript, Visual Basic for Applications (VBA) e assim por diante), especificando um ponto de extremidade do exchange (Mex) de metadados URI que o moniker de serviço usa para extrair o tipo informações sobre o serviço. Este tópico descreve como chamar o exemplo de Introdução ao WCF usando um moniker WCF que especifica um ponto de extremidade de Mex.  
  
> [!NOTE]
>  Os tipos definidos pelo assembly de cliente de WCF, na verdade, nunca são instanciados. O assembly é usado apenas para metadados.  
  
### <a name="using-the-service-moniker-with-a-mex-address"></a>Usando o moniker de serviço com um endereço Mex  
  
1. Criar o exemplo de Introdução e usar o Internet Explorer para navegar até a URL (http://localhost/ServiceModelSamples/Service.svc) para garantir que o serviço está funcionando.  
  
2. Crie um script do Visual Basic ou o aplicativo Visual Basic que contém o código a seguir:  
  
    ```  
    monString = "service:mexaddress=http://localhost/ServiceModelSamples/Service.svc/MEX"  
    monString = monString + ", address=http://localhost/ServiceModelSamples/Service.svc"  
    monString = monString + ", contract=ICalculator, contractNamespace=http://Microsoft.ServiceModel.Samples"  
    monString = monString + ", binding=WSHttpBinding_ICalculator, bindingNamespace=http://Microsoft.ServiceModel.Samples"  
  
    Set calc = GetObject(monString)  
    MsgBox calc.Add(3, 4)  
    ```  
  
3. Execute o script ou aplicativo do Visual Basic.  
  
    > [!NOTE]
    >  O serviço que você está chamando deve expor um ponto de extremidade de Mex para o moniker a ser capaz de ler os metadados do serviço. Para obter mais informações, confira [Como: Publicar metadados para um serviço usando um arquivo de configuração](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md).  
  
    > [!NOTE]
    >  Se o moniker está mal formado ou se o serviço está indisponível, a chamada para `GetObject` retornará um erro informando que "Sintaxe inválida".  Se você receber esse erro, verifique se você estiver usando o identificador de origem está correto e o serviço está disponível.  
  
## <a name="see-also"></a>Consulte também

- [Como: Use o Moniker de serviço do Windows Communication Foundation sem registro](../../../../docs/framework/wcf/feature-details/use-the-wcf-service-moniker-without-registration.md)
- [Como: Usar um Moniker de serviço com contratos WSDL](../../../../docs/framework/wcf/feature-details/how-to-use-a-service-moniker-with-wsdl-contracts.md)
