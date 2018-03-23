---
title: Como configurar um cliente básico do Windows Communication Foundation
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- WCF clients [WCF], configuring
ms.assetid: d067b86d-afb0-47bf-94f6-45180a3d8d78
caps.latest.revision: ''
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f23918031c6cc8cd6509d7b7c079b8df050bbb08
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/23/2018
---
# <a name="how-to-configure-a-basic-windows-communication-foundation-client"></a>Como configurar um cliente básico do Windows Communication Foundation
Este é o quinto de seis tarefas necessárias para criar um basic [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] aplicativo. Para obter uma visão geral de todos os seis das tarefas, consulte o [Tutorial de Introdução](../../../docs/framework/wcf/getting-started-tutorial.md) tópico.  
  
 Este tópico disuccess o arquivo de configuração de cliente que foi gerado usando a funcionalidade Adicionar referência de serviço do [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] ou [Ferramenta Utilitária de metadados ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). Configurando o cliente consiste em especificar o ponto de extremidade que o cliente usa para acessar o serviço. Um ponto de extremidade tem um endereço, uma ligação e um contrato, e cada um deles deve ser especificada no processo de configuração do cliente.  
  
### <a name="to-configure-a-windows-communication-foundation-client"></a>Para configurar um cliente Windows Communication Foundation  
  
1.  Abra o arquivo de configuração gerado (App. config) do projeto GettingStartedClient. O exemplo a seguir é um modo de exibição do arquivo de configuração gerado. Sob o [ \<System. ServiceModel >](../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) seção, localize o [ \<ponto de extremidade >](http://msdn.microsoft.com/library/13aa23b7-2f08-4add-8dbf-a99f8127c017) elemento.  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
        <startup>   
          <!-- specifies the version of WCF to use-->  
            <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.5,Profile=Client" />  
        </startup>  
        <system.serviceModel>  
            <bindings>  
                <!-- Uses wsHttpBinding-->  
                <wsHttpBinding>  
                    <binding name="WSHttpBinding_ICalculator" />  
                </wsHttpBinding>  
            </bindings>  
            <client>  
                <!-- specifies the endpoint to use when calling the service -->  
                <endpoint address="http://localhost:8000/ServiceModelSamples/Service/CalculatorService"  
                    binding="wsHttpBinding" bindingConfiguration="WSHttpBinding_ICalculator"  
                    contract="ServiceReference1.ICalculator" name="WSHttpBinding_ICalculator">  
                    <identity>  
                        <userPrincipalName value="migree@redmond.corp.microsoft.com" />  
                    </identity>  
                </endpoint>  
            </client>  
        </system.serviceModel>  
    </configuration>   
    ```  
  
     Este exemplo configura o ponto de extremidade que o cliente usa para acessar o serviço que está localizado no seguinte endereço: http://localhost:8000/ServiceModelSamples/serviço/CalculatorService  
  
     O elemento de ponto de extremidade Especifica que o `ServiceReference1.ICalculator` contrato de serviço é usado para comunicação entre o cliente do WCF e o serviço. O canal WCF está configurado com o sistema fornecido <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`>. Esse contrato foi gerado por meio de adicionar referência de serviço no Visual Studio. É essencialmente uma cópia do contrato que foi definido no projeto GettingStartedLib. O <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`> associação especifica HTTP como o transporte, segurança interoperável e outros detalhes de configuração.  
  
2.  [!INCLUDE[crabout](../../../includes/crabout-md.md)] como usar o cliente gerado com essa configuração, consulte [como: usar um cliente](../../../docs/framework/wcf/how-to-use-a-wcf-client.md).  
  
## <a name="see-also"></a>Consulte também  
 [Usando associações para configurar serviços e clientes](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [Ferramenta de utilitário de metadados ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)  
 [Como criar um cliente](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)  
 [Introdução](../../../docs/framework/wcf/samples/getting-started-sample.md)  
 [Auto-hospedagem](../../../docs/framework/wcf/samples/self-host.md)
