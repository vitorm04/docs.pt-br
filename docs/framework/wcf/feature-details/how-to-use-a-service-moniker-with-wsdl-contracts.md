---
title: "Como usar um Moniker de serviço com contratos WSDL"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a88d9650-bb50-4f48-8c85-12f5ce98a83a
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 9d98fb82984fec4acbb8b95d4bc4667468804ff9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-a-service-moniker-with-wsdl-contracts"></a>Como usar um Moniker de serviço com contratos WSDL
Há situações quando desejar que um cliente totalmente independente de interoperabilidade COM. O serviço que você deseja chamar não pode expor um ponto de extremidade MEX e o cliente do WCF com que dll não pode ser registrado para interoperabilidade. Nesses casos, você pode criar um arquivo WSDL que descreve o serviço e passá-lo para o moniker de serviço do WCF. Este tópico descreve como chamar o exemplo de obter WCF iniciado usando um moniker de WCF WSDL.  
  
### <a name="using-the-wsdl-service-moniker"></a>Usando o moniker de serviço WSDL  
  
1.  Abrir e criar a solução de exemplo GettingStarted.  
  
2.  Abra o Internet Explorer e navegue até http://localhost/ServiceModelSamples/Service.svc para certificar-se de que o serviço está funcionando.  
  
3.  No arquivo Service.cs, adicione o seguinte atributo na classe CalculatorService:  
  
     [!code-csharp[S_WSDL_Client#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wsdl_client/cs/service.cs#0)]  
  
4.  Adicione um namespace de associação para o serviço App. config:  
  
  
  
5.  Crie um arquivo WSDL para o aplicativo leia. Porque os namespaces foram adicionados nas etapas 3 e 4, você pode usar o Internet Explorer para consultar a descrição inteira do WSDL do serviço, navegando para http://localhost/ServiceModelSamples/Service.svc?wsdl. Em seguida, você pode salvar o arquivo do Internet Explorer como serviceWSDL.xml. Se você não especificar os namespaces nas etapas 3 e 4, o documento WSDL retornado das consultas URL anterior não será concluída WSDL. O documento WSDL retornado incluirá várias instruções de importação que importar outros documentos WSDL. Você precisará passar por cada instrução de importação e criar o documento WSDL completo, combinando WSDL retornada do serviço com o WSDL importado.  
  
6.  Abra o Visual Basic 6.0 e crie um novo arquivo .exe padrão. Adicione um botão ao formulário e clique duas vezes no botão para adicionar o código a seguir para o manipulador de cliques:  
  
    ```  
    ' Open the WSDL contract file and read it all into the wsdlContract string.  
    Const ForReading = 1  
    Set objFSO = CreateObject("Scripting.FileSystemObject")  
    Set objFile = objFSO.OpenTextFile("c:\serviceWsdl.xml", ForReading)  
    wsdlContract = objFile.ReadAll  
    objFile.Close  
  
    ' Create a string for the service moniker including the content of the WSDL contract file.  
    wsdlMonikerString = "service4:address='http://localhost/ServiceModelSamples/service.svc'"  
    wsdlMonikerString = wsdlMonikerString + ", wsdl='" & wsdlContract & "'"  
    wsdlMonikerString = wsdlMonikerString + ", binding=WSHttpBinding_ICalculator, bindingNamespace='http://Microsoft.ServiceModel.Samples'"  
    wsdlMonikerString = wsdlMonikerString + ", contract=ICalculator, contractNamespace='http://Microsoft.ServiceModel.Samples'"  
  
    ' Create the service moniker object.  
    Set wsdlServiceMoniker = GetObject(wsdlMonikerString)  
  
    ' Call the service operations using the moniker object.  
    MsgBox "WSDL service moniker: 145 - 76.54 = " & wsdlServiceMoniker.Subtract(145, 76.54)  
    ```  
  
    > [!NOTE]
    >  Se o identificador de origem está malformado ou se o serviço está indisponível a chamada para `GetObject` retornará um erro dizendo "Sintaxe inválida".  Se você receber esse erro, verifique se você estiver usando o identificador de origem está correto e o serviço está disponível.  
  
7.  Execute o aplicativo do Visual Basic. Uma caixa de mensagem será exibida com os resultados da chamada Subtract (145, 76.54).  
  
## <a name="see-also"></a>Consulte também  
 [Introdução](../../../../docs/framework/wcf/samples/getting-started-sample.md)  
 [Integração com visão geral de aplicativos COM](../../../../docs/framework/wcf/feature-details/integrating-with-com-applications-overview.md)
