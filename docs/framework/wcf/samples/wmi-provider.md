---
title: Provedor de WMI
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 462f0db3-f4a4-4a4b-ac26-41fc25c670a4
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: c1b1f923b6673ead42c7c702bd50d253ea06c765
ms.sourcegitcommit: 15316053918995cc1380163a7d7e7edd5c44e6d7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/19/2018
---
# <a name="wmi-provider"></a>Provedor de WMI
Este exemplo demonstra como coletar dados de [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] serviços em tempo de execução usando o provedor do Windows Management Instrumentation (WMI) que é criado em [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. Além disso, este exemplo demonstra como adicionar um objeto WMI definido pelo usuário a um serviço. O exemplo ativa o provedor WMI para o [Introdução](../../../../docs/framework/wcf/samples/getting-started-sample.md) e demonstra como coletar dados do `ICalculator` serviço em tempo de execução.  
  
 O WMI é a implementação da Microsoft a Web-Based Enterprise Management (WBEM) padrão. Para obter mais informações sobre o SDK do WMI, consulte [Windows Management Instrumentation](https://msdn.microsoft.com/library/aa394582.aspx). O WBEM é um padrão da indústria para como aplicativos expõem instrumentação de gerenciamento para as ferramentas de gerenciamento externo.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] implementa um provedor WMI, um componente que expõe instrumentação em tempo de execução por meio de uma interface compatível com o WBEM. Ferramentas de gerenciamento podem se conectar aos serviços por meio da interface em tempo de execução. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] expõe os atributos de serviços, como endereços, associações, comportamentos e ouvintes.  
  
 O provedor WMI interno está ativado no arquivo de configuração do aplicativo. Isso é feito por meio de `wmiProviderEnabled` atributo do [ \<diagnóstico >](../../../../docs/framework/configure-apps/file-schema/wcf/diagnostics.md) no [ \<System. ServiceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) seção, conforme mostrado no exemplo a seguir configuração:  
  
```xml  
<system.serviceModel>  
    ...  
    <diagnostics wmiProviderEnabled="true" />  
    ...  
</system.serviceModel>  
```  
  
 Essa entrada de configuração expõe uma interface WMI. Aplicativos de gerenciamento podem se conectar por meio dessa interface e acessar a instrumentação de gerenciamento do aplicativo.  
  
## <a name="custom-wmi-object"></a>Objeto WMI personalizados  
 Adicionar objetos WMI para um serviço torna possível revelar informações definidas pelo usuário junto com as informações do provedor WMI internas. Isso é feito ao publicar o esquema do serviço WMI usando o aplicativo Installutil.exe. As instruções para fazer isso, juntamente com mais detalhes podem ser encontradas nas instruções de instalação no final do tópico.  
  
## <a name="accessing-wmi-information"></a>Acessando informações de WMI  
 Dados do WMI podem ser acessados de várias maneiras diferentes. A Microsoft fornece as APIs do WMI para scripts, [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] aplicativos, aplicativos C++ e o [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] (http://msdn.microsoft.com/library/default.asp?url=/library/wmisdk/wmi/using_wmi.asp).  
  
 Este exemplo usa dois scripts Java: uma para enumerar os serviços em execução no computador junto com algumas de suas propriedades e a segunda para exibir dados WMI definido pelo usuário. O script abre uma conexão para o provedor WMI, analisa os dados e exibe os dados coletados.  
  
 Iniciar o exemplo para criar uma instância em execução de um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviço. Enquanto o serviço está em execução, execute cada script de Java usando o seguinte comando no prompt de comando:  
  
```  
cscript EnumerateServices.js  
```  
  
 O script acessa a instrumentação contida no serviço e gera a saída a seguir:  
  
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
  
 Em seguida, execute o Script de Java segunda para exibir os dados WMI definido pelo usuário:  
  
```  
cscript EnumerateCustomObjects.js  
```  
  
 O script acessa a instrumentação definido pelo usuário contida nos serviços e produz a seguinte saída:  
  
```  
1 WMIObject(s) found.  
|-PID:           30285bfd-9d66-4c4e-9be2-310499c5cef5  
|-InstanceId:    3839  
|-WMIInfo:       User Defined WMI Information.  
```  
  
 A saída mostra que há um único serviço em execução no computador. O serviço expõe um ponto de extremidade que implementa o `ICalculator` contrato. As configurações do comportamento e associação são implementadas pelo ponto de extremidade são listadas como a soma dos elementos individuais da pilha de mensagens.  
  
 WMI não está limitado a exposição a instrumentação de gerenciamento do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] infraestrutura. O aplicativo pode expor seus próprios itens de dados específicos de domínio por meio do mesmo mecanismo. O WMI é um mecanismo unificado para inspeção e controle de um serviço Web.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1.  Certifique-se de que você executou o [único procedimento de instalação para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Para compilar o c# ou Visual Basic .NET edição da solução, siga as instruções em [compilar os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Publica o esquema do serviços ao WMI, executando o InstallUtil.exe (os locais padrão de InstallUtil.exe é "% WINDIR%\Microsoft.NET\Framework\v4.0.30319") no arquivo service.dll no diretório de hospedagem. Esta etapa só precisa ser executado quando as alterações foram feitas para o arquivo service.dll. Para obter mais informações, consulte fornecendo informações de gerenciamento por aplicativos de instrumentação em: http://msdn2.microsoft.com/library/ms186147.aspx na seção "Como para: publicar o esquema para WMI para um instrumentado aplicativo".  
  
4.  Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
    > [!NOTE]
    >  Se você instalou [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] após a instalação do ASP.NET, talvez seja necessário executar "%WINDIR%\ Microsoft.Net\Framework\v3.0\Windows comunicação Foundation\servicemodelreg.exe "- r - x para dar permissão à conta ASPNET para publicar objetos WMI.  
  
5.  Exibir dados de exemplo exposto por meio do WMI usando os comandos: `cscript EnumerateServices.js` ou `cscript EnumerateCustomObjects.js`.  
  
> [!IMPORTANT]
>  Os exemplos podem mais ser instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\WMIProvider`  
  
## <a name="see-also"></a>Consulte também  
 [Exemplos de monitoramento do AppFabric](http://go.microsoft.com/fwlink/?LinkId=193959)
