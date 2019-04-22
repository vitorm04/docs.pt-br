---
title: Compatibilidade da funcionalidade de confiança parcial
ms.date: 03/30/2017
ms.assetid: a36a540b-1606-4e63-88e0-b7c59e0e6ab7
ms.openlocfilehash: b0d9b7bd8bd5f33ca344ea5674d08507ced209f5
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59124560"
---
# <a name="partial-trust-feature-compatibility"></a>Compatibilidade da funcionalidade de confiança parcial
Windows Communication Foundation (WCF) oferece suporte a um subconjunto limitado da funcionalidade quando executados em um ambiente parcialmente confiável. Os recursos com suporte em confiança parcial são projetados em torno de um conjunto específico de cenários, conforme descrito na [suporte para cenários de implantação](../../../../docs/framework/wcf/feature-details/supported-deployment-scenarios.md) tópico.  
  
## <a name="minimum-permission-requirements"></a>Requisitos de permissão mínimos  
 O WCF oferece suporte a um subconjunto de recursos em aplicativos em execução em qualquer um dos seguintes conjuntos de permissões nomeadas padrão:  
  
-   Permissões de confiança médio  
  
-   Permissões da zona da Internet  
  
 A tentativa de usar o WCF em aplicativos parcialmente confiáveis com permissões mais restritivas pode resultar em exceções de segurança em tempo de execução.  
  
## <a name="contracts"></a>Contratos  
 Contratos estão sujeitos às seguintes restrições ao executar em confiança parcial:  
  
-   A classe de serviço que implementa o `[ServiceContract]` interface deve ser `public` e ter um `public` construtor. Se ele define `[OperationContract]` métodos, eles devem ser `public`. Se, em vez disso, ele implementa um `[ServiceContract]` interface, essas implementações de método podem ser explícitas ou `private`, desde que o `[ServiceContract]` interface é `public`.  
  
-   Ao usar o `[ServiceKnownType]` atributo, o método especificado deve ser `public`.  
  
-   `[MessageContract]` classes e seus membros podem ser `public`. Se o `[MessageContract]` classe é definida no assembly do aplicativo pode ser `internal` e ter `internal` membros.  
  
## <a name="system-provided-bindings"></a>Associações fornecidas pelo sistema  
 O <xref:System.ServiceModel.BasicHttpBinding> e <xref:System.ServiceModel.WebHttpBinding> têm suporte total em um ambiente de confiança parcial. O <xref:System.ServiceModel.WSHttpBinding> tem suporte para somente modo de segurança de transporte.  
  
 Associações que usam transportes diferentes de HTTP, como o <xref:System.ServiceModel.NetTcpBinding>, o <xref:System.ServiceModel.NetNamedPipeBinding>, ou o <xref:System.ServiceModel.NetMsmqBinding>, não são suportados quando executados em um ambiente de confiança parcial.  
  
## <a name="custom-bindings"></a>Associações personalizadas  
 Associações personalizadas podem ser criadas e usados em um ambiente de confiança parcial, mas devem seguir as restrições especificadas nesta seção.  
  
### <a name="transports"></a>Transportes  
 Os únicos permitidos são elementos de associação de transporte <xref:System.ServiceModel.Channels.HttpTransportBindingElement> e <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>.  
  
### <a name="encoders"></a>Codificadores  
 Os seguintes codificadores são permitidos:  
  
-   O codificador de texto (<xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>).  
  
-   O codificador binário (<xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>).  
  
-   O codificador de mensagem da Web (<xref:System.ServiceModel.Channels.WebMessageEncodingBindingElement>).  
  
 Não há suporte para os codificadores de mensagem MTOM Transmission Optimization Mechanism ().  
  
### <a name="security"></a>Segurança  
 Os aplicativos parcialmente confiáveis podem usar os recursos de segurança de nível de transporte do WCF para proteger sua comunicação. Não há suporte para a segurança em nível de mensagem. Como configurar uma associação para usar a segurança de nível de mensagem resulta em uma exceção em tempo de execução.  
  
### <a name="unsupported-bindings"></a>Associações sem suporte  
 Não há suporte para associações que usam mensagens confiáveis, transações ou segurança em nível de mensagem.  
  
## <a name="serialization"></a>Serialização  
 Tanto a <xref:System.Runtime.Serialization.DataContractSerializer> e o <xref:System.Xml.Serialization.XmlSerializer> têm suporte em um ambiente de confiança parcial. No entanto, usar o <xref:System.Runtime.Serialization.DataContractSerializer> está sujeito a condições a seguir:  
  
-   Todos os serializável `[DataContract]` os tipos devem ser `public`.  
  
-   Todos os serializável `[DataMember]` campos ou propriedades em um `[DataContract]` tipo deve ser pública e leitura/gravação. A serialização e desserialização dos [readonly](https://go.microsoft.com/fwlink/?LinkID=98854) campos não tem suporte durante a execução do WCF em um aplicativo parcialmente confiável.  
  
-   O  `[Serializable]` /modelo de programação ISerializable não tem suporte em um ambiente de confiança parcial.  
  
-   Tipos conhecidos devem ser especificados no código ou configuração de nível de máquina (Machine. config). Tipos conhecidos não podem ser especificados na configuração de nível de aplicativo por motivos de segurança.  
  
-   Tipos que implementam <xref:System.Runtime.Serialization.IObjectReference> lançar uma exceção em um ambiente parcialmente confiável.  
  
 Consulte a seção de serialização [práticas recomendadas de confiança parcial](../../../../docs/framework/wcf/feature-details/partial-trust-best-practices.md) para obter mais informações sobre a segurança ao usar <xref:System.Runtime.Serialization.DataContractSerializer> com segurança em um aplicativo parcialmente confiável.  
  
### <a name="collection-types"></a>Tipos de coleção  
 Alguns tipos de coleção implementam <xref:System.Collections.Generic.IEnumerable%601> e <xref:System.Collections.IEnumerable>. Exemplos incluem tipos que implementam <xref:System.Collections.Generic.ICollection%601>. Esses tipos podem implementar uma `public` implementací `GetEnumerator()`e uma implementação explícita de `GetEnumerator()`. Nesse caso, <xref:System.Runtime.Serialization.DataContractSerializer> invoca o `public` implementação `GetEnumerator()`e não a implementação explícita de `GetEnumerator()`. Se nenhum dos `GetEnumerator()` são implementações `public` e todas são implementações explícitas, em seguida, <xref:System.Runtime.Serialization.DataContractSerializer> invoca `IEnumerable.GetEnumerator()`.  
  
 Para tipos de coleção quando o WCF está em execução em um ambiente de confiança parcial, se nenhum dos `GetEnumerator()` são implementações `public`, ou nenhum deles são implementações de interface explícita e uma exceção de segurança é gerada.  
  
### <a name="netdatacontractserializer"></a>NetDataContractSerializer  
 Muitos tipos de coleção do .NET Framework, como <xref:System.Collections.Generic.List%601>, <xref:System.Collections.ArrayList>, <xref:System.Collections.Generic.Dictionary%602> e <xref:System.Collections.Hashtable> não são compatíveis com o <xref:System.Runtime.Serialization.NetDataContractSerializer> em confiança parcial. Esses tipos têm o `[Serializable]` atributo definido e, conforme mencionado anteriormente na seção de serialização, esse atributo não tem suporte em confiança parcial. O <xref:System.Runtime.Serialization.DataContractSerializer> trata coleções de uma forma especial e, portanto, é possível contornar essa restrição, mas o <xref:System.Runtime.Serialization.NetDataContractSerializer> tem esse mecanismo não evitar essa restrição.  
  
 O <xref:System.DateTimeOffset> tipo não é suportado pelo <xref:System.Runtime.Serialization.NetDataContractSerializer> em confiança parcial.  
  
 Um substituto não pode ser usado com o <xref:System.Runtime.Serialization.NetDataContractSerializer> (usando o <xref:System.Runtime.Serialization.SurrogateSelector> mecanismo) quando em execução em confiança parcial. Observe que essa restrição se aplica ao uso de um substituto, não para serializá-lo.  
  
## <a name="enabling-common-behaviors-to-run"></a>Habilitar comportamentos comuns executar  
 Comportamentos de serviço ou ponto de extremidade não marcado com o <xref:System.Security.AllowPartiallyTrustedCallersAttribute> atributo (APTCA) que são adicionados para o [ \<commonBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/commonbehaviors.md) seção de um arquivo de configuração não são executados quando o aplicativo é executado em uma relação de confiança parcial ambiente e nenhuma exceção é lançada quando isso ocorre. Para impor a execução de comportamentos comuns, você deve fazer uma das seguintes opções:  
  
-   Marcar seu comportamento comum com o <xref:System.Security.AllowPartiallyTrustedCallersAttribute> de atributo para que ele possa executar quando implantado como um aplicativo de confiança parcial. Observe que uma entrada de registro pode ser definida no computador para impedir que os assemblies marcados com APTCA em execução. .  
  
-   Verifique se o aplicativo é implantado como um aplicativo totalmente confiável que os usuários não podem modificar as configurações de segurança de acesso ao código para executar o aplicativo em um ambiente de confiança parcial. Se eles podem fazer isso, o comportamento não é executado e nenhuma exceção é lançada. Para garantir isso, consulte a **levelfinal** usando a opção [Caspol.exe (ferramenta de política de segurança de acesso do código)](../../../../docs/framework/tools/caspol-exe-code-access-security-policy-tool.md).  
  
 Para obter um exemplo de um comportamento comum, consulte [como: Bloquear pontos de extremidade na empresa](../../../../docs/framework/wcf/extending/how-to-lock-down-endpoints-in-the-enterprise.md).  
  
## <a name="configuration"></a>Configuração  
 Com uma exceção, o código parcialmente confiável só pode carregar a seções de configuração do WCF no local `app.config` arquivo. Para carregar as seções de configuração do WCF que fazem referência a seções do WCF em Machine. config ou em uma raiz do arquivo Web. config requer ConfigurationPermission(Unrestricted). Sem essa permissão, referências a WCF seções de configuração (comportamentos, associações) fora os resultados do arquivo de configuração local em uma exceção quando a configuração é carregada.  
  
 A única exceção é a configuração do tipo conhecido para serialização, conforme descrito na seção de serialização deste tópico.  
  
> [!IMPORTANT]
>  Somente há suporte para extensões de configuração quando em execução em confiança total.  
  
## <a name="diagnostics"></a>Diagnóstico  
  
### <a name="event-logging"></a>Registro de eventos em log  
 Há suporte para o log de eventos limitado sob confiança parcial. Apenas falhas de ativação de serviço e falhas de registro em log de rastreamento de mensagens são registradas no Log de eventos. O número máximo de eventos que podem ser registradas em log por um processo é 5, para evitar a escrita de mensagens excessivas no Log de eventos.  
  
### <a name="message-logging"></a>Registro em log de mensagens  
 Log de mensagens não funciona quando o WCF é executado em um ambiente de confiança parcial. Se habilitada em confiança parcial, ele não falhou ativação do serviço, mas nenhuma mensagem será registrada.  
  
### <a name="tracing"></a>Rastreamento  
 Funcionalidade de rastreamento restrito está disponível quando executado em um ambiente de confiança parcial. No <`listeners`> elemento no arquivo de configuração, os únicos tipos que você pode adicionar são <xref:System.Diagnostics.TextWriterTraceListener> e o novo <xref:System.Diagnostics.EventSchemaTraceListener>. Uso do padrão <xref:System.Diagnostics.XmlWriterTraceListener> pode resultar em logs incompletos ou incorretos.  
  
 Fontes de rastreamento com suporte são:  
  
-   <xref:System.ServiceModel>  
  
-   <xref:System.Runtime.Serialization>  
  
-   <xref:System.IdentityModel.Claims>, <xref:System.IdentityModel.Policy>, <xref:System.IdentityModel.Selectors> e <xref:System.IdentityModel.Tokens>.  
  
 Não há suporte para as seguintes fontes de rastreamento:  
  
-   CardSpace  
  
-   <xref:System.IO.Log>  

-   [System.ServiceModel.Internal.TransactionBridge](https://docs.microsoft.com/previous-versions/aa346556(v=vs.110))]
  
 Os seguintes membros do <xref:System.Diagnostics.TraceOptions> enumeração não deve ser especificada:  
  
-   <xref:System.Diagnostics.TraceOptions.Callstack?displayProperty=nameWithType>  
  
-   <xref:System.Diagnostics.TraceOptions.ProcessId?displayProperty=nameWithType>  
  
 Ao usar o rastreamento em um ambiente de confiança parcial, certifique-se de que o aplicativo tem permissões suficientes para armazenar a saída do ouvinte de rastreamento. Por exemplo, ao usar o <xref:System.Diagnostics.TextWriterTraceListener> para gravar a saída de rastreamento em um arquivo de texto, certifique-se de que o aplicativo tenha FileIOPermission necessário necessária para gravar no arquivo de rastreamento com êxito.  
  
> [!NOTE]
>  Para evitar a saturação os arquivos de rastreamento com erros duplicados, WCF desabilita o rastreamento do recurso ou ação após a primeira falha de segurança. Há um rastreamento de exceção para cada acesso a recursos com falha, a primeira vez que uma tentativa de acessar o recurso ou executar a ação.  
  
## <a name="wcf-service-host"></a>Host de serviço WCF  
 Host de serviço do WCF não oferece suporte a confiança parcial. Se você quiser usar um serviço WCF em confiança parcial, não use o modelo de projeto de biblioteca de serviço do WCF no Visual Studio para criar seu serviço. Em vez disso, crie um novo site no Visual Studio escolhendo o modelo de site da Web de serviço do WCF, que pode hospedar o serviço em um servidor Web no qual há suporte para confiança parcial do WCF.  
  
## <a name="other-limitations"></a>Outras limitações  
 O WCF é geralmente limitado às considerações de segurança que imponham pelo aplicativo host. Por exemplo, se o WCF é hospedado em um aplicativo de navegador de XAML (XBAP), é sujeito às limitações do XBAP, conforme descrito em [Windows Presentation Foundation segurança parcialmente confiável](https://go.microsoft.com/fwlink/?LinkId=89138).  
  
 Os seguintes recursos adicionais não são habilitados quando executando indigo2 em um ambiente de confiança parcial:  
  
-   WMI (Instrumentação de Gerenciamento do Windows)  
  
-   Log de eventos é habilitado apenas parcialmente (consulte a discussão na **diagnóstico** seção).  
  
-   Contadores de desempenho  
  
 Uso de recursos do WCF que não são suportados em um ambiente de confiança parcial pode resultar em exceções em tempo de execução.  
  
## <a name="unlisted-features"></a>Recursos não listados  
 A melhor maneira de descobrir que uma parte das informações ou ação não está disponível quando em execução em um ambiente parcialmente confiável é tentar acessar o recurso ou executar a ação dentro de um `try` bloco e, em seguida, `catch` a falha. Para evitar a saturação os arquivos de rastreamento com erros duplicados, WCF desabilita o rastreamento do recurso ou ação após a primeira falha de segurança. Há um rastreamento de exceção para cada acesso a recursos com falha, a primeira vez que uma tentativa de acessar o recurso ou executar a ação.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.Channels.HttpTransportBindingElement>
- <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>
- <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.WebMessageEncodingBindingElement>
- [Cenários de implantação com suporte](../../../../docs/framework/wcf/feature-details/supported-deployment-scenarios.md)
- [Práticas recomendadas de confiança parcial](../../../../docs/framework/wcf/feature-details/partial-trust-best-practices.md)
