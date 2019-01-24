---
title: Provedor de WMI
ms.date: 03/30/2017
ms.assetid: 462f0db3-f4a4-4a4b-ac26-41fc25c670a4
ms.openlocfilehash: 938eb4fd376c699ddbfedf80f05ef62f81232ca2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54497177"
---
# <a name="wmi-provider"></a>Provedor de WMI
Este exemplo demonstra como coletar dados de serviços do Windows Communication Foundation (WCF) em tempo de execução, usando o provedor Windows Management Instrumentation (WMI) que é incorporado ao WCF. Além disso, este exemplo demonstra como adicionar um objeto WMI definido pelo usuário a um serviço. O exemplo ativa o provedor WMI para o [guia de Introdução](../../../../docs/framework/wcf/samples/getting-started-sample.md) e demonstra como coletar dados do `ICalculator` serviço em tempo de execução.  
  
 O WMI é a implementação da Microsoft do Web-Based Enterprise Management (WBEM) padrão. Para obter mais informações sobre o SDK do WMI, consulte [instrumentação de gerenciamento do Windows](/windows/desktop/WmiSdk/wmi-start-page). O WBEM é um padrão do setor para como os aplicativos expõem instrumentação de gerenciamento para as ferramentas de gerenciamento externo.  
  
 O WCF implementa um provedor WMI, um componente que expõe a instrumentação no tempo de execução por meio de uma interface compatível com a iniciativa WBEM. Ferramentas de gerenciamento podem se conectar aos serviços por meio da interface em tempo de execução. O WCF expõe atributos de serviços, como endereços, associações, comportamentos e ouvintes.  
  
 O provedor WMI interno é ativado no arquivo de configuração do aplicativo. Isso é feito por meio das `wmiProviderEnabled` atributo do [ \<diagnóstico >](../../../../docs/framework/configure-apps/file-schema/wcf/diagnostics.md) no [ \<System. ServiceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) seção, conforme mostrado no exemplo a seguir configuração:  
  
```xml  
<system.serviceModel>  
    ...  
    <diagnostics wmiProviderEnabled="true" />  
    ...  
</system.serviceModel>  
```  
  
 Essa entrada de configuração expõe uma interface WMI. Aplicativos de gerenciamento agora podem se conectar por meio dessa interface e acessar a instrumentação de gerenciamento do aplicativo.  
  
## <a name="custom-wmi-object"></a>Objeto WMI personalizados  
 Adicionar objetos WMI a um serviço torna possível revelar informações definidas pelo usuário, juntamente com as informações do provedor WMI internos. Isso é feito ao publicar o esquema do serviço WMI, usando o aplicativo Installutil.exe. Instruções para fazer isso, juntamente com mais detalhes podem ser encontradas nas instruções de instalação no final do tópico.  
  
## <a name="accessing-wmi-information"></a>Acessando informações de WMI  
 Dados do WMI podem ser acessados de várias maneiras diferentes. A Microsoft fornece as APIs do WMI para scripts, aplicativos do Visual Basic, aplicativos de C++ e o [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] (https://docs.microsoft.com/windows/desktop/wmisdk/using-wmi).  
  
 Este exemplo usa dois scripts de Java: uma para enumerar os serviços em execução no computador junto com algumas das suas propriedades e a segunda para exibir dados WMI definido pelo usuário. O script abre uma conexão para o provedor WMI, analisa os dados e exibe os dados coletados.  
  
 Inicie a amostra para criar uma instância em execução de um serviço WCF. Enquanto o serviço está em execução, execute cada script de Java usando o seguinte comando no prompt de comando:  
  
```  
cscript EnumerateServices.js  
```  
  
 O script acessa a instrumentação contida no serviço e gera a seguinte saída:  
  
```  
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
  
 Em seguida, execute o segundo Script de Java para exibir os dados WMI definido pelo usuário:  
  
```  
cscript EnumerateCustomObjects.js  
```  
  
 O script acessa a instrumentação definida pelo usuário contida nos serviços e produz a seguinte saída:  
  
```  
1 WMIObject(s) found.  
|-PID:           30285bfd-9d66-4c4e-9be2-310499c5cef5  
|-InstanceId:    3839  
|-WMIInfo:       User Defined WMI Information.  
```  
  
 A saída mostra que há um único serviço em execução no computador. O serviço expõe um ponto de extremidade que implementa o `ICalculator` contrato. As configurações do comportamento e a associação que são implementados pelo ponto de extremidade são listados como a soma dos elementos individuais da pilha de mensagens.  
  
 WMI não se limita a exposição a instrumentação de gerenciamento da infraestrutura do WCF. O aplicativo pode expor seus próprios itens de dados específicos do domínio por meio do mesmo mecanismo. O WMI é um mecanismo unificado para inspeção e controle de um serviço Web.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1.  Verifique se você tiver executado o [procedimento de configuração de uso único para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Para compilar a edição em C# ou Visual Basic .NET da solução, siga as instruções em [compilando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Publica o esquema de serviços com o WMI, executando o InstallUtil.exe (os locais padrão de InstallUtil.exe é "% WINDIR%\Microsoft.NET\Framework\v4.0.30319") no arquivo service.dll no diretório de hospedagem. Esta etapa só precisa ser executado quando as alterações foram feitas no arquivo service.dll.
  
4.  Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
    > [!NOTE]
    >  Se você instalou o WCF depois de instalar o ASP.NET, você talvez precise executar "%WINDIR%\ Microsoft.Net\Framework\v3.0\Windows comunicação Foundation\servicemodelreg.exe "- r - x para dar permissão à conta ASPNET para publicar objetos WMI.  
  
5.  Exibir dados de exemplo exibido por meio do WMI usando os comandos: `cscript EnumerateServices.js` ou `cscript EnumerateCustomObjects.js`.  
  
> [!IMPORTANT]
>  Os exemplos podem mais ser instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\WMIProvider`  
  
## <a name="see-also"></a>Consulte também
- [AppFabric que monitora exemplos](https://go.microsoft.com/fwlink/?LinkId=193959)
