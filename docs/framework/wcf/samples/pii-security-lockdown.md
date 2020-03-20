---
title: Bloqueio de segurança PII
ms.date: 03/30/2017
ms.assetid: c44fb338-9527-4dd0-8607-b8787d15acb4
ms.openlocfilehash: ad4f4a024b04a028b815faedded58713e001cab0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144260"
---
# <a name="pii-security-lockdown"></a>Bloqueio de segurança PII
Esta amostra demonstra como controlar vários recursos relacionados à segurança de um serviço wcf (Windows Communication Foundation) por:  
  
- Criptografando informações confidenciais no arquivo de configuração de um serviço.  
  
- Bloquear elementos no arquivo de configuração para que os subdiretórios de serviço aninhados não possam substituir as configurações.  
  
- Controlando o registro de Informações Identificáveis Pessoais (PII) em registros de rastreamento e mensagens.  
  
> [!IMPORTANT]
> Os exemplos podem mais ser instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation). Este exemplo está localizado no seguinte diretório.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\SecurityLockdown`  
  
## <a name="discussion"></a>Discussão  
 Cada um desses recursos pode ser usado separadamente ou em conjunto para controlar aspectos da segurança de um serviço. Este não é um guia definitivo para garantir um serviço WCF.  
  
 Os arquivos de configuração .NET Framework podem conter informações confidenciais, como strings de conexão para se conectar a bancos de dados. Em cenários compartilhados e hospedados na Web, pode ser desejável criptografar essas informações no arquivo de configuração de um serviço para que os dados contidos no arquivo de configuração sejam resistentes à visualização casual. .NET Framework 2.0 e posteriormente tem a capacidade de criptografar partes do arquivo de configuração usando a interface de programação de aplicativos do Windows Data Protection (DPAPI) ou o provedor de criptografia RSA. O aspnet_regiis.exe usando o DPAPI ou RSA pode criptografar partes selecionadas de um arquivo de configuração.  
  
 Em cenários hospedados na Web é possível ter serviços em subdiretórios de outros serviços. O semântico padrão para determinar valores de configuração permite que arquivos de configuração nos diretórios aninhadas sobreponham os valores de configuração no diretório pai. Em certas situações isso pode ser indesejável por uma variedade de razões. A configuração de serviço WCF suporta o bloqueio de valores de configuração para que a configuração aninhada gere exceções quando um serviço aninhado é executado usando valores de configuração substituídos.  
  
 Esta amostra demonstra como controlar o registro de Informações Pessoais Identificáveis (PII) conhecidas em registros de rastreamento e mensagens, como nome de usuário e senha. Por padrão, o registro de PII conhecido é desativado, porém em certas situações o registro de PII pode ser importante na depuração de um aplicativo. Esta amostra é baseada no [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md). Além disso, esta amostra usa rastreamento e registro de mensagens. Para obter mais informações, consulte a amostra [de Rastreamento e Registro de Mensagens.](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md)  
  
## <a name="encrypting-configuration-file-elements"></a>Criptografando elementos do arquivo de configuração  
 Para fins de segurança em um ambiente compartilhado de hospedagem na Web, pode ser desejável criptografar certos elementos de configuração, como cadeias de conexão de banco de dados que podem conter informações confidenciais. Um elemento de configuração pode ser criptografado usando a ferramenta aspnet_regiis.exe encontrada na pasta .NET Framework Por exemplo, %WINDIR%\Microsoft.NET\Framework\v4.0.20728.  
  
#### <a name="to-encrypt-the-values-in-the-appsettings-section-in-webconfig-for-the-sample"></a>Para criptografar os valores na seção Configurações de aplicativos na Web.config para a amostra  
  
1. Abra um prompt de comando usando Start->Run.... Digite `cmd` e clique em **OK**.  
  
2. Navegue até o diretório atual .NET Framework `cd %WINDIR%\Microsoft.NET\Framework\v4.0.20728`emitindo o seguinte comando: .  
  
3. Criptografe as configurações de configuração de configuração de aplicativos `aspnet_regiis -pe "appSettings" -app "/servicemodelsamples" -prov "DataProtectionConfigurationProvider"`na pasta Web.config emitindo o seguinte comando: .  
  
 Mais informações sobre a criptografia de seções de arquivos de configuração podem ser encontradas lendo um how-to no DPAPI na configuração ASP.NET ([Building Secure ASP.NET Applications: Authentication, Authorization, and Secure Communication](https://docs.microsoft.com/previous-versions/msp-n-p/ff649248(v=pandp.10))) e um how-to on RSA na configuração ASP.NET ([Como: Criptografar seções de configuração em ASP.NET 2.0 Usando RSA](https://docs.microsoft.com/previous-versions/msp-n-p/ff650304(v=pandp.10))).  
  
## <a name="locking-configuration-file-elements"></a>Elementos de arquivo de configuração de bloqueio  
 Em cenários hospedados na Web, é possível ter serviços em subdiretórios de serviços. Nessas situações, os valores de configuração para o serviço no subdiretório são calculados examinando valores em Machine.config e se fundindo sucessivamente com quaisquer arquivos Web.config em diretórios-pai movendo-se para baixo da árvore de diretório e finalmente mesclando o Arquivo Web.config no diretório que contém o serviço. O comportamento padrão para a maioria dos elementos de configuração é permitir que arquivos de configuração em subdiretórios sobreponham os valores definidos nos diretórios pai. Em certas situações, pode ser desejável impedir que arquivos de configuração em subdiretórios sobrepor valores definidos na configuração do diretório pai.  
  
 O .NET Framework fornece uma maneira de bloquear elementos de arquivo de configuração para que configurações que anulam elementos de configuração bloqueados lancem exceções de tempo de execução.  
  
 Um elemento de configuração pode `lockItem` ser bloqueado especificando o atributo para um nó no arquivo de configuração, por exemplo, para bloquear o nó CalculadoraServiceBehavior no arquivo de configuração para que os serviços de calculadora em arquivos de configuração aninhados não possam alterar o comportamento, a configuração a seguir pode ser usada.  
  
```xml  
<configuration>  
   <system.serviceModel>  
      <behaviors>
          <serviceBehaviors>
             <behavior name="CalculatorServiceBehavior" lockItem="true">
               <serviceMetadata httpGetEnabled="True"/>
               <serviceDebug includeExceptionDetailInFaults="False" />
             </behavior>
          </serviceBehaviors>
       </behaviors>
    </system.serviceModel>  
</configuration>  
```  
  
 O bloqueio de elementos de configuração pode ser mais específico. Uma lista de elementos pode ser `lockElements` especificada como o valor para bloquear um conjunto de elementos dentro de uma coleção de subelementos. Uma lista de atributos pode ser `lockAttributes` especificada como o valor para bloquear um conjunto de atributos dentro de um elemento. Uma coleção inteira de elementos ou atributos pode ser `lockAllElementsExcept` bloqueada, exceto por uma lista especificada, especificando ou `lockAllAttributesExcept` atributos em um nó.  
  
## <a name="pii-logging-configuration"></a>Configuração de registro pii  
 O registro de PII é controlado por dois switches: uma configuração em todo o computador encontrada no Machine.config que permite que um administrador de computador permita ou negue o registro de PII e uma configuração de aplicativo que permite que um administrador de aplicativos alterne o registro de PII para cada fonte em um arquivo Web.config ou App.config.  
  
 A configuração em todo `enableLoggingKnownPii` o `true` `false`computador é `machineSettings` controlada por configuração de ou , no elemento em Machine.config. Por exemplo, o seguinte permite que os aplicativos ativem o registro do PII.  
  
```xml  
<configuration>  
    <system.serviceModel>  
        <machineSettings enableLoggingKnownPii="true" />  
    </system.serviceModel>  
</configuration>  
```  
  
> [!NOTE]
> O arquivo Machine.config tem um local padrão: %WINDIR%\Microsoft.NET\Framework\v2.0.50727\CONFIG.  
  
 Se `enableLoggingKnownPii` o atributo não estiver presente no Machine.config, o registro de PII não é permitido.  
  
 A habilitação do registro de PII `logKnownPii` para um aplicativo `true` é `false` feita definindo o atributo do elemento de origem para ou no arquivo Web.config ou App.config. Por exemplo, o seguinte permite o registro de PII para registro de mensagens e registro de rastreamento.  
  
```xml  
<configuration>  
    <system.diagnostics>  
        <sources>  
            <source name="System.ServiceModel.MessageLogging" logKnownPii="true">  
                <listeners>
                ...
                </listeners>  
            </source>  
            <source name="System.ServiceModel" switchValue="Verbose, ActivityTracing">  
            <listeners>  
        ...
            </listeners>  
            </source>  
        </sources>  
    </system.diagnostics>  
</configuration>  
```  
  
 Se `logKnownPii` o atributo não for especificado, o PII não será registrado.  
  
 O PII só é `enableLoggingKnownPii` registrado `true`se `logKnownPii` ambos forem definidos para , e está definido como `true`.  
  
> [!NOTE]
> System.Diagnostics ignora todos os atributos em todas as fontes, exceto o primeiro listado no arquivo de configuração. Adicionar `logKnownPii` o atributo à segunda fonte no arquivo de configuração não tem efeito.  
  
> [!IMPORTANT]
> Para executar esta amostra envolve modificação manual de Machine.config. Deve-se tomar cuidado ao modificar Machine.config, pois valores incorretos ou a sintaxe pode impedir que todos os aplicativos .NET Framework sejam executados.  
  
 Também é possível criptografar elementos de arquivo de configuração usando DPAPI e RSA. Para obter mais informações, consulte os seguintes links:  
  
- [Construindo aplicativos de ASP.NET Seguro: Autenticação, Autorização e Comunicação Segura](https://docs.microsoft.com/previous-versions/msp-n-p/ff649248(v=pandp.10))  
  
- [Como: Criptografar seções de configuração em ASP.NET 2.0 usando rsa](https://docs.microsoft.com/previous-versions/msp-n-p/ff650304(v=pandp.10))  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar e executar o exemplo  
  
1. Certifique-se de que você tenha realizado o [procedimento de configuração única para as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Editar Máquina.configure para `enableLoggingKnownPii` definir `true`o atributo para , adicionando os nós-pai, se necessário.  
  
3. Para construir a edição C# ou Visual Basic .NET da solução, siga as instruções em [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4. Para executar a amostra em uma configuração de computador único ou cruzado, siga as instruções em [Executar as amostras da Fundação](../../../../docs/framework/wcf/samples/running-the-samples.md)de Comunicação do Windows .  
  
#### <a name="to-clean-up-the-sample"></a>Para limpar a amostra  
  
1. Editar Máquina.configure para `enableLoggingKnownPii` definir `false`o atributo para .  
  
## <a name="see-also"></a>Confira também

- [AppFabric que monitora Exemplos](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))
