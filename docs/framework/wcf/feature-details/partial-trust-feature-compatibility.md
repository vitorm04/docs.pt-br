---
title: "Compatibilidade da funcionalidade de confiança parcial"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a36a540b-1606-4e63-88e0-b7c59e0e6ab7
caps.latest.revision: "75"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1950a0c4015658affb0b9fa0d7c87a062865144b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="partial-trust-feature-compatibility"></a>Compatibilidade da funcionalidade de confiança parcial
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]oferece suporte a um subconjunto limitado de funcionalidade quando executados em um ambiente parcialmente confiável. Os recursos com suporte em confiança parcial são projetados para um conjunto de cenários específicos, conforme descrito no [suporte para cenários de implantação](../../../../docs/framework/wcf/feature-details/supported-deployment-scenarios.md) tópico.  
  
## <a name="minimum-permission-requirements"></a>Requisitos de permissão mínima  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]dá suporte a um subconjunto de recursos em aplicativos em execução em qualquer um dos seguintes conjuntos de permissões nomeadas padrão:  
  
-   Permissões de confiança médio  
  
-   Permissões de zona da Internet  
  
 Tentativa de usar [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] em aplicativos parcialmente confiáveis com permissões mais restritivas pode resultar em exceções de segurança em tempo de execução.  
  
## <a name="contracts"></a>Contratos  
 Contratos estão sujeitas às seguintes restrições ao executar em confiança parcial:  
  
-   A classe de serviço que implementa o `[ServiceContract]` interface deve ser `public` e ter um `public` construtor. Se ele define `[OperationContract]` métodos, eles devem ser `public`. Se, em vez disso, ele implementa um `[ServiceContract]` interface, as implementações de método podem ser explícitas ou `private`, desde que o `[ServiceContract]` interface é `public`.  
  
-   Ao usar o `[ServiceKnownType]` atributo, o método especificado deve ser `public`.  
  
-   `[MessageContract]`classes e seus membros podem ser `public`. Se o `[MessageContract]` classe é definida no assembly do aplicativo pode ser `internal` e ter `internal` membros.  
  
## <a name="system-provided-bindings"></a>Associações fornecidas pelo sistema  
 O <xref:System.ServiceModel.BasicHttpBinding> e <xref:System.ServiceModel.WebHttpBinding> têm suporte total em um ambiente de confiança parcial. O <xref:System.ServiceModel.WSHttpBinding> tem suporte para somente modo de segurança de transporte.  
  
 Associações que usam transportes diferente de HTTP, como o <xref:System.ServiceModel.NetTcpBinding>, o <xref:System.ServiceModel.NetNamedPipeBinding>, ou o <xref:System.ServiceModel.NetMsmqBinding>, não são suportados quando executados em um ambiente de confiança parcial.  
  
## <a name="custom-bindings"></a>Associações personalizadas  
 Associações personalizadas podem ser criadas e usados em um ambiente de confiança parcial, mas devem seguir as restrições especificadas nesta seção.  
  
### <a name="transports"></a>Transportes  
 Os únicos permitidos são elementos de associação de transporte <xref:System.ServiceModel.Channels.HttpTransportBindingElement> e <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>.  
  
### <a name="encoders"></a>Codificadores  
 Os seguintes codificadores são permitidos:  
  
-   O codificador de texto (<xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>).  
  
-   O codificador binário (<xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>).  
  
-   O codificador de mensagem da Web (<xref:System.ServiceModel.Channels.WebMessageEncodingBindingElement>).  
  
 Não há suporte para os codificadores de mecanismo de otimização de transmissão da mensagem (MTOM).  
  
### <a name="security"></a>Segurança  
 Aplicativos parcialmente confiáveis podem usar [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]de recursos de segurança para proteger suas comunicações de nível de transporte. Não há suporte para a segurança em nível de mensagem. Configurando uma associação para usar a segurança de nível de mensagem resulta em uma exceção em tempo de execução.  
  
### <a name="unsupported-bindings"></a>Não há suporte para associações  
 Não há suporte para associações que usam o sistema de mensagens confiável, transações ou segurança em nível de mensagem.  
  
## <a name="serialization"></a>Serialização  
 Tanto o <xref:System.Runtime.Serialization.DataContractSerializer> e <xref:System.Xml.Serialization.XmlSerializer> têm suporte em um ambiente de confiança parcial. No entanto, usar o <xref:System.Runtime.Serialization.DataContractSerializer> está sujeita às seguintes condições:  
  
-   Todos os serializável `[DataContract]` tipos devem ser `public`.  
  
-   Todos os serializável `[DataMember]` campos ou propriedades em um `[DataContract]` tipo deve ser público e leitura/gravação. A serialização e desserialização de [readonly](http://go.microsoft.com/fwlink/?LinkID=98854) campos não é suportado quando executando [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] em um aplicativo parcialmente confiável.  
  
-   O  `[Serializable]` /modelo de programação ISerializable não tem suporte em um ambiente de confiança parcial.  
  
-   Tipos conhecidos devem ser especificados no código ou configuração de nível de máquina (Machine. config). Tipos conhecidos não podem ser especificados na configuração de nível de aplicativo por motivos de segurança.  
  
-   Tipos que implementam <xref:System.Runtime.Serialization.IObjectReference> lançar uma exceção em um ambiente parcialmente confiável.  
  
 Consulte a seção de serialização em [práticas recomendadas de confiança parcial](../../../../docs/framework/wcf/feature-details/partial-trust-best-practices.md) para obter mais informações sobre segurança ao usar <xref:System.Runtime.Serialization.DataContractSerializer> com segurança em um aplicativo parcialmente confiável.  
  
### <a name="collection-types"></a>Tipos de coleção  
 Alguns tipos de coleção implementam <xref:System.Collections.Generic.IEnumerable%601> e <xref:System.Collections.IEnumerable>. Exemplos incluem os tipos que implementam <xref:System.Collections.Generic.ICollection%601>. Esses tipos podem implementar uma `public` implementação de `GetEnumerator()`e uma implementação explícita de `GetEnumerator()`. Nesse caso, <xref:System.Runtime.Serialization.DataContractSerializer> invoca o `public` implementação de `GetEnumerator()`e não a implementação explícita de `GetEnumerator()`. Se nenhuma a `GetEnumerator()` são implementações `public` e todas as implementações explícitas, em seguida, <xref:System.Runtime.Serialization.DataContractSerializer> invoca `IEnumerable.GetEnumerator()`.  
  
 Para a coleção de tipos quando [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] está em execução em um ambiente de confiança parcial, se nenhuma do `GetEnumerator()` são implementações `public`, ou nenhum deles são implementações de interface explícita e é gerada uma exceção de segurança.  
  
### <a name="netdatacontractserializer"></a>NetDataContractSerializer  
 Muitos tipos de coleção do .NET Framework, como <xref:System.Collections.Generic.List%601>, <xref:System.Collections.ArrayList>, <xref:System.Collections.Generic.Dictionary%602> e <xref:System.Collections.Hashtable> não oferece suporte a <xref:System.Runtime.Serialization.NetDataContractSerializer> em confiança parcial. Esses tipos têm o `[Serializable]` atributo definido e, conforme mencionado anteriormente na seção de serialização, esse atributo não tem suporte em confiança parcial. O <xref:System.Runtime.Serialization.DataContractSerializer> trata coleções de uma forma especial e, portanto, é possível contornar essa restrição, mas o <xref:System.Runtime.Serialization.NetDataContractSerializer> não tem nenhum esse mecanismo para contornar essa restrição.  
  
 O <xref:System.DateTimeOffset> tipo não é suportado pelo <xref:System.Runtime.Serialization.NetDataContractSerializer> em confiança parcial.  
  
 Um substituto não pode ser usado com o <xref:System.Runtime.Serialization.NetDataContractSerializer> (usando o <xref:System.Runtime.Serialization.SurrogateSelector> mecanismo) durante a execução em confiança parcial. Observe que essa restrição se aplica ao uso de um substituto, não para serializá-lo.  
  
## <a name="enabling-common-behaviors-to-run"></a>Habilitar comportamentos comuns executar  
 Comportamentos de serviço ou o ponto de extremidade não marcado com o <xref:System.Security.AllowPartiallyTrustedCallersAttribute> atributo (APTCA) que são adicionados para o [ \<commonBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/commonbehaviors.md) seção de um arquivo de configuração não são executados quando o aplicativo é executado em uma relação de confiança parcial ambiente e nenhuma exceção é lançada quando isso ocorre. Para impor a execução de comportamentos comuns, você deve fazer uma das seguintes opções:  
  
-   Marcar o comportamento comum com o <xref:System.Security.AllowPartiallyTrustedCallersAttribute> atributo para que ele pode ser executado quando implantado como um aplicativo de confiança parcial. Observe que uma entrada de registro pode ser definida no computador para impedir que os assemblies marcados APTCA em execução. .  
  
-   Verifique se o aplicativo é implantado como um aplicativo totalmente confiável que os usuários não podem modificar as configurações de segurança de acesso do código para executar o aplicativo em um ambiente de confiança parcial. Se eles podem fazer isso, o comportamento não é executado e nenhuma exceção é lançada. Para verificar isso, consulte o **levelfinal** usando a opção [Caspol.exe (ferramenta de política de segurança de acesso do código)](../../../../docs/framework/tools/caspol-exe-code-access-security-policy-tool.md).  
  
 [!INCLUDE[crexample](../../../../includes/crexample-md.md)]um comportamento comum, consulte [como: bloqueio para pontos de extremidade na empresa](../../../../docs/framework/wcf/extending/how-to-lock-down-endpoints-in-the-enterprise.md).  
  
## <a name="configuration"></a>Configuração  
 Com uma exceção, o código parcialmente confiável somente pode carregar [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] seções de configuração no local `app.config` arquivo. Para carregar [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] seções de configuração que fazem referência [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] seções em Machine. config ou em um arquivo Web. config de raiz requer ConfigurationPermission(Unrestricted). Sem essa permissão, as referências a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] seções de configuração (comportamentos, associações) fora os resultados do arquivo de configuração local em uma exceção quando a configuração é carregada.  
  
 A única exceção é a configuração de tipo conhecido para a serialização, conforme descrito na seção serialização deste tópico.  
  
> [!IMPORTANT]
>  Somente há suporte para extensões de configuração quando em execução em confiança total.  
  
## <a name="diagnostics"></a>Diagnóstico  
  
### <a name="event-logging"></a>Registro de eventos em log  
 O log de eventos limitado tem suporte em confiança parcial. Apenas as falhas de ativação de serviço e falhas de registro em log de rastreamento de mensagens são registradas no log de eventos. O número máximo de eventos que podem ser registrados por um processo é 5, para evitar a escrita de mensagens excessivas no log de eventos.  
  
### <a name="message-logging"></a>Registro em log de mensagens  
 Mensagem de log não funciona quando [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] é executado em um ambiente de confiança parcial. Se habilitada em confiança parcial, ela não falhará ativação do serviço, mas nenhuma mensagem é registrada.  
  
### <a name="tracing"></a>Rastreamento  
 Funcionalidade de rastreamento restrito está disponível quando executado em um ambiente de confiança parcial. No <`listeners`> elemento no arquivo de configuração, os únicos tipos que você pode adicionar são <xref:System.Diagnostics.TextWriterTraceListener> e o novo <xref:System.Diagnostics.EventSchemaTraceListener>. Uso do padrão <xref:System.Diagnostics.XmlWriterTraceListener> pode resultar em logs incompletas ou incorretas.  
  
 Fontes de rastreamento com suporte são:  
  
-   <xref:System.ServiceModel>  
  
-   <xref:System.Runtime.Serialization>  
  
-   <xref:System.IdentityModel.Claims>, <xref:System.IdentityModel.Policy>, <xref:System.IdentityModel.Selectors> e <xref:System.IdentityModel.Tokens>.  
  
 Não há suporte para as seguintes fontes de rastreamento:  
  
-   CardSpace  
  
-   <xref:System.IO.Log>  

-   [System.ServiceModel.Internal.TransactionBridge](https://msdn.microsoft.com/library/system.servicemodel.internal.transactionbridge.aspx)]
  
 Os seguintes membros de <xref:System.Diagnostics.TraceOptions> enumeração não deve ser especificada:  
  
-   <xref:System.Diagnostics.TraceOptions.Callstack?displayProperty=nameWithType>  
  
-   <xref:System.Diagnostics.TraceOptions.ProcessId?displayProperty=nameWithType>  
  
 Ao usar o rastreamento em um ambiente de confiança parcial, certifique-se de que o aplicativo tem permissões suficientes para armazenar a saída do ouvinte de rastreamento. Por exemplo, ao usar o <xref:System.Diagnostics.TextWriterTraceListener> para gravar a saída de rastreamento em um arquivo de texto, certifique-se de que o aplicativo tem FileIOPermission necessário necessária para gravar no arquivo de rastreamento com êxito.  
  
> [!NOTE]
>  Para evitar a saturação com erros duplicados, os arquivos de rastreamento [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] desabilita o rastreamento do recurso ou ação após a primeira falha de segurança. Há um rastreamento de exceção para cada acesso a recursos com falha, a primeira vez que é feita uma tentativa de acessar o recurso ou executar a ação.  
  
## <a name="wcf-service-host"></a>Host de serviço do WCF  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]host de serviço não dá suporte a confiança parcial. Se você quiser usar um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] de serviço em confiança parcial, não use o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] modelo de projeto de biblioteca de serviço em [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] para criar o serviço. Em vez disso, crie um novo site no [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] escolhendo o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] modelo de site da Web do serviço, que pode hospedar o serviço em um servidor Web no qual [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] há suporte para a relação de confiança parcial.  
  
## <a name="other-limitations"></a>Outras limitações  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]é geralmente limitado para as considerações de segurança que imponham pelo aplicativo host. Por exemplo, se [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] está hospedado em um aplicativo de navegador de XAML (XBAP), ele está sujeito a limitações XBAP, conforme descrito na [Windows Presentation Foundation Partial Trust Security](http://go.microsoft.com/fwlink/?LinkId=89138).  
  
 Os seguintes recursos adicionais não são habilitados quando executar indigo2 em um ambiente de confiança parcial:  
  
-   WMI (Instrumentação de Gerenciamento do Windows)  
  
-   O log de eventos é habilitado apenas parcialmente (consulte a discussão **diagnóstico** seção).  
  
-   Contadores de desempenho  
  
 O uso de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] recursos que não são suportados em um ambiente de confiança parcial podem resultar em exceções em tempo de execução.  
  
## <a name="unlisted-features"></a>Recursos não listados  
 A melhor maneira de descobrir que uma parte das informações ou ação não está disponível quando executados em um ambiente de confiança parcial é tentar acessar o recurso ou executar a ação dentro de um `try` bloco e, em seguida, `catch` a falha. Para evitar a saturação com erros duplicados, os arquivos de rastreamento [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] desabilita o rastreamento do recurso ou ação após a primeira falha de segurança. Há um rastreamento de exceção para cada acesso a recursos com falha, a primeira vez que é feita uma tentativa de acessar o recurso ou executar a ação.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Channels.HttpTransportBindingElement>  
 <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>  
 <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>  
 <xref:System.ServiceModel.Channels.WebMessageEncodingBindingElement>  
 [Cenários de implantação com suporte](../../../../docs/framework/wcf/feature-details/supported-deployment-scenarios.md)  
 [Práticas recomendadas de confiança parcial](../../../../docs/framework/wcf/feature-details/partial-trust-best-practices.md)
