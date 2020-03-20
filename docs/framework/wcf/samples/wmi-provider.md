---
title: Provedor WMI
ms.date: 03/30/2017
ms.assetid: 462f0db3-f4a4-4a4b-ac26-41fc25c670a4
ms.openlocfilehash: 04fdbb7efcae6fdbb78f467352e6106ac5218799
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183195"
---
# <a name="wmi-provider"></a>Provedor WMI
Esta amostra demonstra como coletar dados dos serviços da Windows Communication Foundation (WCF) em tempo de execução usando o provedor de Instrumentação de Gerenciamento do Windows (WMI) que é incorporado ao WCF. Além disso, esta amostra demonstra como adicionar um objeto WMI definido pelo usuário a um serviço. A amostra ativa o provedor WMI para o [Getting](../../../../docs/framework/wcf/samples/getting-started-sample.md) Started `ICalculator` e demonstra como coletar dados do serviço em tempo de execução.  
  
 O WMI é a implementação da Microsoft do padrão WBEM (Web-Based Enterprise Management, gerenciamento de empresas baseado na Web). Para obter mais informações sobre o WMI SDK, consulte [A Instrumentação de Gerenciamento do Windows](/windows/desktop/WmiSdk/wmi-start-page). O WBEM é um padrão do setor para como as aplicações expõem a instrumentação de gerenciamento a ferramentas de gestão externa.  
  
 O WCF implementa um provedor WMI, um componente que expõe a instrumentação em tempo de execução através de uma interface compatível com WBEM. As ferramentas de gerenciamento podem se conectar aos serviços através da interface em tempo de execução. O WCF expõe atributos de serviços como endereços, vinculações, comportamentos e ouvintes.  
  
 O provedor WMI incorporado é ativado no arquivo de configuração do aplicativo. Isso é feito `wmiProviderEnabled` através do atributo do [ \<>de diagnóstico](../../../../docs/framework/configure-apps/file-schema/wcf/diagnostics.md) na seção [ \<system.serviceModel>,](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) conforme mostrado na seguinte configuração de amostra:  
  
```xml  
<system.serviceModel>  
    ...  
    <diagnostics wmiProviderEnabled="true" />  
    ...  
</system.serviceModel>  
```  
  
 Esta entrada de configuração expõe uma interface WMI. Os aplicativos de gerenciamento agora podem se conectar através desta interface e acessar a instrumentação de gerenciamento do aplicativo.  
  
## <a name="custom-wmi-object"></a>Objeto WMI personalizado  
 A adição de objetos WMI a um serviço permite revelar informações definidas pelo usuário, juntamente com as informações incorporadas do provedor WMI. Isso é feito publicando o esquema do serviço para o WMI usando o aplicativo Installutil.exe. Instruções para isso, juntamente com mais detalhes podem ser encontradas nas instruções de configuração no final do tópico.  
  
## <a name="accessing-wmi-information"></a>Acessando as informações do WMI  

Os dados WMI podem ser acessados de muitas maneiras diferentes. A Microsoft fornece APIs WMI para scripts, aplicativos Visual Basic, aplicativos C++ e o .NET Framework. Para obter mais informações, consulte [Usando WMI](/windows/desktop/wmisdk/using-wmi).
  
 Esta amostra usa dois scripts Java: um para enumerar serviços em execução no computador, juntamente com algumas de suas propriedades e o segundo para visualizar dados WMI definidos pelo usuário. O script abre uma conexão com o provedor WMI, analisa dados e exibe os dados coletados.  
  
 Inicie a amostra para criar uma instância em execução de um serviço WCF. Enquanto o serviço estiver em execução, execute cada script Java usando o seguinte comando no prompt de comando:  
  
```console  
cscript EnumerateServices.js  
```  
  
 O script acessa a instrumentação contida no serviço e produz a seguinte saída:  
  
```console  
Microsoft (R) Windows Script Host Version 5.6  
Copyright © Microsoft Corporation 1996-2001. All rights reserved.  
  
1 service(s) found.  
|-PID:           5776  
|-DistinguishedName:  CalculatorService@http://localhost/ServiceModelSamples/service.svc  
|-Endpoints:     1 endpoints  
  |-CalculatorService.ICalculator@http://localhost/ServiceModelSamples/service.svc  
    |-Address:                        http://localhost/ServiceModelSamples/service.svc  
    |-CounterInstanceName:  
    |-AddressHeaders:                 0  
    |-ContractType:                   Contract.Name='ICalculator'  
    |-BindingElements:                4 bindings  
      |-BindingElements[0]  
        |-Type:                       TransactionFlowBindingElement  
      |-BindingElements[1]  
        |-Type:                       SymmetricSecurityBindingElement  
      |-BindingElements[2]  
        |-Type:                       TextMessageEncodingBindingElement  
        |-MaxReadPoolSize:            64  
        |-MaxWritePoolSize:           16  
      |-BindingElements[3]  
        |-Type:                       HttpTransportBindingElement  
        |-ManualAddressing:           false  
        |-MaxBufferSize:              65536  
        |-AllowCookies:               false  
        |-AuthenticationScheme:       Anonymous  
        |-BypassProxyOnLocal:         false  
        |-HostNameComparisonMode:     StrongWildcard  
        |-ProxyAddress:               null  
        |-ProxyAuthenticationScheme:  Anonymous  
        |-Realm:  
        |-TransferMode:               Buffered  
        |-UseDefaultWebProxy:         true  
|-Behaviors:     5 behaviors  
      |-Behavior[0]  
      |-Type:                       ServiceBehaviorAttribute  
        |-AddressFilterMode:               Exact  
        |-AutomaticSessionShutdown:        true  
        |-ConcurrencyMode:                 Single  
        |-IncludeExceptionDetailInFaults:  false  
        |-InstanceContextMode:             PerSession  
        |-TransactionIsolationLevel:       Unspecified  
        |-TransactionTimeout:              null  
        |-ValidateMustUnderstand:          true  
      |-Behavior[1]  
      |-Type:                       AspNetCompatibilityRequirementsAttribute  
      |-Behavior[2]  
      |-Type:                       ServiceDebugBehavior  
      |-Behavior[3]  
      |-Type:                       ServiceAuthorizationBehavior  
      |-Behavior[4]  
      |-Type:                       Behavior  
```  
  
 Em seguida, execute o segundo Script Java para exibir os dados WMI definidos pelo usuário:  
  
```console  
cscript EnumerateCustomObjects.js  
```  
  
 O script acessa a instrumentação definida pelo usuário contida nos serviços e produz a seguinte saída:  
  
```console
1 WMIObject(s) found.  
|-PID:           30285bfd-9d66-4c4e-9be2-310499c5cef5  
|-InstanceId:    3839  
|-WMIInfo:       User Defined WMI Information.  
```  
  
 A saída mostra que há um único serviço em execução no computador. O serviço expõe um ponto final `ICalculator` que implementa o contrato. As configurações do comportamento e da vinculação que são implementadas até o ponto final são listadas como a soma de elementos individuais da pilha de mensagens.  
  
 O WMI não se limita a expor a instrumentação gerencial da infra-estrutura do WCF. O aplicativo pode expor seus próprios itens de dados específicos de domínio através do mesmo mecanismo. WMI é um mecanismo unificado para inspeção e controle de um serviço Web.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1. Certifique-se de ter realizado o [procedimento de configuração única para as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Para construir a edição C# ou Visual Basic .NET da solução, siga as instruções em [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Publique o esquema de serviços para o WMI executando o InstallUtil.exe (os locais padrão para InstallUtil.exe é "%WINDIR%\Microsoft.NET\Framework\v4.0.30319") no arquivo service.dll no diretório de hospedagem. Esta etapa só precisa ser executada quando alterações forem feitas no arquivo service.dll.
  
4. Para executar a amostra em uma configuração de computador único ou cruzado, siga as instruções em [Executar as amostras da Fundação](../../../../docs/framework/wcf/samples/running-the-samples.md)de Comunicação do Windows .  
  
    > [!NOTE]
    > Se você instalou o WCF depois de instalar ASP.NET, talvez seja necessário executar "%WINDIR%\ Microsoft.Net\Framework\v3.0\Windows Communication Foundation\servicemodelreg.exe " -r -x para dar à conta ASPNET permissão para publicar objetos WMI.  
  
5. Exibir dados da amostra em sipor através `cscript EnumerateServices.js` do `cscript EnumerateCustomObjects.js`WMI usando os comandos: ou .  
  
> [!IMPORTANT]
> Os exemplos podem mais ser instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation). Este exemplo está localizado no seguinte diretório.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\WMIProvider`  
  
## <a name="see-also"></a>Confira também

- [AppFabric que monitora Exemplos](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))
