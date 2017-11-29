---
title: "Como usar um Moniker de serviço com contratos de intercâmbio de metadados"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c41a07e5-cb9d-45d6-9ea4-34511e227faf
caps.latest.revision: "11"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: ed6ce9b87a5e2d8945a57110c02cce8024439f14
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-a-service-moniker-with-metadata-exchange-contracts"></a>Como usar um Moniker de serviço com contratos de intercâmbio de metadados
Depois de desenvolver algumas novas [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services, você pode decidir que deseja ser capaz de chamar esses serviços de um script ou um aplicativo do Visual Basic 6.0. Um método seria gerar um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] assembly de cliente, registre o assembly com, instalar o assembly no GAC e faça referência os tipos COM o código do Visual Basic. Quando você distribui o aplicativo, você precisa distribuir o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] assembly cliente também. O usuário terá, em seguida, registre o assembly de cliente do WCF com e colocá-lo no GAC. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]Interoperabilidade COM também permite que você faça o mesmo serviço chama sem depender de um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] assembly cliente. O [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] moniker permite que você possa chamar qualquer [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviço em qualquer linguagem compatível COM o com (Visual Basic, VBScript, Visual Basic for Applications (VBA) e assim por diante), especificando um ponto de extremidade do exchange (Mex) de metadados URI que usa o moniker de serviço para extrair informações de tipo sobre o serviço. Este tópico descreve como chamar o guia de Introdução [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] de exemplo usando um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] moniker que especifica um ponto de extremidade Mex.  
  
> [!NOTE]
>  Os tipos definidos pelo [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] assembly cliente nunca são instanciados. O assembly é usado apenas para metadados.  
  
### <a name="using-the-service-moniker-with-a-mex-address"></a>Usando o moniker de serviço com um endereço Mex  
  
1.  Criar o exemplo de Introdução e usar o Internet Explorer para navegar até a URL (http://localhost/ServiceModelSamples/Service.svc) para garantir que o serviço está funcionando.  
  
2.  Crie um script do Visual Basic ou o aplicativo do Visual Basic que contém o código a seguir:  
  
    ```  
    monString = "service:mexaddress=http://localhost/ServiceModelSamples/Service.svc/MEX"  
    monString = monString + ", address=http://localhost/ServiceModelSamples/Service.svc"  
    monString = monString + ", contract=ICalculator, contractNamespace=http://Microsoft.ServiceModel.Samples"  
    monString = monString + ", binding=WSHttpBinding_ICalculator, bindingNamespace=http://Microsoft.ServiceModel.Samples"  
  
    Set calc = GetObject(monString)  
    MsgBox calc.Add(3, 4)  
    ```  
  
3.  Execute o script ou aplicativo do Visual Basic.  
  
    > [!NOTE]
    >  O serviço de chamada deve expor um ponto de extremidade Mex para o moniker para ser capaz de ler os metadados do serviço. Para obter mais informações, consulte [como: publicar metadados para um serviço usando um arquivo de configuração](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md).  
  
    > [!NOTE]
    >  Se o identificador de origem está malformado ou se o serviço está indisponível, a chamada para `GetObject` retornará um erro dizendo "Sintaxe inválida".  Se você receber esse erro, verifique se você estiver usando o identificador de origem está correto e o serviço está disponível.  
  
## <a name="see-also"></a>Consulte também  
 [Como: usar o Moniker de serviço do Windows Communication Foundation sem registro](../../../../docs/framework/wcf/feature-details/use-the-wcf-service-moniker-without-registration.md)  
 [Como: usar um Moniker de serviço com contratos WSDL](../../../../docs/framework/wcf/feature-details/how-to-use-a-service-moniker-with-wsdl-contracts.md)
