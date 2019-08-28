---
title: Bloqueio de segurança PII
ms.date: 03/30/2017
ms.assetid: c44fb338-9527-4dd0-8607-b8787d15acb4
ms.openlocfilehash: f82d3f19a3bf6fc6a5ac038034880dafc03fcce1
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70044792"
---
# <a name="pii-security-lockdown"></a>Bloqueio de segurança PII
Este exemplo demonstra como controlar vários recursos relacionados à segurança de um serviço Windows Communication Foundation (WCF) da seguinte maneira:  
  
- Criptografia de informações confidenciais no arquivo de configuração de um serviço.  
  
- Bloqueando elementos no arquivo de configuração para que os subdiretórios de serviço aninhados não possam substituir as configurações.  
  
- Controle do log de informações de identificação pessoal (PII) em logs de mensagens e rastreamento.  
  
> [!IMPORTANT]
> Os exemplos podem mais ser instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) [!INCLUDE[wf1](../../../../includes/wf1-md.md)] e exemplos. Este exemplo está localizado no seguinte diretório.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\SecurityLockdown`  
  
## <a name="discussion"></a>Discussão  
 Cada um desses recursos pode ser usado separadamente ou em conjunto para controlar aspectos da segurança de um serviço. Esse não é um guia definitivo para proteger um serviço WCF.  
  
 Os arquivos de configuração de .NET Framework podem conter informações confidenciais, como cadeias de conexão para se conectar a bancos de dados. Em cenários hospedados na Web, pode ser desejável criptografar essas informações no arquivo de configuração para um serviço para que os dados contidos no arquivo de configuração sejam resistentes à exibição casual. .NET Framework 2,0 e posteriores têm a capacidade de criptografar partes do arquivo de configuração usando a interface de programação de aplicativo de proteção de dados do Windows (DPAPI) ou o provedor de criptografia RSA. O Aspnet_regiis. exe usando o DPAPI ou RSA pode criptografar partes selecionadas de um arquivo de configuração.  
  
 Em cenários hospedados na Web, é possível ter serviços em subdiretórios de outros serviços. A semântica padrão para determinar os valores de configuração permite que os arquivos de configuração nos diretórios aninhados substituam os valores de configuração no diretório pai. Em determinadas situações, isso pode ser indesejável por vários motivos. A configuração do serviço WCF dá suporte ao bloqueio de valores de configuração para que a configuração aninhada gere exceções quando um serviço aninhado for executado usando valores de configuração substituídos.  
  
 Este exemplo demonstra como controlar o log de PII (informações de identificação pessoal) conhecidas em logs de rastreamento e de mensagens, como nome de usuário e senha. Por padrão, o log de PII conhecidas é desabilitado no entanto, em determinadas situações, o registro em log de PII pode ser importante na depuração de um aplicativo. Este exemplo é baseado na [introdução](../../../../docs/framework/wcf/samples/getting-started-sample.md). Além disso, este exemplo usa rastreamento e log de mensagens. Para obter mais informações, consulte o exemplo de [rastreamento e log de mensagens](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md) .  
  
## <a name="encrypting-configuration-file-elements"></a>Criptografando elementos do arquivo de configuração  
 Para fins de segurança em um ambiente de hospedagem na Web compartilhado, pode ser desejável criptografar determinados elementos de configuração, como cadeias de conexão de banco de dados que podem conter informações confidenciais. Um elemento de configuração pode ser criptografado usando a ferramenta Aspnet_regiis. exe encontrada na pasta .NET Framework, por exemplo,%WINDIR%\Microsoft.NET\Framework\v4.0.20728.  
  
#### <a name="to-encrypt-the-values-in-the-appsettings-section-in-webconfig-for-the-sample"></a>Para criptografar os valores na seção appSettings no Web. config para o exemplo  
  
1. Abra um prompt de comando usando Start-> executar.... Digite e clique em **OK.** `cmd`  
  
2. Navegue até o diretório de .NET Framework atual emitindo o seguinte comando: `cd %WINDIR%\Microsoft.NET\Framework\v4.0.20728`.  
  
3. Criptografe as definições de configuração appSettings na pasta Web. config emitindo o seguinte comando: `aspnet_regiis -pe "appSettings" -app "/servicemodelsamples" -prov "DataProtectionConfigurationProvider"`.  
  
 Mais informações sobre como criptografar seções de arquivos de configuração podem ser encontradas lendo um instruções sobre DPAPI na configuração do ASP.net ([criando aplicativos seguros do ASP.net: Autenticação, autorização e comunicação](https://go.microsoft.com/fwlink/?LinkId=95137)segura) e um "como" no RSA na configuração do ASP.net ([como: Criptografar seções de configuração no ASP.NET 2,0](https://go.microsoft.com/fwlink/?LinkId=95138)usando RSA).  
  
## <a name="locking-configuration-file-elements"></a>Elementos do arquivo de configuração de bloqueio  
 Em cenários hospedados na Web, é possível ter serviços em subdiretórios de serviços. Nessas situações, os valores de configuração para o serviço no subdiretório são calculados examinando os valores em Machine. config e mesclando sucessivamente com quaisquer arquivos Web. config em diretórios pai que se movem para baixo na árvore de diretórios e, por fim, mesclam o Arquivo Web. config no diretório que contém o serviço. O comportamento padrão para a maioria dos elementos de configuração é permitir que os arquivos de configuração em subdiretórios substituam os valores definidos em diretórios pai. Em determinadas situações, pode ser desejável impedir que arquivos de configuração em subdiretórios substituam valores definidos na configuração de diretório pai.  
  
 O .NET Framework fornece uma maneira de Bloquear elementos do arquivo de configuração para que as configurações que substituem elementos de configuração bloqueados lancem exceções em tempo de execução.  
  
 Um elemento de configuração pode ser bloqueado especificando o `lockItem` atributo para um nó no arquivo de configuração, por exemplo, para bloquear o nó CalculatorServiceBehavior no arquivo de configuração para que os serviços de calculadora em arquivos de configuração aninhados Não é possível alterar o comportamento, a configuração a seguir pode ser usada.  
  
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
  
 O bloqueio de elementos de configuração pode ser mais específico. Uma lista de elementos pode ser especificada como o valor para `lockElements` para bloquear um conjunto de elementos dentro de uma coleção de subelementos. Uma lista de atributos pode ser especificada como o valor para `lockAttributes` para bloquear um conjunto de atributos dentro de um elemento. Uma coleção inteira de elementos ou atributos pode ser bloqueada, exceto por uma lista especificada, `lockAllElementsExcept` especificando `lockAllAttributesExcept` os atributos ou em um nó.  
  
## <a name="pii-logging-configuration"></a>Configuração de log de PII  
 O registro em log de PII é controlado por duas opções: uma configuração em todo o computador encontrada em Machine. config que permite que um administrador de computador autorize ou negue o registro em log de PII e uma configuração de aplicativo que permite que um administrador de aplicativo Alterne o registro de PII para cada um fonte em um arquivo Web. config ou app. config.  
  
 A configuração em todo o computador é controlada pela `enableLoggingKnownPii` configuração `true` de `false`ou, no `machineSettings` elemento em Machine. config. Por exemplo, o seguinte permite que os aplicativos ativem o registro em log de PII.  
  
```xml  
<configuration>  
    <system.serviceModel>  
        <machineSettings enableLoggingKnownPii="true" />  
    </system.serviceModel>  
</configuration>  
```  
  
> [!NOTE]
> O arquivo Machine. config tem um local padrão:%WINDIR%\Microsoft.NET\Framework\v2.0.50727\CONFIG.  
  
 Se o `enableLoggingKnownPii` atributo não estiver presente em Machine. config, o registro em log de PII não será permitido.  
  
 Habilitar o log de PII para um aplicativo é feito definindo o `logKnownPii` atributo do elemento de origem como `true` ou `false` no arquivo Web. config ou app. config. Por exemplo, o seguinte habilita o registro em log de PII para log de mensagens e log de rastreamento.  
  
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
  
 Se o `logKnownPii` atributo não for especificado, PII não será registrado.  
  
 PII só será registrado se ambos `enableLoggingKnownPii` for definido como `true`e `logKnownPii` for definido como `true`.  
  
> [!NOTE]
> System. Diagnostics ignora todos os atributos de todas as fontes, exceto o primeiro listado no arquivo de configuração. Adicionar o `logKnownPii` atributo à segunda fonte no arquivo de configuração não tem nenhum efeito.  
  
> [!IMPORTANT]
> Para executar este exemplo envolve a modificação manual de Machine. config. Deve-se ter cuidado ao modificar Machine. config como valores incorretos ou a sintaxe pode impedir a execução de todos os aplicativos .NET Framework.  
  
 Também é possível criptografar os elementos do arquivo de configuração usando DPAPI e RSA. Para obter mais informações, consulte os links a seguir:  
  
- [Criando aplicativos ASP.NET seguros: Autenticação, autorização e comunicação segura](https://go.microsoft.com/fwlink/?LinkId=95137)  
  
- [Como: Criptografar seções de configuração no ASP.NET 2,0 usando RSA](https://go.microsoft.com/fwlink/?LinkId=95138)  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar e executar o exemplo  
  
1. Verifique se você executou o [procedimento de configuração única para os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Edite Machine. config para definir `enableLoggingKnownPii` o atributo `true`como, adicionando os nós pai, se necessário.  
  
3. Para compilar a C# edição do ou Visual Basic .NET da solução, siga as instruções em [criando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4. Para executar o exemplo em uma configuração de computador único ou entre computadores, siga as instruções em [executando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
#### <a name="to-clean-up-the-sample"></a>Para limpar o exemplo  
  
1. Edite Machine. config para definir `enableLoggingKnownPii` o atributo `false`como.  
  
## <a name="see-also"></a>Consulte também

- [Exemplos de monitoramento do AppFabric](https://go.microsoft.com/fwlink/?LinkId=193959)
