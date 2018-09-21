---
title: Como configurar um cliente básico do Windows Communication Foundation
ms.date: 09/14/2018
helpviewer_keywords:
- WCF clients [WCF], configuring
ms.assetid: d067b86d-afb0-47bf-94f6-45180a3d8d78
ms.openlocfilehash: 3f267edf87711de8a5969e3e0b577648008c5a75
ms.sourcegitcommit: dfb2a100cfb4d3902c042f17b3204f49bc7635e7
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/21/2018
ms.locfileid: "46524857"
---
# <a name="how-to-configure-a-basic-windows-communication-foundation-client"></a>Como configurar um cliente básico do Windows Communication Foundation

Esse é o quinto de seis tarefas necessárias para criar um aplicativo básico do Windows Communication Foundation (WCF). Para obter uma visão geral de todas as seis tarefas, confira o tópico [Tutorial de introdução](../../../docs/framework/wcf/getting-started-tutorial.md).

Este tópico discute o arquivo de configuração de cliente que foi gerado usando o **adicionar referência de serviço** funcionalidade do Visual Studio ou o [ferramenta Utilitário de metadados ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). Configurando o cliente consiste em especificar o ponto de extremidade que o cliente usa para acessar o serviço. Um ponto de extremidade tem um endereço, uma ligação e um contrato, e cada um deles deve ser especificada no processo de configuração do cliente.

## <a name="configure-a-windows-communication-foundation-client"></a>Configurar um cliente do Windows Communication Foundation

Abra o arquivo de configuração gerado (App. config) do projeto GettingStartedClient. O exemplo a seguir é um modo de exibição do arquivo de configuração gerado. Sob o [ \<System. ServiceModel >](../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) seção, localize o [ \<ponto de extremidade >](https://msdn.microsoft.com/library/13aa23b7-2f08-4add-8dbf-a99f8127c017) elemento.

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

Este exemplo configura o ponto de extremidade que o cliente usa para acessar o serviço que está localizado no seguinte endereço: `http://localhost:8000/ServiceModelSamples/Service/CalculatorService`.

O elemento de ponto de extremidade Especifica que o `ServiceReference1.ICalculator` contrato de serviço é usado para comunicação entre o cliente do WCF e o serviço. O canal do WCF é configurado com o sistema forneceu <xref:System.ServiceModel.WSHttpBinding>. Esse contrato foi gerado usando **adicionar referência de serviço** no Visual Studio. Ele é essencialmente uma cópia do contrato que foi definido no projeto GettingStartedLib. O <xref:System.ServiceModel.WSHttpBinding> associação especifica HTTP como o transporte, segurança interoperável e outros detalhes de configuração.

Para obter mais informações sobre como usar o cliente gerado com essa configuração, consulte [como: usar um cliente](../../../docs/framework/wcf/how-to-use-a-wcf-client.md).

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Como: usar um cliente WCF](../../../docs/framework/wcf/how-to-use-a-wcf-client.md)

## <a name="see-also"></a>Consulte também

- [Usando associações para configurar serviços e clientes](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [Ferramenta de utilitário de metadados ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
- [Como criar um cliente](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)
- [Introdução](../../../docs/framework/wcf/samples/getting-started-sample.md)
- [Auto-hospedagem](../../../docs/framework/wcf/samples/self-host.md)