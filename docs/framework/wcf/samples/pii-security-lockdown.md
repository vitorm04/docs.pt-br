---
title: Bloqueio de segurança PII
ms.date: 03/30/2017
ms.assetid: c44fb338-9527-4dd0-8607-b8787d15acb4
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: ec8af8c7df9335774b1f3953f88c2aad438963b6
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2018
---
# <a name="pii-security-lockdown"></a>Bloqueio de segurança PII
Este exemplo demonstra como controlar vários recursos relacionados à segurança de um serviço do Windows Communication Foundation (WCF) por:  
  
-   Criptografar informações confidenciais no arquivo de configuração do serviço.  
  
-   Bloqueio de elementos no arquivo de configuração para que aninhados subdiretórios de serviço não é possível substituir as configurações.  
  
-   Controlando o registro em log da identificação informações pessoal (PII) em logs de rastreamento e a mensagem.  
  
> [!IMPORTANT]
>  Os exemplos podem mais ser instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\SecurityLockdown`  
  
## <a name="discussion"></a>Discussão  
 Cada um desses recursos pode ser usadas separadamente ou em conjunto controle aspectos de segurança do serviço. Isso não é um guia definitivo para proteger um serviço WCF.  
  
 Os arquivos de configuração do .NET Framework podem conter informações confidenciais, como cadeias de caracteres de conexão para se conectar aos bancos de dados. Em cenários compartilhados hospedado na Web, pode ser desejável para criptografar essas informações no arquivo de configuração para um serviço de forma que os dados contidos no arquivo de configuração são resistentes a visualização casual. .NET framework 2.0 e posteriores tem a capacidade de criptografar partes do arquivo de configuração usando o DPAPI (interface) ou o provedor de criptografia RSA de programação de aplicativo de proteção de dados do Windows. O aspnet_regiis.exe usando a DPAPI ou RSA pode criptografar partes específicas de um arquivo de configuração.  
  
 Em cenários hospedado na Web, é possível ter serviços em subdiretórios de outros serviços. O padrão a semântico para determinar os valores de configuração permite que os arquivos de configuração nos diretórios aninhados para substituir os valores de configuração no diretório pai. Em determinadas situações, isso pode ser indesejável para uma variedade de razões. WCF serviço configuração suporta o bloqueio de valores de configuração para que aninhados configuração gera exceções quando um serviço aninhado é executado usando substituído valores de configuração.  
  
 Este exemplo demonstra como controlar o registro em log de conhecidos identificação informações pessoal (PII) em logs de rastreamento e a mensagem, como nome de usuário e senha. Por padrão, o log de PII conhecido está desabilitado no entanto, em certas situações o log de PII pode ser importante na depuração de um aplicativo. Este exemplo se baseia o [Introdução](../../../../docs/framework/wcf/samples/getting-started-sample.md). Além disso, este exemplo usa o rastreamento e o registro de mensagem. Para obter mais informações, consulte o [rastreamento e registro em log de mensagem](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md) exemplo.  
  
## <a name="encrypting-configuration-file-elements"></a>Elementos do arquivo de configuração de criptografia  
 Para fins de segurança em um ambiente compartilhado de hospedagem na Web, pode ser desejável para criptografar determinados elementos de configuração, como cadeias de caracteres de conexão de banco de dados que podem conter informações confidenciais. Um elemento de configuração pode ser criptografado usando a ferramenta aspnet_regiis.exe encontrada na pasta do .NET Framework, por exemplo, % WINDIR%\Micrsoft.NET\Framework\v4.0.20728.  
  
#### <a name="to-encrypt-the-values-in-the-appsettings-section-in-webconfig-for-the-sample"></a>Para criptografar os valores na seção appSettings no Web. config para o exemplo  
  
1.  Abra um prompt de comando usando Iniciar -> Executar... Digite `cmd` e clique em **Okey**.  
  
2.  Navegue até o diretório do .NET Framework atual emitindo o comando a seguir: `cd %WINDIR%\Microsoft.NET\Framework\v4.0.20728`.  
  
3.  Criptografar as definições de configuração appSettings na pasta de Web. config, emitindo o comando a seguir: `aspnet_regiis -pe "appSettings" -app "/servicemodelsamples" -prov "DataProtectionConfigurationProvider"`.  
  
 Para obter mais informações sobre como criptografar seções de arquivos de configuração podem ser encontradas lendo um como DPAPI na configuração do ASP.NET ([Building Secure ASP.NET Applications: autenticação, autorização e comunicação segura](http://go.microsoft.com/fwlink/?LinkId=95137)) e um em RSA na configuração do ASP.NET ([How To: criptografar seções de configuração no ASP.NET 2.0 usando RSA](http://go.microsoft.com/fwlink/?LinkId=95138)).  
  
## <a name="locking-configuration-file-elements"></a>Elementos travamento do arquivo de configuração  
 Em cenários de hospedado na Web, é possível ter serviços em subdiretórios de serviços. Nessas situações, os valores de configuração para o serviço no subdiretório são calculados examinando os valores em Machine. config e mesclagem sucessivamente com todos os arquivos Web. config em diretórios pai mover para baixo na árvore do diretório e, finalmente, mesclando os Arquivo Web. config no diretório que contém o serviço. É o comportamento padrão para a maioria dos elementos de configuração Permitir que os arquivos de configuração em subdiretórios para substituir os valores definidos nos diretórios pai. Em determinadas situações pode ser desejável para impedir que arquivos de configuração em subdiretórios substituindo valores definidos na configuração do diretório pai.  
  
 O .NET Framework fornece uma maneira de bloquear elementos do arquivo de configuração para que as configurações que substituem elementos de configuração bloqueada lançam exceções de tempo de execução.  
  
 Um elemento de configuração pode ser bloqueado, especificando o `lockItem` de atributo para um nó no arquivo de configuração, por exemplo, para bloquear o nó CalculatorServiceBehavior no arquivo de configuração para que os serviços de cálculo no aninhados arquivos de configuração não é possível alterar o comportamento, a configuração a seguir pode ser usado.  
  
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
  
 Bloqueio de elementos de configuração pode ser mais específico. Uma lista de elementos pode ser especificada como o valor para o `lockElements` para bloquear um conjunto de elementos em uma coleção de subelementos. Uma lista de atributos pode ser especificada como o valor para o `lockAttributes` para bloquear um conjunto de atributos dentro de um elemento. Uma coleção inteira de elementos ou atributos pode ser bloqueada, exceto uma lista especificada, especificando o `lockAllElementsExcept` ou `lockAllAttributesExcept` atributos em um nó.  
  
## <a name="pii-logging-configuration"></a>Configuração de log de PII  
 Log de PII é controlado por duas opções: uma configuração de todo o computador encontrada em Machine. config que permite que um administrador do computador permitir ou negar o log de informações de identificação pessoal e uma configuração de aplicativo que permite que um administrador de aplicativo ativar o log de PII para cada fonte em um arquivo App. config ou Web. config.  
  
 A configuração de todo o computador é controlada pela configuração `enableLoggingKnownPii` para `true` ou `false`, além de `machineSettings` elemento em Machine. config. Por exemplo, o exemplo a seguir permite que aplicativos ativar o log de PII.  
  
```xml  
<configuration>  
    <system.serviceModel>  
        <machineSettings enableLoggingKnownPii="true" />  
    </system.serviceModel>  
</configuration>  
```  
  
> [!NOTE]
>  O arquivo Machine. config tem um local padrão: % WINDIR%\Microsoft.NET\Framework\v2.0.50727\CONFIG.  
  
 Se o `enableLoggingKnownPii` atributo não estiver presente em Machine. config, o log de PII não é permitido.  
  
 Habilitar o log de PII para um aplicativo é feito definindo o `logKnownPii` atributo do elemento de origem para `true` ou `false` no arquivo Web. config ou App. config. Por exemplo, a seguir habilita o log de PII para log de mensagens e logs de rastreamento.  
  
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
  
 Se o `logKnownPii` atributo não for especificado, em seguida, informações de identificação pessoal não está conectada.  
  
 Informações de identificação pessoal são registradas apenas se os dois `enableLoggingKnownPii` é definido como `true`, e `logKnownPii` é definido como `true`.  
  
> [!NOTE]
>  System. Diagnostics ignora todos os atributos em todas as fontes, exceto o primeiro listados no arquivo de configuração. Adicionando o `logKnownPii` atributo para a segunda fonte no arquivo de configuração não tem nenhum efeito.  
  
> [!IMPORTANT]
>  Para executar esse exemplo envolve a modificação manual de Machine. config. Deve-se ter cuidado ao modificar o Machine. config como valores incorretos ou sintaxe pode impedir que todos os aplicativos do .NET Framework em execução.  
  
 Também é possível criptografar os elementos do arquivo de configuração usando DPAPI e RSA. Para obter mais informações, consulte os links a seguir:  
  
-   [Criando aplicativos do ASP.NET seguros: Autenticação, autorização e comunicação segura](http://go.microsoft.com/fwlink/?LinkId=95137)  
  
-   [Como: Criptografar seções de configuração no ASP.NET 2.0 usando o RSA](http://go.microsoft.com/fwlink/?LinkId=95138)  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar e executar o exemplo  
  
1.  Certifique-se de que você executou o [único procedimento de instalação para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Editar o Machine. config para definir o `enableLoggingKnownPii` atributo `true`, adicionar os nós pai, se necessário.  
  
3.  Para compilar o c# ou Visual Basic .NET edição da solução, siga as instruções em [compilar os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4.  Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
#### <a name="to-clean-up-the-sample"></a>Para limpar o exemplo  
  
1.  Editar o Machine. config para definir o `enableLoggingKnownPii` atributo `false`.  
  
## <a name="see-also"></a>Consulte também  
 [Exemplos de monitoramento do AppFabric](http://go.microsoft.com/fwlink/?LinkId=193959)
